#
## 说明
该文档是用来介绍各个模块之间的关键接口，便于开发人员进行速查。
这种将文档放入代码仓库中，在业内的实践也叫做 doc-as-code .

## 交互接口介绍
    - 数据库SQL语句的总入口： `exec_query(sql_stmt: str) -> Result ` 用于接收用户的访问SQL，协调数据库内各组件
    - SQL引擎SQL解析部分的入口： `query_parse(sql_stmt: str) -> ASTNode`，用于解析SQL语句，返回AST
    - SQL引擎SQL优化过程的入口： `query_plan(ast: ASTNode) -> PlanTree`，用于将解析后的AST转换为具体的执行计划
    - 执行引擎的入口： `exec_plan(plan_tree: PlanTree) -> Result `，用于将具体的执行计划进行执行，并返回结果
