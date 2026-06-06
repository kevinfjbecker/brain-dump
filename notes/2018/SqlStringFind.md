/*
 *  String Find
 */
SELECT distinct Name
FROM sys.objects
WHERE OBJECT_DEFINITION(OBJECT_ID) LIKE '%meta_RunComplete%'
AND name LIKE '%'
ORDER BY name