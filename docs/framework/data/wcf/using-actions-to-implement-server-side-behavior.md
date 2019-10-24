---
title: Sunucu tarafı davranışı uygulamak için eylemleri kullanma
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 7068845054e04a002296e7c157655eef6a98db78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774136"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Sunucu tarafı davranışı uygulamak için eylemleri kullanma

OData eylemleri, bir OData hizmetinden alınan bir kaynak üzerinde davranan bir davranışı uygulamak için bir yol sağlar. Örneğin, bir dijital filmi kaynak olarak düşünün, dijital bir filmle yapabileceğiniz pek çok şey vardır: kullanıma alma, oran/açıklama veya iade etme. Bunlar, dijital filmleri yöneten bir WCF veri hizmeti tarafından uygulanabilecek eylemlere örnektir. Eylemler, üzerinde eylemin çağrılabilecek bir kaynağı içeren bir OData yanıtında açıklanır. Bir Kullanıcı dijital bir filmi temsil eden bir kaynak istediğinde, WCF veri hizmetinden döndürülen yanıt, bu kaynak için kullanılabilen eylemler hakkında bilgi içerir. Bir eylemin kullanılabilirliği, veri hizmetinin veya kaynağın durumuna bağlı olabilir. Örneğin, dijital bir film kullanıma alındıktan sonra başka bir kullanıcı tarafından kullanıma alınamaz. İstemciler bir URL belirterek eylemi çağırabilirler. Örneğin, `http://MyServer/MovieService.svc/Movies(6)` belirli bir dijital filmi tanımlayabilir ve `http://MyServer/MovieService.svc/Movies(6)/Checkout` belirli bir filmle eylemi çağıracaktır. Eylemler, veri modelinizi açığa çıkarmadan hizmet modelini kullanıma sunmanıza olanak tanır. Film hizmeti örneğine devam etmek için, bir kullanıcının bir filmi derecelendirmesini, ancak derecelendirme verilerini bir kaynak olarak doğrudan kullanıma sunmasına izin vermek isteyebilirsiniz. Kullanıcının bir filmi derecelendirmesini, ancak derecelendirme verilerine kaynak olarak doğrudan erişemesinin bir ücret eylemi uygulayabilirsiniz.

## <a name="implementing-an-action"></a>Eylem uygulama
 Bir hizmet eylemi uygulamak için <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))ve [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) arabirimlerini uygulamanız gerekir. <xref:System.IServiceProvider>, WCF Veri Hizmetleri [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))uygulamanızı almasına izin verir. [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) , hizmet eylemlerini oluşturma, bulma, açıklama ve çağırma WCF veri Hizmetleri olanak tanır. [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , hizmet eylemlerinin davranışını uygulayan kodu çağıralmanızı ve varsa sonuçları almanızı sağlar. WCF Veri Hizmetleri, her hizmet çağrıldığında hizmetin yeni bir örneğinin oluşturulduğuna dikkat edin, bu da hizmetin her çağrılışında bir hizmetin yeni bir örneğini oluşturulacaktır.  Hizmet oluşturulduğunda gereksiz bir işin yapıldığından emin olun.

### <a name="iserviceprovider"></a>IServiceProvider
 <xref:System.IServiceProvider>, <xref:System.IServiceProvider.GetService%2A> adlı bir yöntem içerir. Bu yöntem, meta veri hizmeti sağlayıcıları ve veri hizmeti eylem sağlayıcıları da dahil olmak üzere birçok hizmet sağlayıcısını almak için WCF Veri Hizmetleri tarafından çağırılır. Bir veri hizmeti eylem sağlayıcısı istendiğinde, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) uygulamanızı geri döndürün.

### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) , kullanılabilir eylemler hakkında bilgi almanıza izin veren yöntemler içerir. [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) 'ı uyguladığınızda, hizmetinizin bu eylemlere yönelik eylemler ve Işleme gönderme işlemleri ile birlikte, hizmetiniz tarafından tanımlanan [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) uygulaması tarafından tanımlanan hizmetinize ait meta verileri genişletmenizi sağlar ilişkili.

#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction
 [Advertiseserviceaction yöntemi](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) , belirtilen kaynak için hangi eylemlerin kullanılabildiğini belirlemek üzere çağırılır. Bu yöntem yalnızca her zaman kullanılabilir olmayan eylemler için çağırılır. İşlemin, istenen kaynağın durumuna veya hizmetin durumuna göre OData yanıtına dahil edilip edilmediğini denetlemek için kullanılır. Bu denetim nasıl gerçekleştirilir? Kullanılabilirliği hesaplamak ve geçerli kaynağın bir akışda olması pahalı ise, denetimi atlamak ve eylemi tanıtmak kabul edilebilir. Döndürülen geçerli kaynak bir akışın parçasıysa `inFeed` parametresi `true` olarak ayarlanır.

