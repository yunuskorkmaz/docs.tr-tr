---
title: Filtre Seçme
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 908e905b4196409b00abccccae03436640cbe986
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045973"
---
# <a name="choosing-a-filter"></a>Filtre Seçme
Yönlendirme hizmetini yapılandırırken, doğru ileti filtrelerini seçmek ve bunları aldığınız iletilerle tam olarak eşleştirmenizi sağlamak için yapılandırmak önemlidir. Seçtiğiniz filtreler, eşleşmelerinde çok geniş ise veya yanlış yapılandırıldıysa, iletiler hatalı yönlendirilir. Filtreler çok kısıtlayıcıysa, bazı iletileriniz için geçerli bir yolunuz bulunmayabilir.

## <a name="filter-types"></a>Filtre türleri

Yönlendirme hizmeti tarafından kullanılan filtreleri seçerken, her bir filtrenin nasıl çalıştığını ve gelen iletilerin bir parçası olarak hangi bilgilerin kullanılabilir olduğunu anlamanız önemlidir. Örneğin, tüm iletiler aynı uç nokta üzerinden alınmışsa, tüm iletiler bu filtrelerle eşleştiğinden adres ve EndpointName filtreleri yararlı değildir.

### <a name="action"></a>Eylem

Eylem filtresi, <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> özelliği inceler. İletideki eylem üstbilgisinin içeriği, filtre yapılandırmasında belirtilen filtre verileri değeriyle eşleşiyorsa, bu filtre döndürülür `true`. Aşağıdaki örnek, bir `FilterElement` `http://namespace/contract/operation/`değeri içeren bir eylem üst bilgisine sahip iletileri eşleştirmek için eylem filtresini kullanan bir tanımlar.

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

Bu filtre, benzersiz bir eylem üst bilgisi içeren iletileri yönlendirçalışırken kullanılmalıdır.

### <a name="endpointaddress"></a>EndpointAddress

EndpointAddress filtresi, iletinin alındığı EndpointAddress öğesini inceler. İletinin ulaştığı adres, filtre yapılandırmasında belirtilen filtre adresiyle tam olarak eşleşiyorsa, bu filtre döndürülür `true`. Aşağıdaki örnek, "http:// `FilterElement` \<hostname >/vdir/s.svc/b" ile adreslenen tüm iletilerle eşleştirmek için adres filtresini kullanan bir tanımlar.

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Bir adresin ana bilgisayar adı bölümünün, istemcinin tam etki alanı adı, NetBIOS adı, IP adresi veya başka bir ad kullanıp kullanmadığını dikkate almak önemlidir. Farklı değerler aynı konağa başvurabileceğinden, bu karşılaştırma için varsayılan davranış, eşleşmeleri gerçekleştirirken adresin ana bilgisayar adı kısmını kullanmamalıdır.
>
> Bu davranış, yönlendirme hizmetini programlı bir şekilde yapılandırırken karşılaştırmanın ana bilgisayar adını değerlendirmesi için değiştirilebilir.

Gelen iletiler benzersiz bir adrese değinilmesi durumunda bu filtre kullanılmalıdır.

### <a name="endpointaddressprefix"></a>EndpointAddressPrefix

EndpointAddressPrefix filtresi EndpointAddress filtresine benzerdir. EndpointAddressPrefix filtresi, iletinin alındığı EndpointAddress öğesini inceler. Ancak EndpointAddressPrefix filtresi, filtre yapılandırmasında belirtilen değerle başlayan adresleriyle eşleşen bir joker karakter görevi görür. Aşağıdaki örnek, ile `FilterElement` `http://<hostname>/vdir*`bahsedilen tüm iletileri eşleştirmek için EndpointAddressPrefix filtresini kullanan bir tanımlar.

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> Bir adresin ana bilgisayar adı bölümünün, istemcinin tam etki alanı adı, NetBIOS adı, IP adresi veya başka bir ad kullanıp kullanmadığını dikkate almak önemlidir. Farklı değerler aynı konağa başvurabileceğinden, bu karşılaştırma için varsayılan davranış, eşleşmeleri gerçekleştirirken adresin ana bilgisayar adı kısmını kullanmamalıdır.

Bu filtre, ortak adres ön ekini paylaşan gelen iletileri yönlendirmesinde kullanılmalıdır.

### <a name="and"></a>AND

Ve filtresi bir ileti içindeki bir değer üzerinde doğrudan filtrelemez, ancak her iki filtrenin de ve filtresi `AND` `true`hesaplanmadan önce iletiyle eşleşmesi gereken bir koşul oluşturmak için iki diğer filtreyi birleştirmenize olanak tanır. Bu, yalnızca tüm alt filtreler eşleşiyorsa eşleşen karmaşık filtreler oluşturmanıza olanak sağlar. Aşağıdaki örnek bir adres filtresini ve bir eylem filtresini tanımlar ve ardından bir iletiyi hem adres hem de eylem filtrelerine karşı değerlendiren bir ve filtresi tanımlar. Hem adres hem de eylem filtresi eşleşiyorsa, ve filtresi döndürülür `true`.

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

