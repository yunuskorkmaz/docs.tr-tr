---
title: Zayıf yazılmış JSON Seri Hale Getirme Örneği
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: 370030671a6a8c6709567bf070411543722ab8d8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842674"
---
# <a name="weakly-typed-json-serialization-sample"></a>Zayıf yazılmış JSON Seri Hale Getirme Örneği
Verilen kablo biçimini veya kablo biçimini geri bir kullanıcı tanımlı türe seri durumdan çıkarılırken bir kullanıcı tanımlı türe serileştirilirken verilen kullanıcı tanımlı tür hem hizmet hem de istemcinin kullanılabilir olması gerekir. Genellikle bunu gerçekleştirmek için <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği, bu kullanıcı tarafından tanımlanan türlerine uygulandığında ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik üyeleri için uygulanır. Bu mekanizma da JavaScript nesne gösterimi (JSON) nesneler ile çalışma konusunda açıklandığı gibi uygulanır [nasıl yapılır: JSON verileri seri hale getrime ve](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Bazı senaryolarda, bir Windows Communication Foundation (WCF) hizmet veya istemcinin hizmet veya geliştiricisinin denetimi dışında olan istemci tarafından oluşturulan JSON nesneleri erişmeniz gerekir. Daha fazla Web Hizmetleri JSON API'leri genel kullanıma gibi hangi rastgele JSON nesneleri seri durumdan çıkarılacak yerel kullanıcı tanımlı türler oluşturmak WCF Geliştirici kullanışsız hale gelebilir. Bu örnek, WCF geliştiricileri, kullanıcı tanımlı türler oluşturmadan seri durumdan çıkarılmış, rastgele JSON nesneleriyle birlikte çalışmasını sağlayan bir mekanizma sağlar. Bu olarak bilinir *zayıf yazılmış serileştirme* JSON nesneleri, içine bir JSON nesnesi seri durumdan çıkarır türü olmadığı için derleme zamanında bilinen.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örneğin, genel bir Web hizmeti API'si açıklayan bir kullanıcı hakkında bazı bilgiler hizmetinin aşağıdaki JSON nesnesi döndürür.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Bu nesnenin serisini kaldırmak için bir WCF istemcisi aşağıdaki kullanıcı tanımlı türler uygulamalıdır.  
  
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
  
 Bu, özellikle istemcinin JSON nesnesinin birden fazla türünü işleyecek şekilde olduğunda hantal olabilir.  
  
 `JsonObject` Bu örnek tarafından sağlanan türü seri durumdan çıkarılmış JSON nesnesi zayıf yazılmış bir gösterimini sunar. `JsonObject` JSON nesneleri arasındaki doğal eşleme kullanır ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sözlükleri ve JSON dizileri arasında eşleme ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizileri. Aşağıdaki kodda gösterildiği `JsonObject` türü.  
  
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
  
 "JSON nesneler ve Diziler, türü derleme zamanında bildirin gerek kalmadan göz atabileceğiniz," unutmayın. Üst düzey gereksinimini açıklaması için `["root"]` nesne, konusuna [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Sınıfı, yalnızca bir örnek olarak sağlanır. Kapsamlı test ve üretim ortamlarında kullanılmamalıdır. Zayıf yazılmış JSON seri hale getirme belirgin bir olduğu çıkarımında tür güvenliği eksikliği ile çalışırken `JsonObject`.  
  
 Kullanılacak `JsonObject` türü, istemci işlem anlaşması kullanmalıdır <xref:System.ServiceModel.Channels.Message> dönüş türü olarak.  
  
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
  
 `JsonObject` Ardından aşağıdaki kodda gösterildiği gibi oluşturulur.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Oluşturucusu alır bir <xref:System.Xml.XmlDictionaryReader>, aracılığıyla edinilen <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yöntemi. Okuyucu, istemci tarafından alınan JSON ileti bir XML temsilini içerir. Daha fazla bilgi için Ek Yardım konusuna [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program şu çıktıyı üretir:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  ' % S'çözüm WeaklyTypedJson.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
