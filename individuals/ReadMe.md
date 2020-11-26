个体仓库，为每个实例化的个体分为唯一的URI。
基础上下文20190112/base.jsonld文档定义个体仓库根目录的命名空间为"kzidv:https://schema.kanzhun.com/individuals/"。

根据个体的type，将个体仓库分为16个子仓库，每个自仓库的个体单独编号：
AdministrativeArea      : 行政区划个体仓库，每个个体代表一个地址节点，包括省、市、区县、乡镇、村、街、街道号、地标、楼区、楼座、栋、单元、楼层、门牌号。
BSSIDSpecification      : BSSID(mac)个体仓库，每个个体代表一个路由器。
EducationalOrganization : 学校个体仓库，每个个体代表一所学校。
EmailAccount            : 邮箱账户个体仓库，每个个体代表一个邮箱账户。
FreezingEvent           : 冻结事件个体仓库，每个个体代表一次冻结事件，至少关联到一个用户。
GeoCoordinates          : 坐标个体仓库，每个个体代表一个经纬度坐标，精度是千米。
IPAddress               : IP个体仓库，每个个体代表一个IP地址。
JobPosting              : 招聘信息个体仓库，每个个体代表一份招聘信息，至少关联到一个用户和一个地址。
NotUser                 : 非用户人员个体仓库，每个个体代表一名人员，该人员不是用户，可能是公司的自然人股东，也可能是冻结事件的运营管理人员。
Organization            : 公司个体仓库，每个个体代表一个公司，可能是实际存在的公司，也可能是虚拟的公司。
PhoneNumber             : 电话号码个体仓库，每个个体代表一个电话号码。
PhoneSpecification      : 手机识别个体仓库，每个个体代表一份手机识别信息，暗示一个手机。
ServiceMembership       : 服务身份仓库，每个个体代表一个服务身份，服务身份包含该身份下的独有状态信息
SSIDSpecification       : SSID(wifi)个体仓库，每个个体代表一个wifi名称。
User                    : 用户个体仓库，每个个体代表一个用户
WechatAccount           : 微信账号个体仓库，每个个体代表一个微信账号，不是微信昵称。

引用示例：
绝对路径：https://schema.kanzhun.com/individuals/User#1003
相对路径：kzidv:User#1003

每个个体的引用页面，应该展示该个体的信息，信息可以实时从知识图谱中提取，具体实现细节待定。