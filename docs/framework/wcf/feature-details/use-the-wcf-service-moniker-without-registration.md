---
title: "Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e91889947a17f8cba66d822b857e1c8bc875cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma
Bağlanmak ve ile iletişim kurmak için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulaması hizmeti adresi, bağlama yapılandırma ve hizmet sözleşmesi ayrıntılarını olması gerekir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet bilinen adı genellikle gerekli öznitelik türlerini önceki kaydı aracılığıyla gerekli sözleşme alır, ancak bu olduğu uygun durumlar olabilir. Kayıt yerine, kullanım yoluyla, bir Web Hizmetleri tanım dili (WSDL) belge biçiminde sözleşme tanımı ad edinebilirsiniz `wsdl` parametresi veya kullanımı aracılığıyla meta veri değişimi üzerinden `mexAddress` parametre.  
  
 Bu, bazı hücre değerleri Web hizmeti etkileşimleri burada hesaplanan bir Excel elektronik tablosuna dağıtımı gibi senaryolara olanak sağlar. Bu senaryoda, belgeyi açabilir tüm istemcilere hizmet sözleşmesi derlemesi kaydetmek için uygun olmayabilir. `wsdl` Parametresi veya `mexAddress` parametresi kendi başına bir çözüm sağlar.  
  
> [!NOTE]
>  Karşılıklı kimlik doğrulaması istek ve yanıt değiştirilmesine veya yanıltmaya karşı korumak için kullanılmalıdır. Özellikle, istemcilerin yanıt meta veri değişimi uç nokta hedeflenen güvenilen taraf olduğunu da gösterilmeyeceği için önemlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, hizmet bilinen adı MEX sözleşme ile kullanımını gösterir. Aşağıdaki sözleşme hizmetiyle wsHttpBinding ile sunulur.  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 Oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcisi aşağıdaki örnek ad dizesini kullanılabilir uzak hizmeti.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 İstemci uygulaması yürütülmesi sırasında istemci gerçekleştiren bir `WS-MetadataExchange` sağlanan ile `mexAddress`. Bu adresi, bağlama ve hizmetlerin sayısı sözleşme ayrıntılarını döndürebilir. `address`, `contract`, `contractNamespace`, `binding` Ve `bindingNamespace` parametreleri hedeflenen hizmet tanımlamak için kullanılır. Bu parametreler eşleşen sonra ad yapıları bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağrıları ve uygun sözleşme tanımı istemcisiyle sonra yapılabilir kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, yazılı sözleşme ile.  
  
> [!NOTE]
>  Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi" bildiren bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: kaydetmek ve hizmet bilinen adı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