#### <a name="createinvokable"></a>Kullanıcılanabilir
 , Eylemin davranışını uygulayan kodu kapsülleyen bir temsilci içeren bir [ıdataserviceınkable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) oluşturmak Için [createınvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) çağırılır. Bu, [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) örneğini oluşturur ancak eylemi çağırmaz. WCF veri hizmeti eylemlerinin yan etkileri vardır ve bu değişiklikleri diske kaydetmek için güncelleştirme sağlayıcısıyla birlikte çalışmanız gerekir. [IDataServiceInvokable. Invoke](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) yöntemi Update sağlayıcının SaveChanges () yönteminden çağrılır.

#### <a name="getserviceactions"></a>GetServiceActions
 Bu yöntem, bir WCF veri hizmetinin sunduğu tüm işlemleri temsil eden [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) örneklerinin bir koleksiyonunu döndürür. [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) , bir eylemin meta veri gösterimidir ve eylem adı, parametreleri ve dönüş türü gibi bilgileri içerir.

#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType
 Bu yöntem, belirtilen bağlama parametre türüne bağlanabilen tüm [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) örneklerinin bir koleksiyonunu döndürür. Diğer bir deyişle, belirtilen kaynak türü üzerinde (Ayrıca bağlama parametre türü olarak da bilinir) işlem yapacak tüm [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))'lar. Bu, hizmet kaynak için çağrılabilecek eylemler hakkında bilgi eklemek için bir kaynak döndürdüğünde kullanılır. Bu yöntem, yalnızca tam bağlama parametre türüne (türetilmiş tür olmadan) bağlanabilir eylemler döndürmelidir. Bu yöntem, tür başına istek başına bir kez çağrılır ve sonuç WCF Veri Hizmetleri tarafından önbelleğe alınır.

#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction
 Bu yöntem, belirtilen bir [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) öğesini arar ve [serviceaction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) bulunursa `true` döndürür. Bulunursa, `serviceAction` `out` parametresinde [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) döndürülür.

### <a name="idataserviceinvokable"></a>Idataserviceınkable
 Bu arabirim, WCF veri hizmeti eylemini yürütmek için bir yol sağlar. Idataserviceınkable 'i uygularken 3 şey sorumludur:

1. Parametreleri yakalama ve potansiyel olarak sıralama

2. Invoke () çağrıldığında eylemi gerçekten uygulayan koda gönderme

3. GetResult () kullanılarak alınabilmesi için Invoke () ' den herhangi bir sonuç depolanıyor

 Parametreler belirteç olarak geçirilebilir. Bunun nedeni, kaynakları temsil eden belirteçlerle birlikte çalışacak bir veri hizmeti sağlayıcısı yazmak, bu durum gerçek eyleme göndermeden önce bu belirteçleri gerçek kaynaklara dönüştürmeniz (sıralamalarınızda) gerekebilir. Parametre sıralandıktan sonra, kaynak, eylem çağrıldığında gerçekleşen tüm değişikliklerin diske kaydedilip diske yazılacağı şekilde düzenlenebilir bir durumda olmalıdır.

 Bu arabirim için iki yöntem gerekir: Invoke ve GetResult. Invoke komut, eylemin davranışını uygulayan temsilciyi çağırır ve GetResult eylemin sonucunu döndürür.

## <a name="invoking-a-wcf-data-service-action"></a>WCF veri hizmeti eylemini çağırma
 Eylemler bir HTTP POST isteği kullanılarak çağrılır. URL, kaynağı ve ardından eylem adını belirtir. Parametreler isteğin gövdesine geçirilir. Örneğin, MovieService adlı bir hizmet varsa, oran adlı bir eylem ortaya çıkarılır. Belirli bir filmin hız eylemini çağırmak için aşağıdaki URL 'YI kullanabilirsiniz:

 `http://MovieServer/MovieService.svc/Movies(1)/Rate`

 Filmler (1) derecelendirmek istediğiniz filmi belirtir ve oran ücret eylemini belirtir. Derecelendirmenin gerçek değeri, aşağıdaki örnekte gösterildiği gibi HTTP isteğinin gövdesinde olacaktır:

```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1
Content-Type: application/json
Content-Length: 20
Host: localhost:15238
{
   "rating": 4
}
```

> [!WARNING]
> Yukarıdaki örnek kod yalnızca JSON ışığı desteği olan WCF Veri Hizmetleri 5,2 ve üzeri sürümlerle çalışır. WCF Veri Hizmetleri önceki bir sürümünü kullanıyorsanız JSON ayrıntılı içerik türü olarak şu şekilde belirtmeniz gerekir: `application/json;odata=verbose`.

 Alternatif olarak, aşağıdaki kod parçacığında gösterildiği gibi WCF Veri Hizmetleri Istemcisini kullanarak bir eylemi çağırabilirsiniz.

```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));
//...
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```

 Yukarıdaki kod parçacığında, `MoviesModel` sınıfı, bir WCF veri hizmetine Hizmet Başvurusu Ekle için Visual Studio kullanılarak oluşturulmuştur.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri 4.5](index.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri Geliştirme ve Dağıtma](developing-and-deploying-wcf-data-services.md)
- [Özel Veri Hizmeti Sağlayıcıları](custom-data-service-providers-wcf-data-services.md)
