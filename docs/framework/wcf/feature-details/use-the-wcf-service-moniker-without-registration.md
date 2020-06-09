---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: f69314948a0e0a69e49ec148f94572f17d0b8e3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595056"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma
Bir Windows Communication Foundation (WCF) hizmetine bağlanmak ve iletişim kurmak için, bir WCF istemci uygulaması hizmet adresi, bağlama yapılandırması ve hizmet sözleşmesinin ayrıntılarına sahip olmalıdır.  
  
 WCF hizmeti bilinen adı genellikle gerekli öznitelik türlerinin önceki kayıtları aracılığıyla gerekli sözleşmeyi edinir, ancak bunun olanaklı olmadığı durumlar olabilir. Kayıt yerinde, ad, bir Web Hizmetleri tanım dili (WSDL) belgesi biçiminde veya parametresi kullanılarak `wsdl` veya meta veri değişimi aracılığıyla sözleşmenin tanımını alabilir `mexAddress` .  
  
 Bu, bazı hücre değerlerinden bazıları Web hizmeti etkileşimleri aracılığıyla hesaplanıyorsa Excel elektronik tablosunun dağıtılması gibi senaryolara izin vermez. Bu senaryoda, belge açmış olabilecek tüm istemcilere hizmet sözleşmesi derlemesini kaydetmek uygun olmayabilir. `wsdl`Parametresi veya parametresi, `mexAddress` bağımsız bir çözüm sunar.  
  
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
  
 İstemci uygulamasının yürütülmesi sırasında istemci, `WS-MetadataExchange` belirtilen ile bir kullanır `mexAddress` . Bu işlem, birkaç hizmet için adres, bağlama ve Sözleşme ayrıntılarını döndürebilir. `address`,, `contract` `contractNamespace` `binding` Ve `bindingNamespace` parametreleri amaçlanan hizmeti belirlemek için kullanılır. Bu parametreler eşleştirildiği sürece bilinen ad, uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrılar, yazılı sözleşmede olduğu gibi WCF istemcisi kullanılarak yapılabilir.  
  
> [!NOTE]
> Bilinen ad hatalı biçimlendirilmiş veya hizmet kullanılamaz durumdaysa, çağrı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma](how-to-register-and-configure-a-service-moniker.md)
