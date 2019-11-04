---
title: Zayıf yazılmış JSON Seri Hale Getirme Örneği
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: 1450a0e46ade615769d7ffdc1006102772dbc977
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424536"
---
# <a name="weakly-typed-json-serialization-sample"></a>Zayıf yazılmış JSON Seri Hale Getirme Örneği
Kullanıcı tanımlı bir türü belirli bir hat biçiminde serileştirilirken veya bir tel biçiminin Kullanıcı tanımlı bir türe geri serisi kaldırılırken, belirtilen kullanıcı tanımlı tür hem hizmette hem de istemcide kullanılabilir olmalıdır. Genellikle bunu gerçekleştirmek için, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bu kullanıcı tanımlı türlere uygulanır ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği üyelerine uygulanır. Bu mekanizma Ayrıca JavaScript Nesne Gösterimi (JSON) nesneleriyle çalışırken, [JSON verilerini serileştirme ve serisini kaldırma](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)konusunda açıklandığı şekilde geçerlidir.  
  
 Bazı senaryolarda, bir Windows Communication Foundation (WCF) hizmeti veya istemcisinin, geliştirici denetimi dışında bir hizmet veya istemci tarafından oluşturulan JSON nesnelerine erişmesi gerekir. Daha fazla Web hizmeti JSON API 'Leri kullanıma sunduğundan, WCF geliştiricisinin rastgele JSON nesnelerinin serisini kaldırmak için yerel kullanıcı tanımlı türler oluşturmasına pratik hale gelebilir. Bu örnek, WCF geliştiricilerinin Kullanıcı tanımlı türler oluşturmadan, serisi olmayan, rastgele JSON nesneleriyle çalışmasını sağlayan bir mekanizma sağlar. JSON nesnelerinin, derleme zamanında bilinmediği tür olmadığı için, bu, JSON nesnelerinin *zayıf olarak yazılmış seri hale getirme* olarak bilinir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örneğin, bir genel Web hizmeti API 'SI, bir hizmetin kullanıcısı hakkında bazı bilgileri açıklayan aşağıdaki JSON nesnesini döndürür.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Bu nesnenin serisini kaldırmak için, bir WCF istemcisinin aşağıdaki Kullanıcı tanımlı türleri uygulaması gerekir.  
  
```csharp  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 Özellikle istemcinin birden fazla JSON nesne türünü işlemesi gerekiyorsa, bu çok sayıda olabilir.  
  
 Bu örnek tarafından belirtilen `JsonObject` türü, serisi kaldırılan JSON nesnesinin zayıf yazılmış bir gösterimini tanıtır. `JsonObject`, JSON nesneleri ile .NET Framework sözlükleri arasındaki doğal eşlemeyi ve JSON dizileri ile .NET Framework dizileri arasındaki eşlemeyi kullanır. Aşağıdaki kod `JsonObject` türünü gösterir.  
  
```csharp  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 Derleme zamanında türlerini bildirmek zorunda kalmadan, JSON nesnelerine ve dizilerine "göz atabileceğinizi" unutmayın. Üst düzey `["root"]` nesnesine yönelik gereksinimin açıklaması için, bkz. [JSON ve XML arasındaki konuya eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> `JsonObject` sınıfı yalnızca bir örnek olarak sağlanır. Kapsamlı olarak test edilmemiştir ve üretim ortamlarında kullanılmamalıdır. Kesin türü belirtilmiş JSON serileştirmesi, `JsonObject`ile çalışırken tür güvenliği olmamasıdır.  
  
 `JsonObject` türünü kullanmak için, istemci işlem sözleşmesinin dönüş türü olarak <xref:System.ServiceModel.Channels.Message> kullanması gerekir.  
  
```csharp  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 `JsonObject`, aşağıdaki kodda gösterildiği gibi oluşturulur.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Oluşturucusu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yöntemi aracılığıyla elde edilen bir <xref:System.Xml.XmlDictionaryReader>alır. Okuyucu, istemci tarafından alınan JSON iletisinin bir XML gösterimini içerir. Daha fazla bilgi için bkz. [JSON ve XML arasındaki konuya eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program aşağıdaki çıktıyı üretir:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi WeaklyTypedJson. sln çözümünü oluşturun.  
  
3. Çözümü çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
