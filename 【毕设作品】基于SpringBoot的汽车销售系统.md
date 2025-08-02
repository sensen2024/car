@[TOC](文章目录)


## 前言

> :heart:**博主简介**：全网累计学员1000+，培训机构讲师、全栈开发工程师、知乎/小红书优秀作者、腾讯云/阿里云VIP客户、专注Java、小程序、安卓领域和毕业项目开发:heart:
> :star:<font color=red>文末获取源码+数据库</font>:star:
> <font color=brown>`同学们可以先收藏起来，以免迷路，关于毕设选题，项目和论文的相关问题可以找我咨询，希望帮助到越来越多的同学。`</font>
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


## 系统测试
我们必须从多个角度对系统进行全面检查，以识别潜在问题，这构成了我们测试工作的核心目标。通过功能测试，我们旨在发现系统中的所有缺陷，并进行修正，以确保系统的可靠性。在测试过程中，我们需验证汽车销售系统是否满足客户的需求，一旦发现任何不符合预期的情况，必须立即进行调整。完成测试后，我们将能够掌握测试结果。

### 系统测试目的
在**汽车销售系统**开发中，系统测试是关键环节，确保系统品质与稳定性。其目的是预防使用问题，提升用户体验。测试需全面考虑潜在问题，通过模拟场景发现并修正缺陷。测试流程完成后，系统品质和用户体验将得到提升。测试目标是验证系统是否符合需求规格，发现不符或冲突问题。测试应从用户角度出发，避免不切实际场景，确保测试效率和准确性。
### 系统功能测试
执行汽车销售系统功能模块测试，采用黑盒测试方法，包括点击、输入边界值和验证必填项。依据测试用例进行检验，得出结论。
登录功能测试方案：通过账户密码验证，输入需与数据库匹配，错误输入提示错误。界面校验角色权限，管理员角色登录报错。测试用例如下表。

| 用户名 | 密码 |预期结果 |实际结果 |分析 |
|--|--|--|--|-|
| admin | 123456|密码错误 |密码错误 |正常 |
| admin | admin |登录成功 |登录成功 |正常|
| admin | 空 |密码不能为空 |密码不能为空 |正常 |


### 系统测试结论
本系统主要采用黑盒测试，编写并执行测试用例以确保流程正确性。系统测试对完善系统、提高可用性至关重要。测试目的是验证功能模块是否符合设计理念及逻辑准确性，测试场景须符合用户需求。最终测试结果表明汽车销售系统功能和性能满足设计要求。

## 文章参考
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/738f9e6cf61e425e911ec452b322564e.png)


## 我的优势
<font color="brown">:heart:文章下方联系我</font>
![请添加图片描述](https://i-blog.csdnimg.cn/direct/b3b9bf847b2246438ed83a1fbb822538.png)


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

## 源码获取
<font color=red>文章下方名片联系我:point_down:</font>

