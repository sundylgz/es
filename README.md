 SELECT
        a.id,a.org_id,a.catalog_id,a.catalog_name catalogName,a.cover_url,a.title,a.read_count,b.description,b.tag_ids,a.study_count,
        b.author,b.contributors_name,b.lectures_name,a.create_time,a.create_user_id,a.create_fullname,
        c.id as collegeId, c.college_name as collegeName, b.permission_type as permissionType, a.update_time as updateTime,
        a.support_count as supportCount, a.recommend_level as recommendLevel, a.type, a.file_type fileType, a.app_enabled appEnabled,
        a.avg_comment_score avgCommentScore, a.study_score studyScore, b.price, b.version, a.study_hours as studyHours, b.originality,
        b.lectures_id as lectureId, b.counse_lorteacher_ids as assistLectureId, b.contributors_user as contributorId, b.down_enabled as downEnabled, d.opened
FROM
    kng_knowledge a
join
    kng_knowledge_ext b 
        on a.id = b.id
join
    kng_college c 
        on a.college_id = c.id
join
    kng_catalog d 
        on a.catalog_id = d.id
WHERE
    a.org_id = '' 
    and a.deleted = 0 
    and a.visiable = 1 
    and a.on_sale = 1
    and a.status = 4 
    and c.enabled = 1 
    and c.deleted = 0
