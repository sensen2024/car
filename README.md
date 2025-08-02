

## 前言

> :heart:**博主简介**：全网累计学员1000+，培训机构讲师、全栈开发工程师、知乎/小红书优秀作者、腾讯云/阿里云VIP客户、专注Java、小程序、安卓领域和毕业项目开发
>
>
> <font color=brown>`同学们可以先收藏起来，以免迷路，关于毕设选题，项目和论文的相关问题可以找我咨询，希望帮助到越来越多的同学。`</font>

:heart:所有成品源码售卖100-200元/套，白嫖勿扰


:star:微信：sen885988

## 题目
汽车销售系统
## 技术栈
后端：SpringBoot
前端：Vue
数据库：MySQL

## 功能概述
本系统为实现汽车选购需求，而打造的“汽车销售系统”，汽车销售系统是一个工作量丰富，实用性极强的选题，所以如果没有特殊要求 汽车销售系统是一个不错的选择，本汽车销售系统功能涵盖了用户管理、车辆管理、品牌管理、车型管理、留言管理、维修材料管理、材料分类管理、论坛管理、汽车资讯管理、订单管理、轮播图管理等

>汽车销售系统包括用户、管理员2个模块
:star:用户功能：主要包括车辆信息浏览、在线购买、论坛交流、汽车资讯查看、留言反馈、订单管理、购物车管理、在线客服、地址管理、充值、个人信息管理等
:star:管理员功能：用户管理、车辆管理、品牌管理、车型管理、留言管理、维修材料管理、材料分类管理、论坛管理、汽车资讯管理、订单管理、轮播图管理等
## 实现页面截图 
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d574c44c23b24a5dbdcbb9cee82436d5.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/64f0fac540884203aada3c323836dcde.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/511b68e7d99e4edb8a36908fb582cbb2.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/69b84f8cdd3a480381c9bb5f25662c1d.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/46aee3b84eed4bf6a8d7555d867dbbeb.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b0904dc1669d4e70bc6d6d3010305c35.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e54fda5fc4024c3c841c70d4e838d3ca.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/9dc461ea73434acaafd209da515a48da.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/43acc5c90d8b47a7a16eb3eef429a36f.png)



## 文章参考
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/738f9e6cf61e425e911ec452b322564e.png)


## 我的优势
<font color="brown">:heart:下方是我的[个人网站](https://sensencoding.cn)，可查看最新选题推荐</font>

毕设最全站点：[https://sensencoding.cn](https://sensencoding.cn)


<img width="1462" height="812" alt="image" src="https://github.com/user-attachments/assets/4e9d84e1-38ac-4298-a892-879521de63e9" />



`网站上传的项目均是博主自己开发的，质量都可以得到保障，适合有一些开发基础的同学使用`
## 代码参考

```java
@RestController
@RequestMapping("/yonghu")
public class YonghuController {
    @Autowired
    private YonghuService yonghuService;


    
	@Autowired
	private TokenService tokenService;
	
	/**
	 * 登录
	 */
	@IgnoreAuth
	@RequestMapping(value = "/login")
	public R login(String username, String password, String captcha, HttpServletRequest request) {
		YonghuEntity u = yonghuService.selectOne(new EntityWrapper<YonghuEntity>().eq("yonghuming", username));
		if(u==null || !u.getMima().equals(password)) {
			return R.error("账号或密码不正确");
		}
		
		String token = tokenService.generateToken(u.getId(), username,"yonghu",  "用户" );
		return R.ok().put("token", token);
	}

	
	/**
     * 注册
     */
	@IgnoreAuth
    @RequestMapping("/register")
    public R register(@RequestBody YonghuEntity yonghu){
    	//ValidatorUtils.validateEntity(yonghu);
    	YonghuEntity u = yonghuService.selectOne(new EntityWrapper<YonghuEntity>().eq("yonghuming", yonghu.getYonghuming()));
		if(u!=null) {
			return R.error("注册用户已存在");
		}
		Long uId = new Date().getTime();
		yonghu.setId(uId);
        yonghuService.insert(yonghu);
        return R.ok();
    }
```
## 数据库参考

```java

DROP TABLE IF EXISTS `caipufenlei`;
CREATE TABLE `caipufenlei`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `addtime` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `caipufenlei` varchar(200) CHARACTER SET utf8mb3 COLLATE utf8mb3_general_ci NOT NULL COMMENT '资讯分类',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `caipufenlei`(`caipufenlei` ASC) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 27 CHARACTER SET = utf8mb3 COLLATE = utf8mb3_general_ci COMMENT = '资讯分类' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of caipufenlei
-- ----------------------------
INSERT INTO `caipufenlei` VALUES (21, '2024-03-20 12:07:59', '资讯分类1');
INSERT INTO `caipufenlei` VALUES (22, '2024-03-20 12:07:59', '资讯分类2');
```

我的博客即将同步至腾讯云开发者社区，邀请大家一同入驻：https://cloud.tencent.com/developer/support-plan?invite_code=dmnq9dz62bm

