后端接口（API）服务协议规范
=======================

本文档定义了前/后端接口协议所需遵循的一些基础规范，以便统一接口的请求/响应格式，便于前/后端进行统一的处理。

接口服务采用JSON作为API数据传输的基础格式。请求形式建议采用RESTful规范的URL格式。

前端请求
-------

RESTful API。

后端响应
---------

	{
		"errcode":"_ERROR_NUMBER_",
		"errmsg":"_ERROR_MESSAGE_",
		"timestamp":"_TIME_STAMP_",
		"reqid":"_REQUEST_ID_",
		"data":{ … }
	}

其中，

* errno：必选字段，表示错误号，0为正常/成功，非0（默认为-1）为异常。除0外的异常编号可在具体接口中约定。
* data：必选字段，承载接口数据，无数据时需要留空节点。
* errmsg：可选字段，可根据需要写入出错信息。
* timestamp：可选字段，表示服务器处理请求的UNIX时间戳。
* reqid：可选字段，表示请求id，由服务器分配，适用于需要一个包含多次请求的session的场景。

