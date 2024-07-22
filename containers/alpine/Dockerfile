# trunk-ignore-all(trivy/DS002,trivy/DS026,checkov/CKV_DOCKER_2,checkov/CKV_DOCKER_3)
FROM alpine:3.20@sha256:0a4eaa0eecf5f8c050e5bba433f58c052be7587ee8af3e8b3910ef9ab5fbe9f5 as SOURCE

RUN apk upgrade --no-cache

FROM scratch

COPY --from=SOURCE / /

