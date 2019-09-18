package com.wistron.avatar.sci.common.dao;

import java.util.List;
import java.util.Map;
import java.util.Map.Entry;

import com.google.common.collect.Maps;
import com.wistron.avatar.common.util.ConnectionUtils;

import org.apache.commons.collections.CollectionUtils;
import org.apache.commons.collections.MapUtils;

import redis.clients.jedis.JedisCluster;

public class RedisMpspSciProcessCtrlDao {

    private String redisKey = "";

    public final static String FN_ISPROCESSING = "isProcessing";
    public final static String FN_PROCESSING_SCI_ENGINE = "processing_SCI_engine";
    public final static String FN_MRP_RUN_DATE = "mrp_run_date";
    public final static String FN_MPSP_VERSION = "mpsp_version";
    public final static String FN_SCI_VERSION = "sci_version";
    public final static String FN_MRP_FROZEN_DATETIME = "mrp_frozen_date_time";

    public RedisMpspSciProcessCtrlDao(String plant) {
        this.redisKey = String.format("MPSP_SCI_PROCESS_CTRL:%s", plant);
    }

    /***********************************
     * Below methods can be put into super class, but only used for HashMap key
     ***********************************/
    
     /**
     * Get Redis connection
     */
    private JedisCluster getRedisConnection() throws Exception {
        return ConnectionUtils.getRedisConnection();
    }

    /**
     * Check Redis key whether exists
     */
    public boolean existsKey() throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        return jedis.exists(this.redisKey);
    }

    /**
     * Return redis key.
     */
    public String getRedisKey() {
        return this.redisKey;
    }

    /**
     * Return all fields and values as hashmap of the redis key.
     */
    public Map<String, String> getValues() throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        return jedis.hgetAll(this.redisKey);
    }

    /**
     * Create the redis key using a hashmap.
     * 
     */
    public void initRedisKey(Map<String, String> map) throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        if (jedis.exists(this.redisKey)) {
            jedis.del(this.redisKey);
        }
        Map<String, String> hashMap = map == null ? Maps.newHashMap() : map;
        jedis.hmset(this.redisKey, hashMap);
    }

    /**
     * Remove the key.
     */
    public void deleteRedisKey() throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        jedis.del(this.redisKey);
    }

    /**
     * Delete Hashkey from the redis key using a hashmap.
     */
    public void removeHashKey(List<String> lstHashKey) throws Exception {
        if (CollectionUtils.isNotEmpty(lstHashKey)) {
            JedisCluster jedis = this.getRedisConnection();
            for (String hashKey : lstHashKey) {
                jedis.hdel(this.redisKey, hashKey);
            }
        }
    }

    /**
     * Set fields value.
     */
    public void setFieldValues(Map<String, String> mapFieldValue) throws Exception {
        if (MapUtils.isNotEmpty(mapFieldValue)) {
            JedisCluster jedis = this.getRedisConnection();
            for (Entry<String, String> entry : mapFieldValue.entrySet()) {
                jedis.hset(this.redisKey, entry.getKey(), entry.getValue());
            }
        }
    }

    /**
     * Set Filed Value
     */
    public void setFieldValue(String fieldName, String value) throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        jedis.hset(this.redisKey, fieldName, value);
    }

    /**
     * Get a field value.
     */
    public String getFieldValue(String field) throws Exception {
        Map<String, String> mapFields = this.getValues();
        return mapFields.containsKey(field) ? mapFields.get(field) : "";
    }

    /**
     * set expired time
     */
    public void setExpiredTime(int seconds) throws Exception {
        JedisCluster jedis = this.getRedisConnection();
        jedis.expire(this.redisKey, seconds);
    }

    /****************************
     * Provide some other methods like:
     ****************************/

    /**
     * Get in-processing SCI Version
     */
    public String getSciVersion() throws Exception {
        return this.getFieldValue(FN_SCI_VERSION);
    }

    /**
     * Return if SCI Engine is processing.
     */
    public boolean isProcessingEngine() throws Exception {
        return "Y".equals(this.getFieldValue(FN_ISPROCESSING));
    }
}
