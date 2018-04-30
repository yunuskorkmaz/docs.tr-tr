---
title: Filtre Seçme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 653013de37278f051f37fdda52e68fc3d84c2cbb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="choosing-a-filter"></a>Filtre Seçme
Yönlendirme hizmeti yapılandırırken, doğru ileti filtreleri seçin ve bunları aldığınız iletileri karşı tam eşleşme yapmanıza izin verecek şekilde yapılandırmak önemlidir. Seçtiğiniz filtre kendi eşleşmeleri aşırı geniş kapsamlı veya yanlış yapılandırılmış iletiler yanlış yönlendirilir. Filtreler çok kısıtlayıcı olması durumunda, kullanılabilir tüm geçerli yollar bazı iletilerinizin olmayabilir.  
  
## <a name="filter-types"></a>Filtre türleri  
 Yönlendirme hizmeti tarafından kullanılan filtreleri seçerken, hangi bilgilerin kullanılabilir yanı sıra her bir filtrenin nasıl çalıştığını anlamak önemlidir gelen iletileri bir parçası olarak. Tüm iletileri aynı uç noktası üzerinden alınırsa, tüm iletileri bu filtreler eşleştiğinden örneği için adres ve EndpointName filtreleri yararlı değildir.  
  
### <a name="action"></a>Eylem  
 Eylem filtresi inceler <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> özelliği. Eylem üst bilgi iletisi içeriği filtre yapılandırmasında belirtilen filtre veri değeri eşleşmesi durumunda bu filtre döndürür `true`. Aşağıdaki örnek tanımlayan bir `FilterElement` iletileri değerini içeren bir eylem üstbilgisi ile eşleşecek şekilde eylem filtresi kullanan "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Bu filtre, benzersiz bir Action üstbilgisi içeren iletileri yönlendirme kullanılmalıdır.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 EndpointAddress filtre iletisi alındı EndpointAddress olup olmadığını denetler. Filtre yapılandırmasında belirtilen filtre adres iletinin tam olarak ulaştığında adresiyle eşleşen sonra bu filtre döndürür `true`. Aşağıdaki örnek tanımlayan bir `FilterElement` gönderilen iletileri eşleşecek şekilde adresi filtresi kullanan "http://\<ana bilgisayar adı > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Bir adresi ana bilgisayar adı bölümü olup tam etki alanı adı, NetBIOS adını, IP adresini veya diğer ad istemcinin göre farklı olabilir dikkate almak önemlidir. Farklı değerleri aynı ana bilgisayarına başvurduğundan bu karşılaştırma için varsayılan davranış adresi ana bilgisayar adı bölümü eşleşmeleri gerçekleştirirken değil kullanmaktır.  
>   
>  Bu davranış, ana bilgisayar adı yönlendirme hizmeti program aracılığıyla yapılandırırken değerlendirmek karşılaştırma izin verecek şekilde değiştirilebilir.  
  
 Gelen iletiler için benzersiz bir adresi ele alınan bu filtre kullanılmalıdır.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 EndpointAddressPrefix filtre EndpointAddress filtre benzer. EndpointAddressPrefix filtre iletisi alındı EndpointAddress olup olmadığını denetler. Ancak EndpointAddressPrefix filtre filtre yapılandırmasında belirtilen değerle başlayan adreslerini eşleştirerek joker karakter olarak işlev görür. Aşağıdaki örnek tanımlayan bir `FilterElement` gönderilen iletileri eşleşecek şekilde EndpointAddressPrefix filtresi kullanan "http://\<ana bilgisayar adı > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Bir adresi ana bilgisayar adı bölümü olup tam etki alanı adı, NetBIOS adını, IP adresini veya diğer ad istemcinin göre farklı olabilir dikkate almak önemlidir. Farklı değerleri aynı ana bilgisayarına başvurduğundan bu karşılaştırma için varsayılan davranış adresi ana bilgisayar adı bölümü eşleşmeleri gerçekleştirirken değil kullanmaktır.  
  
 Bu filtre, ortak bir adres öneki paylaşan gelen iletileri yönlendirme kullanılmalıdır.  
  
### <a name="and"></a>AND  
 VE filtre doğrudan bir ileti içinde bir değerle filtre değil, ancak oluşturmak için iki filtre birleştirmek sağlar bir `AND` burada hem filtreleri eşleşmelidir ileti ve filtresinin önce koşul `true`. Bu, tüm alt filtreleri eşleşirse, yalnızca eşleşen karmaşık filtreler oluşturmanızı sağlar. Aşağıdaki örnekte bir adres filtresi ve bir eylem filtresi tanımlar ve bir ileti adresi ve eylem filtreleriyle değerlendirir ve filtre tanımlar. VE filtre döndürür sonra adres ve eylem filtreleri, eşleşiyorsa `true`.  
  
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
  
 Bir eşleşme ne zaman yapılması gerektiğini belirlemek için birden çok filtre mantığından birlikte kullandığınızda bu filtre kullanılmalıdır. Örneğin, yalnızca belirli eylemler ve birleşimleri belirli adresleri iletileri alması gereken birden çok varış yeri varsa gerekli eylem ve adresi filtrelerini birleştirmeye ve filtre kullanabilirsiniz.  
  
