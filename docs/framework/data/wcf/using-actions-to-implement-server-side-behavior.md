---
title: Sunucu tarafı davranışı uygulamak için eylemleri kullanma
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 4467d52df5dbb134947111e96782e257eef253e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875259"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Sunucu tarafı davranışı uygulamak için eylemleri kullanma

OData eylemleri bağlı bir OData hizmetinden bir kaynağı görevi gören bir davranışı uygulamak için bir yol sağlar. Örneğin bir kaynak olarak dijital film göz önünde bulundurun, dijital film ile yapabilir birçok şey vardır: kullanıma, oranı/açıklama veya iade etme. Tüm örnekleri dijital film yöneten bir WCF veri hizmeti tarafından uygulanan eylemler şunlardır. Eylem çağrılabilir bir kaynağı içeren bir OData yanıtında eylemler açıklanmaktadır. Kullanıcı dijital film temsil eden bir kaynak istediğinde WCF veri hizmetinden döndürülen yanıtı bu kaynak için kullanılabilir olan eylemler hakkında bilgi içerir. Eylemin kullanılabilirliğini veri hizmeti veya kaynak durumuna bağlı olabilir. Dijital film teslim iade edildikten sonra örnek başka bir kullanıcı tarafından kullanıma için. İstemciler, bir URL belirterek bir eylem çağırabilir. Örneğin, `http://MyServer/MovieService.svc/Movies(6)` belirli bir dijital film tanımlar ve `http://MyServer/MovieService.svc/Movies(6)/Checkout` belirli film eylemini çağırır. Eylemler, kullanıma izin olmadan veri modelinizi kullanıma sunan hizmet modeli. Film hizmet örneğiyle devam, film derecelendirme, ancak doğrudan derecelendirme veri kaynağı olarak kullanıma sunma olanağı sağlamak isteyebilirsiniz. Film derecelendirme ancak derecelendirme veri kaynağı olarak doğrudan erişmek izin vermek için bir oranı eylem uygulayabilirsiniz.
  
## <a name="implementing-an-action"></a>Bir eylem uygulama  
 Bir hizmet eylemi uygulanmalı uygulamak için <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)), ve [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) arabirimleri. <xref:System.IServiceProvider> uygulamanıza almak WCF veri hizmetleri sağlayan [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)). [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) oluşturmak, WCF veri hizmetleri sağlayan bulmak, tanımlamak ve hizmet eylemleri. [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) varsa hizmet eylemleri davranışı uygulayan kodu çağırabilir ve sonuçları elde etmenizi sağlar. WCF Veri Hizmetleri çağrı başına WCF hizmetleri, hizmetin yeni bir örneğini olduğunu unutmayın. hizmet her çağrıldığında oluşturulur.  Gereksiz hiçbir iş hizmeti oluşturulduğunda yapıldığından emin olun.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider> adlı bir yöntem içerir <xref:System.IServiceProvider.GetService%2A>. Bu yöntem, meta veri hizmeti sağlayıcıları ve veri hizmeti eylem sağlayıcıları dahil, hizmet sağlayıcıları sayısını almak için WCF Veri Hizmetleri tarafından çağrılır. Bir veri hizmeti eylem sağlayıcısı için sorulduğunda döndürür, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) uygulaması.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) kullanılabilir eylemler hakkında bilgi almanıza olanak tanıyan yöntemler içerir. Uyguladığınızda [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) hizmetinizin uygulaması tarafından tanımlanan hizmetiniz için meta veriler deneyimlerinizi [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) işlemlerde ve dağıtım için uygun şekilde bu eylemlerin işleme.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [AdvertiseServiceAction yöntemi](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) hangi eylemleri için belirtilen kaynak kullanılabilir olduğunu belirlemek için çağrılır. Bu yöntem, her zaman kullanılabilir olmayan eylemler için yalnızca çağrılır. Eylem durumu istenen kaynağın veya hizmetin durumunu göre OData yanıtına dahil edilip edilmeyeceğini denetlemek için kullanılır. Bu onay nasıl gerçekleştirilir tamamen size bağlıdır. Kullanılabilirliği hesaplamak bir pahalı olduğundan ve geçerli kaynak bir akışta ise, bu denetimi atlamak ve eylem tanıtmak için kabul edilebilir. `inFeed` Parametrenin ayarlanmış `true` döndürülen geçerli kaynak bir akışın parçası ise.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) oluşturmak için çağrılan bir [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) eylemin davranışı uygulayan kodu kapsülleyen bir temsilci içerir. Bu oluşturur [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) örnek ancak eylemi çağırma kullanılamaz. WCF veri hizmeti eylemleri yan etkileri olduğu ve bu değişiklikler diske kaydetmek için güncelleştirme sağlayıcısı ile birlikte çalışması gerekiyor. [IDataServiceInvokable.Invoke](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) yöntemi çağrıldığında güncelleştirme sağlayıcısının SaveChanges() yöntemi çağrılır.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Bu yöntem bir koleksiyonunu döndürür [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) tüm WCF veri hizmeti sunan eylemleri temsil eden örnekleri. [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) eylem adı, parametreleri ve dönüş türü gibi bilgileri içeren bir eylem meta veri gösterimidir.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Bu yöntem tüm koleksiyonunu döndürür [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) belirtilen bağlama parametre türüne bağlı örnekleri. Diğer bir deyişle, tüm [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))(bağlama parametresi türü olarak da bilinir) belirtilen kaynak türüne davranabilir s. Bu hizmet, bu kaynağa karşı çağrılabilen eylemler hakkında bilgi içerecek bir kaynak döndürdüğünde kullanılır. Bu yöntem, yalnızca tam bağlama parametresi türü (türetilmiş tür) bağlayabilirsiniz eylemleri döndürmelidir. Bu yöntem türü ile karşılaşıldı başına istek başına bir kez çağrılır ve sonucu WCF Veri Hizmetleri tarafından önbelleğe alınır.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Bu yöntem için belirtilen arar [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) ve döndürür `true` varsa [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) bulunur. Varsa bulunan [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) döndürülür `serviceAction` `out` parametresi.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Bu arabirim, WCF veri hizmeti eylemi yürütmek için bir yol sağlar. IDataServiceInvokable uygularken, siz 3 işlemler için sorumlu olursunuz:  
  
