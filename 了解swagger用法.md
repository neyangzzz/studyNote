# 入职第三天笔记
了解swagger

## swagger常用注解

###1，@Api 
用在类上，说明该类的作用。可以标记一个Controller类做为swagger 文档资源，使用方式：
	@Api(value = "/user", description = "Operations about user")


### 2，@ApiOperation：用在方法上，说明方法的作用，每一个url资源的定义,使用方式：
@ApiOperation(
          value = "Find purchase order by ID",
          notes = "For valid response try integer IDs with value <= 5 or > 10. Other values will generated exceptions",
          response = Order,
          tags = {"Pet Store"})


### 3，ApiParam标记
ApiParam请求属性,使用方式：
public ResponseEntity<User> createUser(@RequestBody @ApiParam(value = "Created user object", required = true)  User user)
与Controller中的方法并列使用。


### 4，ApiResponse
ApiResponse：响应配置，使用方式：
@ApiResponse(code = 400, message = "Invalid user supplied")
与Controller中的方法并列使用。 属性配置：

### 5，ApiResponses
ApiResponses：响应集配置，使用方式：
 @ApiResponses({ @ApiResponse(code = 400, message = "Invalid Order") })
与Controller中的方法并列使用。


### 6， ResponseHeader
响应头设置，使用方法
@ResponseHeader(name="head1",description="response head conf")
与Controller中的方法并列使用。
* @ApiImplicitParams：用在方法上包含一组参数说明；
* @ApiImplicitParam：用在@ApiImplicitParams注解中，指定一个请求参数的各个方面
    * paramType：参数放在哪个地方
    * name：参数代表的含义
    * value：参数名称
    * dataType： 参数类型，有String/int，无用
    * required ： 是否必要
    * defaultValue：参数的默认值
* @ApiResponses：用于表示一组响应；
* @ApiResponse：用在@ApiResponses中，一般用于表达一个错误的响应信息；
    * code： 响应码(int型)，可自定义
    * message：状态码对应的响应信息
* @ApiModel：描述一个Model的信息（这种一般用在post创建的时候，使用@RequestBody这样的场景，请求参数无法使用@ApiImplicitParam注解进行描述的时候；
* @ApiModelProperty：描述一个model的属性。