### <a name="custom"></a>Özel  
 Özel filtre türü seçerken içeren bütünleştirilmiş kodun türünü içeren bir customType değeri sağlamalısınız **MessageFilter** Bu filtre için kullanılacak uygulama. Ayrıca, filterData özel filtre iletileri değerlendirilmesinde gerektirebilecek herhangi bir değeri içermelidir. Aşağıdaki örnek tanımlayan bir `FilterElement` kullanan `CustomAssembly.MyCustomMsgFilter` MessageFilter uygulaması.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 İle sağlanan filtreler tarafından kapsanmayan bir ileti karşı özel eşleşen mantık yapmanız gereken [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], uygulamasıdır özel bir filtre oluşturmanız gerekir **MessageFilter** sınıfı. Örneğin, bir alana filtre yapılandırma olarak verilen bilinen değerler listesini karşı gelen ileti karşılaştırır veya belirli ileti öğesi karma hale getirir ve bu değeri belirlemek için inceler özel bir filtre oluşturabilirsiniz olup olmadığını filtresi döndürmelidir `true` veya `false`.  
  
### <a name="endpointname"></a>EndpointName  
 EndpointName filtre iletisi aldı uç noktanın adı olup olmadığını denetler. Aşağıdaki örnek tanımlayan bir `FilterElement` EndpointName filtre "SvcEndpoint" alınan iletileri yönlendirmek için kullanır.  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Bu filtre, yönlendirme hizmeti birden fazla adlandırılmış hizmet uç noktasını kullanıma sunar yararlıdır. Örneğin, yönlendirme hizmeti iletileri almak için kullandığı iki uç nokta açmış olabilirsiniz; gerçek zamanlı diğer uç nokta sırasında iletilerinin işlenmesini duyarlı saat değil iletilerini alır isteyen öncelik müşteriler tarafından kullanılır.  
  
 Genellikle tam kullanabilirsiniz, ancak bir ileti, tanımlanmış uç nokta adı kullanmayı alındı hangi uç noktaya belirlemek için eşleşen daha az hataya, özellikle bir Yapılandırması'nı kullanarak bir yönlendirme hizmeti yapılandırırken görülür kullanışlı bir kısayol adresidir (uç nokta adları gerekli bir öznitelik nerede) dosyası.  
  
### <a name="matchall"></a>MatchAll  
 MatchAll filtre ile eşleşen hiçbir alınan ileti. Tüm alınan iletinin bir kopyasını depolayan bir günlük kaydı hizmeti gibi belirli bir uç nokta için tüm alınan iletileri yönlendirmek her zaman gerekir yararlıdır. Aşağıdaki örnek tanımlayan bir `FilterElement` MatchAll filtre kullanır.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 XPath filtresi iletisi içinde belirli bir öğenin incelemek için kullanılan bir XPath sorgusu belirtmenize olanak tanır. XPath filtresi doğrudan herhangi bir XML adreslenebilir giriş iletisindeki incelemek izin veren bir güçlü filtreleme seçenektir; ancak aldığınız iletileri yapısını belirli bilgisine sahip olmasını gerektirir. Aşağıdaki örnek tanımlayan bir `FilterElement` ileti "ns" ad alanı öneki'tarafından başvurulan ad alanı içindeki "öğesi" adlı bir öğe için incelemek için XPath filtresi kullanan.  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Bu filtre, aldığınız iletileri belirli bir değer içeren biliyorsanız yararlıdır. Örneğin, hizmetinin daha yeni sürümünü gönderilen iletiler özel üstbilgisinde benzersiz bir değer içermesi bildiğiniz iki sürümü aynı hizmet barındırma bu başlığı gitmek için XPath kullanır ve değer pres karşılaştırır bir filtresi oluşturabilirsiniz başka bir filtre eşleşip eşleşmediğini belirlemek için filtre yapılandırmada verilen üstbilgisinde ent.  
  
 XPath sorguları genellikle uzun benzersiz ad alanları genellikle içerir veya karmaşık dize değerlerini XPath filtresi ad alanı tablosu, ad alanları için benzersiz önekleri belirlemek için kullanılır olanak tanıyan çünkü. Ad alanı tablosu hakkında daha fazla bilgi için bkz: [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 XPath sorguları tasarlama hakkında daha fazla bilgi için bkz: [XPath sözdizimi](http://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Nasıl yapılır: Filtreleri Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
