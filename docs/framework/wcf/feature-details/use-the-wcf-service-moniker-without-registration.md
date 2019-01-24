---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: 3ce388da75711ab1378ce59575c067cf828089e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615288"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma
Bağlanmak ve bir Windows Communication Foundation (WCF) hizmetiyle iletişim kurmak için ayrıntıları hizmeti adresi, bağlama yapılandırma ve hizmet sözleşmesi WCF istemci uygulaması olmalıdır.  
  
 WCF hizmet bilinen adı genellikle gerekli sözleşme aracılığıyla önceki kayıt gerekli öznitelik türlerini alır, ancak bu mantıklı olduğu durumlar olabilir. Kayıt yerine, kullanımının, Web Hizmetleri tanım dili (WSDL) belgenin biçiminde sözleşme tanımı ad edinebilirsiniz `wsdl` parametresi veya kullanımı aracılığıyla meta veri değişimi üzerinden `mexAddress` parametre.  
  
 Bu, burada hücre değerlerinin bazıları Web hizmeti etkileşimler hesaplanır bir Excel elektronik tablosuna dağıtımını gibi senaryolara olanak sağlar. Bu senaryoda, belgeyi açabilir tüm istemcilere hizmet sözleşme derlemesi kaydetmek için uygun olmayabilir. `wsdl` Parametresi veya `mexAddress` parametresi kendi başına bir çözüm sağlar.  
  
> [!NOTE]
>  Karşılıklı kimlik doğrulaması, istek ve izinsiz veya yanıltma yanıt karşı korumak için kullanılmalıdır. Özellikle, istemcilerin yanıt meta veri değişimi uç noktası hedeflenen güvenilen taraf olduğunu garanti için önemlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, hizmet bilinen adı MEX sözleşme ile kullanımını gösterir. Şu sözleşme hizmetiyle bir wsHttpBinding kullanıma sunulur.  
  
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
  
 Aşağıdaki örnek bilinen ad dizesini uzak hizmet için bir WCF istemcisi oluşturmak için kullanılabilir.  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 İstemci uygulama yürütme sırasında istemci gerçekleştiren bir `WS-MetadataExchange` ile sağlanan `mexAddress`. Bu adres, bağlama ve bir dizi hizmet için podrobnosti o kontraktu döndürebilir. `address`, `contract`, `contractNamespace`, `binding` Ve `bindingNamespace` parametreleri hedeflenen hizmet tanımlamak için kullanılır. Bu parametreleri eşleşen sonra ad uygun sözleşme tanımına sahip bir WCF istemcisi oluşturur ve çağrıları ardından WCF istemcisi kullanarak sözleşmenin yazılı olarak ile yapılabilir.  
  
> [!NOTE]
>  Bilinen ad hatalı veya hizmet kullanılamıyor durumunda çağrısı `GetObject` "Geçersiz sözdizimi" belirten bir hata döndürür. Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Kaydetme ve hizmet bilinen adı yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
