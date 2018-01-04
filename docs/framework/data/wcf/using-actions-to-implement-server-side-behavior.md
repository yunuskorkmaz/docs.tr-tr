---
title: "Sunucu tarafı davranışı uygulamak için Eylemler kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d8ca19a5a49815130103672f43452ebbfedfae3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Sunucu tarafı davranışı uygulamak için Eylemler kullanma
OData eylemlerinin bir OData hizmetinden alınan bir kaynağa bağlı görevi gören bir davranış uygulamak için bir yol sağlar.  Örneğin bir kaynak olarak dijital bir filmi göz önünde bulundurun, dijital bir filmi yapabilir pek çok şey vardır: kullanıma, oranı/açıklama veya iade etme. Bunlar tüm dijital filmler yöneten bir WCF veri hizmeti tarafından uygulanan eylemler örneğidir. Eylem çağrılabilen bir kaynağı içeren bir OData yanıtında eylemler açıklanmaktadır. Bir kullanıcının dijital film temsil eden bir kaynak istediğinde WCF veri hizmetinden döndürülen yanıt bu kaynak için kullanılabilir olan eylemler hakkında bilgi içerir. Bir eylem kullanılabilirliğini veri hizmet ya da kaynak durumuna bağlı olabilir. Dijital film teslim iade edildikten sonra örnek başka bir kullanıcı tarafından kullanıma alınamıyor için. İstemciler, bir URL belirterek bir eylem çağırabilirsiniz. Örneğin http://MyServer/MovieService.svc/Movies (6) belirli bir dijital film belirleyin ve http://MyServer/MovieService.svc/Movies (6) / Checkout belirli film eylemini çağıracaktır. Eylemler izin verir, kullanıma sunmak veri modelinizi gösterme olmadan hizmet modeli. Film hizmet örnekle devam edersek, film derecelendirme, ancak bir kaynak olarak derecelendirme verileri doğrudan açığa yapmalarına izin vermek isteyebilirsiniz. Film derecelendirme ancak derecelendirme veri kaynağı olarak doğrudan erişmek kullanıcı izin vermek için bir oran eylem uygulamanız.  
  
## <a name="implementing-an-action"></a>Bir eylem uygulama  
 Uygulaması gerekiyor bir hizmet eylemi uygulamak için <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), ve [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) arabirimleri. <xref:System.IServiceProvider>uygulamanıza almak WCF veri hizmetleri sağlayan [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) oluşturmak WCF veri hizmetleri sağlayan bulmak, açıklar ve hizmet eylemleri çağırma. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) varsa hizmet eylemleri davranışı uygulayan kod çağırabilir ve sonuçları elde olanak tanır. WCF Veri Hizmetleri çağrı başına WCF hizmetleri, hizmetin yeni bir örneğini olduğunu unutmayın, hizmetin her çağrıldığında oluşturulur.  Hizmet oluşturulduğunda gereksiz çalışma yapıldığından emin olun.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider>adlı bir yöntem içerir <xref:System.IServiceProvider.GetService%2A>. Bu yöntem, bir dizi hizmet sağlayıcılarının, meta veri hizmet sağlayıcıları ve veri sağlayıcılarını eylem dahil almak için WCF Veri Hizmetleri tarafından çağrılır. Bir veri hizmeti eylem sağlayıcısı için sorulduğunda, dönüş, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) uygulaması.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) kullanılabilir eylemler hakkında bilgi almak sağlayan yöntemler içerir. Ne zaman uygulamanız [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) hizmetinizin uygulama tarafından tanımlanan hizmetiniz için meta veriler program.cs'ye [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) eylemlerle ve Bu eylemleri gerektiği için gönderme işleme.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) hangi eylemleri belirtilen kaynak için kullanılabilir olduğunu belirlemek için çağrılır. Bu yöntem yalnızca her zaman kullanılabilir olmayan eylemler için çağrılır. Bu eylem istenen kaynağın durumunu veya hizmeti durumunu göre OData yanıtı dahil edilmesi gereken varsa denetlemek için kullanılır. Bu onay nasıl yapıldığını tamamen size bağlıdır. Pahalı bir kullanılabilirliği hesaplamak ise ve geçerli kaynak bir akışta ise denetimi atlamak ve eylem tanıtmak için kabul edilebilir. `inFeed` Parametrenin ayarlanmış `true` döndürülen geçerli kaynak bir akış parçası ise.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) oluşturmak için çağrılan bir [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) eylemin davranışı uygulayan kod yalıtan bir temsilci içerir. Bu oluşturur [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) örnek ancak eylemi çağırma kullanılamaz. WCF veri hizmeti eylemleri yan etkileri var ve bu değişiklikleri diske kaydetmek için güncelleştirme sağlayıcısı ile birlikte çalışmak gerekiyor. [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) yöntemi yöntemi çağrıldığında güncelleştirme sağlayıcının SaveChanges() çağrılır.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Bu yöntem koleksiyonu döndürür [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) tüm WCF veri hizmeti sunan eylemleri temsil eden örnekleri. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) eylem adı, parametrelerini ve dönüş türü gibi bilgileri içeren bir eylem, meta veri gösterimidir.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Bu yöntem tüm koleksiyonunu döndürür [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) için belirtilen bağlama parametresi türü bağlı örnekleri. Diğer bir deyişle, tüm [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)(bağlama parametresi türü olarak da bilinir) belirtilen kaynak türüne davranamaz s. Bu kaynak karşı çağrılabilir eylemler hakkında bilgi eklemek için bir kaynak hizmeti döndürürse, bu kullanılır. Bu yöntem yalnızca tam bağlama parametresi türü (hiçbir türetilmiş türler) bağlayabilirsiniz Eylemler döndürmelidir. Bu yöntem türü ile karşılaşıldı her istek başına bir kez çağrılır ve sonuç WCF Veri Hizmetleri tarafından önbelleğe alınır.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Bu yöntem için belirtilen arar [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) ve döndürür `true` varsa [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) bulunur. Varsa bulunan [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) döndürülür `serviceAction``out` parametresi.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Bu arabirim bir WCF veri hizmeti eylemi yürütmek için bir yol sağlar. IDataServiceInvokable uygularken 3 işlemler için sorumlu şunlardır:  
  
