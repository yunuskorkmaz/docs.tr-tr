---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: 16f428b614fe331faffabab477c6584fb682801d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955240"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma
Bir Windows Communication Foundation (WCF) hizmetine bağlanmak ve iletişim kurmak için, bir WCF istemci uygulaması hizmet adresi, bağlama yapılandırması ve hizmet sözleşmesinin ayrıntılarına sahip olmalıdır.  
  
 WCF hizmeti bilinen adı genellikle gerekli öznitelik türlerinin önceki kayıtları aracılığıyla gerekli sözleşmeyi edinir, ancak bunun olanaklı olmadığı durumlar olabilir. Kayıt yerinde, ad, sözleşmenin tanımını bir Web Hizmetleri tanım dili (wsdl) belgesi biçiminde, `wsdl` parametre kullanımı veya meta veri değişimi `mexAddress` aracılığıyla, parametresinin.  
  
 Bu, bazı hücre değerlerinden bazıları Web hizmeti etkileşimleri aracılığıyla hesaplanıyorsa Excel elektronik tablosunun dağıtılması gibi senaryolara izin vermez. Bu senaryoda, belge açmış olabilecek tüm istemcilere hizmet sözleşmesi derlemesini kaydetmek uygun olmayabilir. `wsdl` Parametresi`mexAddress` veya parametresi, bağımsız bir çözüm sunar.  
  
> [!NOTE]
> Karşılıklı kimlik doğrulaması, istek ve yanıt üzerinde değişiklik yapılmasını veya yanıltmayı korumak için kullanılmalıdır. Özellikle, istemcilerin yanıt veren meta veri değişimi uç noktasının amaçlanan güvenilen taraf olduğundan emin olmak önemlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, hizmet adının bir MEX sözleşmesiyle kullanımını gösterir. Bir wsHttpBinding ile aşağıdaki sözleşmeye sahip bir hizmet sunulur.  
  
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
  
 Uzak hizmet için bir WCF istemcisi oluşturmak üzere aşağıdaki örnek bilinen ad dizesi kullanılabilir.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 İstemci uygulamasının yürütülmesi sırasında istemci, belirtilen `WS-MetadataExchange` `mexAddress`ile bir kullanır. Bu işlem, birkaç hizmet için adres, bağlama ve Sözleşme ayrıntılarını döndürebilir. `address` ,`contract` ,Ve`bindingNamespace`parametreleri amaçlanan hizmeti belirlemek için kullanılır. `binding` `contractNamespace` Bu parametreler eşleştirildiği sürece bilinen ad, uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrılar, yazılı sözleşmede olduğu gibi WCF istemcisi kullanılarak yapılabilir.  
  
> [!NOTE]
> Bilinen ad hatalı biçimlendirilmiş veya hizmet kullanılamaz durumdaysa, çağrı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet bilinen adını kaydetme ve yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
