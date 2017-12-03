---
title: "Zayıf yazılmış JSON Seri Hale Getirme Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b804064a2b7a7bb0f587ae1dc2014769ca6e058
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="weakly-typed-json-serialization-sample"></a>Zayıf yazılmış JSON Seri Hale Getirme Örneği
Kullanıcı tanımlı bir tür verilen kablo biçiminde veya kablo biçiminde geri bir kullanıcı tanımlı tür seri durumdan serileştirilirken verilen kullanıcı tanımlı tür hem hizmet hem de istemci kullanılabilir olması gerekir. Genellikle Bunu başarmak için <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği, bu kullanıcı tanımlı türler uygulanır ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik üyeleri için uygulanır. Bu düzenek de JavaScript nesne gösterimi (JSON) nesneleriyle çalışırken konu başlığı altında açıklandığı gibi geçerlidir [nasıl yapılır: seri hale getirmek ve seri durumdan JSON verilerini](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Bazı senaryolarda bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet veya istemci bir hizmet veya Geliştirici denetimi dışında olan istemci tarafından oluşturulan JSON nesnelerine erişim gerekir. Daha fazla Web Hizmetleri, JSON API'leri genel olarak kullanıma sunmak gibi için pratik olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geliştirici, rastgele JSON nesneleri seri durumdan çıkarılacak içine yerel kullanıcı tanımlı türler oluşturmak için. Bu örnek sağlayan bir mekanizma sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geliştiricilerin kullanıcı tanımlı türler oluşturmadan seri durumdan çıkarılmış, rastgele JSON nesneleriyle çalışma. Bu olarak bilinir *zayıf yazılmış serileştirme* JSON nesnelerin içine bir JSON nesnesi seri durumdan çıkarır türü olmadığından derleme zamanında bilinir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örneğin, bir ortak Web hizmeti API'si hizmeti kullanıcı hakkındaki bazı bilgileri açıklar aşağıdaki JSON nesnesi döndürür.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Bu nesne seri durumdan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci aşağıdaki kullanıcı tanımlı türler uygulaması gerekiyor.  
  
```  
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
  
 Bu özellikle istemcinin JSON nesnesinin birden fazla türü işlemek varsa sıkıcı olabilir.  
  
 `JsonObject` Bu örnek tarafından sağlanan türü seri durumdan çıkarılmış JSON nesnesi zayıf yazılmış bir gösterimini sunar. `JsonObject`JSON nesnelerinin arasındaki doğal eşlemeyi kullanır ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sözlükler ve JSON diziler arasındaki eşlemeyi ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizileri. Aşağıdaki kodda gösterildiği `JsonObject` türü.  
  
```  
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
  
 "JSON nesneler ve diziler derleme zamanında kendi türünü bildirmesine gerek kalmadan Tarayabileceğiniz olduğunu" unutmayın. Üst düzey gereksinimi açıklaması için `["root"]` nesne, konusuna [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Sınıfı, yalnızca bir örnek olarak sağlanır. Tamamen test ve üretim ortamlarında kullanılmamalıdır. Zayıf yazılmış JSON seri hale getirme, belirgin bir uygulanır, tür güvenliği ile çalışırken yetersizliğidir `JsonObject`.  
  
 Kullanılacak `JsonObject` türü, istemci işlemi sözleşme kullanmalıdır <xref:System.ServiceModel.Channels.Message> dönüş türü olarak.  
  
```  
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
  
 `JsonObject` Sonra aşağıdaki kodda gösterildiği gibi örneği.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Oluşturucusu geçen bir <xref:System.Xml.XmlDictionaryReader>, aracılığıyla elde <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yöntemi. Okuyucu istemci tarafından alınan JSON ileti XML gösterimini içerir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]konu [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program şu çıkışı üretir:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm WeaklyTypedJson.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Ayrıca Bkz.