1.  Yakalama ve potansiyel olarak parametreleri hazırlama  
  
2.  Parametreleri olması çağrıldığında gerçekte eylemi uygulayan kod gönderme  
  
3.  Herhangi bir depolama olması GetResult() kullanılarak alınabilir şekilde sonuçları  
  
 Parametreleri belirteçleri geçirilebilir. (Hazırlama) dönüştürmeniz gerekebilir Durum buysa, kaynakları temsil eden belirteçleri ile çalışan bir veri hizmeti sağlayıcısı gerçek eyleme dağıtmadan önce bu belirteçler gerçek kaynakları yazmak mümkündür olmasıdır. Parametre sıraya sonra böylece eylem çağrıldığında gerçekleşen değişiklikleri kaynağa için yazılmış ve kaydedilmiş disk düzenlenebilir bir durumda olması gerekir.  
  
 Bu arabirim iki yöntem gerektirir: çağırma ve GetResult. Çağırma eylemin sonucu eylemin davranışı ve GetResult döndürür uygulayan temsilcisini çağırır.  
  
## <a name="invoking-a-wcf-data-service-action"></a>WCF veri hizmeti eylemi çağırma  
 Eylemler HTTP POST isteği kullanarak çağrılır. URL, eylem adından kaynağı belirtir. Parametreler istek gövdesinde iletilir. Örneğin, oranı çağrılan bir eylem kullanıma MovieService adlı bir hizmet ise. Belirli bir filmi oranı eylemi çağırmak için aşağıdaki URL'yi kullanabilirsiniz:  
  
 http://MovieServer/MovieService.svc/Movies (1) / oranı  
  
 Movies(1) hızı ve hızı istediğiniz film oranı eylemi belirtir. Derecelendirme gerçek değerini HTTP istek gövdesinde aşağıdaki örnekte gösterildiği gibi olacaktır:  
  
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
>  Yukarıdaki örnek kod yalnızca WCF Veri Hizmetleri 5.2 ile çalışır ve daha sonra JSON light için destek vardır. WCF Veri Hizmetleri daha önceki bir sürümünü kullanıyorsanız, json verbose content-type aşağıdaki gibi belirtmeniz gerekir: `application/json;odata=verbose`.  
  
 Alternatif olarak, aşağıdaki kod parçacığında gösterildiği gibi WCF Veri Hizmetleri istemcisini kullanarak bir eylem çağırabilirsiniz.  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 Yukarıdaki kod parçacığında bulunan `MoviesModel` sınıfı, bir WCF veri hizmetine hizmet Başvurusu Ekle için Visual Studio kullanarak üretilmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md)  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Veri Hizmetleri Geliştirme ve Dağıtma](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Özel Veri Hizmeti Sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