Bu filtre, bir eşleşmenin ne zaman yapılması gerektiğini öğrenmek için birden çok filtreden mantığı birleştirmeniz gerektiğinde kullanılmalıdır. Örneğin, belirli adreslere yalnızca belirli eylem ve ileti birleşimlerini alması gereken birden çok hedef varsa, gerekli eylem ve adres filtrelerini birleştirmek için bir ve filtresi kullanabilirsiniz.

### <a name="custom"></a>Özel

Özel filtre türünü seçerken, bu filtre için kullanılacak **MessageFilter** uygulamasını içeren derlemenin türünü Içeren bir CustomType değeri sağlamanız gerekir. Ayrıca, filterData özel filtrenin ileti değerlendirmesi için ihtiyaç duyduğu herhangi bir değer içermelidir. Aşağıdaki örnek, `CustomAssembly.MyCustomMsgFilter` MessageFilter `FilterElement` uygulamasını kullanan bir tanımlar.

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

İle birlikte [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]sunulan filtrelerin kapsamına girmeyen bir iletiye karşı özel bir eşleştirme mantığı gerçekleştirmeniz gerekiyorsa, **MessageFilter** sınıfının uygulanması olan özel bir filtre oluşturmanız gerekir. Örneğin, gelen iletideki bir alanı, yapılandırmaya göre filtreye verilen bilinen değerler listesiyle karşılaştırarak veya belirli bir ileti öğesini karma hale getirir ve sonra filtrenin bu değeri inceleyerek filtre olup olmadığını belirleyebilirsiniz. `true` veya`false`döndürmelidir.

### <a name="endpointname"></a>EndpointName

EndpointName filtresi, iletiyi alan uç noktanın adını inceler. Aşağıdaki örnek, "svcendpoint" üzerinde alınan iletileri yönlendirmek için EndpointName filtresini kullanan bir `FilterElement` tanımlar.

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

Bu filtre, yönlendirme hizmeti birden fazla adlandırılmış hizmet uç noktası açığa çıkardığı zaman yararlıdır. Örneğin, yönlendirme hizmetinin iletileri almak için kullandığı iki uç noktayı kullanıma sunmanız gerekebilir; biri, iletilerinin gerçek zamanlı işlenmesini gerektiren öncelikli müşteriler tarafından kullanılır, diğer uç nokta zamana duyarlı olmayan iletileri alır.

Genellikle bir iletinin hangi bitiş noktasına alındığını tespit etmek için tam adres eşleştirmeyi kullanabilirsiniz. bunun yerine, tanımlanan uç nokta adının kullanılması, özellikle de bir yapılandırma kullanarak bir yönlendirme hizmeti yapılandırılırken daha az hata durumunda olan kullanışlı bir kısayoldur. dosya (uç nokta adları gerekli bir özniteliktir).

### <a name="matchall"></a>MatchAll

MatchAll filtresi, alınan tüm iletiyle eşleşir. Alınan tüm iletilerin bir kopyasını depolayan günlüğe kaydetme hizmeti gibi, tüm alınan iletileri her zaman belirli bir uç noktasına yönlendirdiğinizde yararlıdır. Aşağıdaki örnek, Matchall `FilterElement` filtresini kullanan bir tanımlar.

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a>XPath

XPath filtresi, ileti içinde belirli bir öğeyi denetlemek için kullanılan bir XPath sorgusu belirtmenize olanak tanır. XPath filtreleme, ileti içinde herhangi bir XML adreslenebilir girişi doğrudan incelemenize olanak tanıyan güçlü bir filtreleme seçeneğidir; Ancak, aldığınız iletilerin yapısına özgü bir bilginiz olmasını gerektirir. Aşağıdaki örnek, "NS `FilterElement` " ad alanı öneki tarafından başvurulan ad alanı içinde "element" adlı bir öğenin iletisini incelemek için XPath filtresini kullanan bir tanımlar.

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

Bu filtre, aldığınız iletilerin belirli bir değer içerdiğini biliyorsanız yararlıdır. Örneğin, aynı hizmetin iki sürümünü barındırıyorsanız ve hizmetin yeni sürümüne ait olan iletilerin özel bir üst bilgide benzersiz bir değer içerdiğini biliyorsanız, bu üstbilgiye gitmek için XPath kullanan bir filtre oluşturabilir ve bu değeri önceden kullanabilirsiniz filtrenin eşleşip eşleşmediğini öğrenmek için üst bilgide filtre yapılandırmasında verilen başka bir şekilde.

XPath sorguları genellikle uzun veya karmaşık dize değerleri olan benzersiz ad alanları içerdiğinden, XPath filtresi, ad alanlarınızın benzersiz öneklerini tanımlamak için ad alanı tablosunu kullanmanıza olanak sağlar. Ad alanı tablosu hakkında daha fazla bilgi için bkz. [Ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).

XPath sorguları tasarlama hakkında daha fazla bilgi için bkz. [XPath sözdizimi](https://go.microsoft.com/fwlink/?LinkId=164592).

## <a name="see-also"></a>Ayrıca bkz.

- [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [Nasıl yapılır: Filtreleri kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
