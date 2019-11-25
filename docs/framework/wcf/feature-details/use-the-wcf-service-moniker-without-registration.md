---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: c08fc362694469560eb7368eb5e536c08ec19bdf
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975992"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma
Bir Windows Communication Foundation (WCF) hizmetine bağlanmak ve iletişim kurmak için, bir WCF istemci uygulaması hizmet adresi, bağlama yapılandırması ve hizmet sözleşmesinin ayrıntılarına sahip olmalıdır.  
  
 WCF hizmeti bilinen adı genellikle gerekli öznitelik türlerinin önceki kayıtları aracılığıyla gerekli sözleşmeyi edinir, ancak bunun olanaklı olmadığı durumlar olabilir. Kayıt yerinde, bilinen ad, `mexAddress` parametresinin kullanımı aracılığıyla `wsdl` parametresi veya meta veri değişimi aracılığıyla bir Web Hizmetleri tanım dili (WSDL) belgesi biçiminde sözleşmenin tanımını alabilir.  
  
 Bu, bazı hücre değerlerinden bazıları Web hizmeti etkileşimleri aracılığıyla hesaplanıyorsa Excel elektronik tablosunun dağıtılması gibi senaryolara izin vermez. Bu senaryoda, belge açmış olabilecek tüm istemcilere hizmet sözleşmesi derlemesini kaydetmek uygun olmayabilir. `wsdl` parametresi veya `mexAddress` parametresi, kendi içinde bir çözüm sunar.  
  
> [!NOTE]
> Karşılıklı kimlik doğrulaması, istek ve yanıt üzerinde değişiklik yapılmasını veya yanıltmayı korumak için kullanılmalıdır. Özellikle, istemcilerin yanıt veren meta veri değişimi uç noktasının amaçlanan güvenilen taraf olduğundan emin olmak önemlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, hizmet adının bir MEX sözleşmesiyle kullanımını gösterir. Bir wsHttpBinding ile aşağıdaki sözleşmeye sahip bir hizmet sunulur.  
  
```csharp
using System.ServiceModel;  
  
// ...
  
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
  
 İstemci uygulamasının yürütülmesi sırasında istemci, sağlanmış `mexAddress`bir `WS-MetadataExchange` gerçekleştirir. Bu işlem, birkaç hizmet için adres, bağlama ve Sözleşme ayrıntılarını döndürebilir. `address`, `contract`, `contractNamespace`, `binding` ve `bindingNamespace` parametreleri amaçlanan hizmeti belirlemek için kullanılır. Bu parametreler eşleştirildiği sürece bilinen ad, uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrılar, yazılı sözleşmede olduğu gibi WCF istemcisi kullanılarak yapılabilir.  
  
> [!NOTE]
> Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, `GetObject` çağrısı "geçersiz sözdizimi" belirten bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
