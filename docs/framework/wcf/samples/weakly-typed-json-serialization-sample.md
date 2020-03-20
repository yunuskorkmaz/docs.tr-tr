---
title: Zayıf yazılmış JSON Seri Hale Getirme Örneği
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: bdeaffe31ba9bced28eebcfe294fc9944e5d05d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143596"
---
# <a name="weakly-typed-json-serialization-sample"></a>Zayıf yazılmış JSON Seri Hale Getirme Örneği
Kullanıcı tanımlı bir türü belirli bir tel biçimine seri hale getirdiğinizde veya bir tel biçimini kullanıcı tanımlı bir türe dönüştürdüğünde, verilen kullanıcı tanımlı tür hem hizmette hem de istemcide kullanılabilir olmalıdır. Genellikle bunu gerçekleştirmek <xref:System.Runtime.Serialization.DataContractAttribute> için, öznitelik bu kullanıcı tanımlı <xref:System.Runtime.Serialization.DataMemberAttribute> türlere uygulanır ve öznitelik üyelerine uygulanır. Bu mekanizma, JavaScript Object Notation (JSON) nesneleri ile çalışırken de geçerlidir, konu nasıl açıklandığı [gibi: Serialize ve Deserialize JSON Verileri](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Bazı senaryolarda, bir Windows Communication Foundation (WCF) hizmeti veya istemci, geliştiricinin denetimi dışında bir hizmet veya istemci tarafından oluşturulan JSON nesnelerine erişmelidir. Daha fazla Web hizmeti JSON API'lerini genel olarak ortaya çıkarırken, WCF geliştiricisinin rasgele JSON nesnelerini deserialize etmek için yerel kullanıcı tanımlı türleri oluşturması pratik hale gelebilir. Bu örnek, WCF geliştiricilerinin kullanıcı tanımlı türler oluşturmadan deserialized, rasgele JSON nesneleri ile çalışmasını sağlayan bir mekanizma sağlar. JSON nesnesinin seri sini olarak deserialize ettiği tür derleme zamanında bilinmedığından, bu JSON nesnelerinin *zayıf yazılı serileştirmesi* olarak bilinir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örneğin, genel web hizmeti API'si, hizmetin kullanıcısı hakkında bazı bilgileri açıklayan aşağıdaki JSON nesnesini döndürür.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Bu nesneyi deserialize etmek için, bir WCF istemcisi aşağıdaki kullanıcı tanımlı türleri uygulamak gerekir.  
  
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
  
 Bu hantal olabilir, özellikle istemci JSON nesnesinin birden fazla tür işlemek zorunda.  
  
 Bu `JsonObject` örnek tarafından sağlanan tür, deserialized JSON nesnesinin zayıf bir şekilde yazılmış bir temsilini tanıtır. `JsonObject`JSON nesneleri ve .NET Framework sözlükleri arasındaki doğal eşleme ile JSON dizileri ile .NET Framework dizileri arasındaki eşleme temeline dayanır. Aşağıdaki kod `JsonObject` türünü gösterir.  
  
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
  
 JSON nesnelerine ve dizilerine derleme zamanında kendi türünü bildirmeye gerek kalmadan "göz atabileceğinizi" unutmayın. Üst düzey `["root"]` nesne gereksiniminin açıklaması için [JSON ve XML arasındaki](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)konu Eşleme bölümüne bakın.  
  
> [!NOTE]
> Sınıf `JsonObject` yalnızca örnek olarak sağlanır. Ayrıntılı olarak test edilmemiştir ve üretim ortamlarında kullanılmamalıdır. Zayıf yazılı JSON serileştirme bariz bir sonucu ile `JsonObject`çalışırken tip güvenliği eksikliğidir.  
  
 `JsonObject` Türü kullanmak için istemci işlem sözleşmesinin iade türü olarak kullanılması <xref:System.ServiceModel.Channels.Message> gerekir.  
  
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
  
 Daha `JsonObject` sonra aşağıdaki kodda gösterildiği gibi anında.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 Yapıcı, `JsonObject` <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yöntemle <xref:System.Xml.XmlDictionaryReader>elde edilen bir , alır. Okuyucu, istemci tarafından alınan JSON iletisinin XML temsilini içerir. Daha fazla bilgi için [JSON ve XML arasındaki](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)konu Eşleme'ye bakın.  
  
 Program aşağıdaki çıktıyı üretir:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. [Windows İletişim Temel Örnekleri Bina](../../../../docs/framework/wcf/samples/building-the-samples.md)açıklandığı gibi Çözüm WeaklyTypedJson.sln oluşturun.  
  
3. Çözümü çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