1. Yakalama ve potansiyel olarak parametreleri hazırlama  
  
2. Invoke() çağrıldığında eylemin gerçekten uygulayan kodu parametreleri gönderme  
  
3. GetResult() kullanılarak alınabilir herhangi depolama Invoke() sonuçlar sağlar. böylece  
  
 Parametre belirteçleri geçirilebilir. Veri hizmeti sağlayıcısı (hazırlama) dönüştürmeniz gerekebilir Durum buysa, kaynakları temsil eden belirteçleri ile çalışan gerçek eyleme dağıtmadan önce bu belirteçleri gerçek Kaynakları Yazmayı mümkün olduğundan bu değildir. Parametre sıraya sonra böylelikle eylemi çağrıldığında oluşan değişiklikleri kaynağa kaydedilmiş ve üzerine yazılma disk düzenlenebilir bir durumda olması gerekir.  
  
 Bu arabirim, iki yöntem gerektirir: Çağırma ve GetResult. Çağırma eylemin davranışı ve GetResult döndürür uygulayan temsilci eylem sonucunu çağırır.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Bir WCF veri hizmeti eylemi çağırma  
 Eylemler, bir HTTP POST isteği kullanılarak çağrılır. Ardından eylem adı kaynak URL'sini belirtir. Parametreleri istek gövdesinde geçirilir. Örneğin, varsa oranı olarak adlandırılan bir eylem ifşa eden MovieService adlı bir hizmet. Belirli bir filmi oranı eylemi çağırmak için aşağıdaki URL'yi kullanabilirsiniz:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Movies(1) hızı ve hızı için istediğiniz film oranı eylemi belirtir. Derecelendirme gerçek değerini HTTP istek gövdesinde, aşağıdaki örnekte gösterildiği gibi olacaktır:  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> Yukarıdaki örnek kod, yalnızca WCF Veri Hizmetleri 5.2 ile çalışır ve daha sonra JSON Light için desteği vardır. WCF Data Services'ın önceki bir sürümünü kullanıyorsanız, json verbose içerik türü şu şekilde belirtmeniz gerekir: `application/json;odata=verbose`.  
  
 Alternatif olarak, aşağıdaki kod parçacığında gösterildiği gibi WCF Veri Hizmetleri istemcisini kullanarak bir eylem çağırabilirsiniz.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 Yukarıdaki kod parçacığında `MoviesModel` sınıfı, WCF veri hizmetine hizmet başvurusu eklemek için Visual Studio kullanılarak oluşturuldu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md)
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [WCF Veri Hizmetleri Geliştirme ve Dağıtma](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)
- [Özel Veri Hizmeti Sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
