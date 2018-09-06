---
title: Filtre Seçme
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: bc3bba9a2b00b35f3e0cff1786ea98cfa881f311
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743156"
---
# <a name="choosing-a-filter"></a>Filtre Seçme
Yönlendirme hizmeti yapılandırırken, doğru ileti filtreleri seçin ve bunları tam eşleşme aldığınız mesajlarına karşı yapmanıza izin verecek şekilde yapılandırmak önemlidir. Seçtiğiniz filtreler kendi eşleşmelerin aşırı geniş kapsamlı veya yanlış yapılandırılırsa, iletiler yanlış yönlendirilir. Filtreleri çok fazla kısıtlayıcıysa, kullanılabilir tüm geçerli rotalar iletilerinizi bazıları için sahip olmayabilir.  
  
## <a name="filter-types"></a>Filtre türleri  
 Yönlendirme hizmeti tarafından kullanılan filtreler seçerken, hangi bilgilerin kullanılabilir yanı sıra her bir filtrenin nasıl çalıştığını anlamanız önemli gelen iletiler bir parçası olarak. Tüm iletiler aynı uç noktası üzerinden alınırsa, tüm iletileri bu filtrelerle eşleşen örneği için adres ve Uçnoktaadı filtreleri kullanışlı değildir.  
  
### <a name="action"></a>Eylem  
 Eylem filtresi inceler <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> özelliği. İleti eylem başlığında içeriğini filtre yapılandırmasında belirtilen filtre veri değeri eşleşen ardından bu filtre döndürür `true`. Aşağıdaki örnekte tanımlayan bir `FilterElement` iletileri değerini içeren bir eylem üst bilgisi ile eşleşecek şekilde eylem filtresi kullanan "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Bu filtre, benzersiz bir eylem üst bilgisi içeren iletileri yönlendirme kullanılmalıdır.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 EndpointAddress filtre iletisi alındı EndpointAddress inceler. İleti tam olarak ulaştığında adres filtresi yapılandırmasında belirtilen filtre adresi eşleşen ardından bu filtre döndürür `true`. Aşağıdaki örnekte tanımlayan bir `FilterElement` gönderilen iletileri eşleşmesi için adres filtresi kullanan "http://\<ana bilgisayar adı > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Bir adresi konak adı kısmı istemci tam etki alanı adı, NetBIOS adı, IP adresi veya diğer adı kullanıp kullanmadığını göre değişebilir dikkat edin önemlidir. Farklı değerleri de aynı konağa başvurabilir olduğundan, bu karşılaştırma için varsayılan davranış adresi konak adı kısmı eşleşme gerçekleştirirken değil kullanmaktır.  
>   
>  Bu davranışı, ana bilgisayar adı, yönlendirme hizmeti programlı bir şekilde yapılandırırken değerlendirmek karşılaştırma izin verecek şekilde değiştirilebilir.  
  
 Bu filtre benzersiz bir adrese gönderilen gelen iletiler kullanılmalıdır.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 EndpointAddressPrefix filtre EndpointAddress filtreye benzerdir. EndpointAddressPrefix filtre iletisi alındı EndpointAddress inceler. Ancak EndpointAddressPrefix filtre, filtre yapılandırmasında belirtilen değerle başlayan adresler eşleşen bir joker karakter olarak görür. Aşağıdaki örnekte tanımlayan bir `FilterElement` gönderilen iletileri eşleştirilecek EndpointAddressPrefix filtresi kullanan "http://\<ana bilgisayar adı > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Bir adresi konak adı kısmı istemci tam etki alanı adı, NetBIOS adı, IP adresi veya diğer adı kullanıp kullanmadığını göre değişebilir dikkat edin önemlidir. Farklı değerleri de aynı konağa başvurabilir olduğundan, bu karşılaştırma için varsayılan davranış adresi konak adı kısmı eşleşme gerçekleştirirken değil kullanmaktır.  
  
 Bu filtre, ortak bir adres öneki paylaşan gelen iletileri yönlendirme kullanılmalıdır.  
  
### <a name="and"></a>AND  
 VE filtre doğrudan bir ileti içindeki bir değerin üzerinde filtre, ancak oluşturmak için iki filtre birleştirmenizi sağlar bir `AND` burada her iki filtreleri eşleşmelidir ileti ve filtresinin önce koşul `true`. Bu, tüm alt filtrelerle eşleşen, yalnızca eşleşen karmaşık filtreler oluşturmanızı sağlar. Aşağıdaki örnek, bir adres filtresi ve bir eylem filtresi tanımlar ve sonra bir ileti adresi ve eylem filtreleriyle değerlendiren bir ve filtre tanımlar. VE filtre verir hem adresi hem de eylem filtreleri, eşleşiyorsa `true`.  
  
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
  
 Bir eşleşme olduğunda yapılması gerektiğini belirlemek için birden çok filtre mantığından birleştirdiğinizde gerekir, bu filtre kullanılmalıdır. Örneğin, yalnızca belirli birleşimleri Eylemler ve iletileri belirli adresleri için almaları gerekir birden çok hedefe sahip, gerekli eylem ve adresi filtrelerini birleştirmeye ve filtre kullanabilirsiniz.  
  
### <a name="custom"></a>Özel  
 Özel filtre türü seçerken içeren bütünleştirilmiş kodun türünü içeren customType değeri sağlamalısınız **MessageFilter** Bu filtre için kullanılacak uygulama. Ayrıca, filtre veri iletileri kendi değerlendirmesinde özel filtre gerektirebilecek herhangi bir değeri içermelidir. Aşağıdaki örnekte tanımlayan bir `FilterElement` kullanan `CustomAssembly.MyCustomMsgFilter` MessageFilter uygulaması.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 İle sağlanan filtreler tarafından kapsanmayan bir ileti karşı özel eşleşen mantıksal gerçekleştirmek gereken [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], özel bir filtre uygulamasıdır oluşturmalısınız **MessageFilter** sınıfı. Örneğin, bir alana filtre yapılandırması için verilen bilinen değer listesiyle gelen ileti karşılaştırır veya belirli ileti öğesi karma hale getirir ve sonra bu değeri belirlemek için inceler özel filtre oluşturabilirsiniz olmadığını filtresi döndürmelidir `true` veya `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Uçnoktaadı filtre ileti alındı. uç nokta adı olup olmadığını denetler. Aşağıdaki örnekte tanımlayan bir `FilterElement` Uçnoktaadı filtre "SvcEndpoint" alınan iletileri yönlendirmek için kullanır.  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Bu filtre, birden fazla adlandırılmış hizmet uç noktası yönlendirme hizmeti sunan yararlıdır. Örneğin, yönlendirme hizmeti, iletileri almak için kullanır. iki uç noktalarını kullanıma; gerçek zamanlı başka bir uç noktası hata iletilerinin işlenmesini duyarlı saat değil iletileri alan isteyen öncelik müşteriler tarafından kullanılır.  
  
 Genellikle tam kullanabilirsiniz, ancak adresine bir ileti, tanımlı bir uç nokta adı kullanmayı alındı hangi uç noktaya belirlemek için eşleşen, genellikle daha az hata yapmaya açık, özellikle bir Yapılandırması'nı kullanarak bir yönlendirme hizmeti yapılandırırken olan uygun bir kısayol bulunur. (uç nokta adları gerekli bir öznitelik olduğu) dosyası.  
  
### <a name="matchall"></a>MatchAll  
 MatchAll filtre herhangi bir alınan ileti ile eşleşir. Alınan iletilerin tümünü bir kopyasını depolayan bir günlüğe kaydetme hizmeti gibi belirli bir uç noktası için tüm alınan iletileri yönlendirmek her zaman gerekir, yararlı olur. Aşağıdaki örnekte tanımlayan bir `FilterElement` MatchAll filtresi kullanan.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 XPath filtresi ileti içinde belirli bir öğeyi incelemek için kullanılan bir XPath sorgusu belirtmenize olanak verir. XPath filtresi doğrudan herhangi bir XML adreslenebilir giriş iletisi içinde incelemek izin veren bir güçlü filtreleme seçeneğidir; Ancak, aldığınız iletileri yapısının olan özel bilgilere sahip olmasını gerektirir. Aşağıdaki örnekte tanımlayan bir `FilterElement` ileti "ns" ad alanı öneki'tarafından başvurulan ad alanı içinde "öğesi" adlı bir öğe için incelemek için XPath filtresi kullanan.  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Bu filtre, aldığınız iletileri belirli bir değer içeren biliyorsanız, kullanışlıdır. Örneğin, iki sürümü aynı hizmet barındırıyorsanız ve bildiğiniz hizmetinin daha yeni sürümü için gönderilen iletiler gelmeyecek özel bir başlık içinde benzersiz bir değer içeren bu başlığına giderek XPath kullanır ve değer SrktTanıt karşılaştıran filtre oluşturabilirsiniz başka bir filtre eşleşip eşleşmediğini belirlemek için filtre yapılandırmasında belirtilen üst bilgisindeki ent.  
  
 XPath genellikle sorguladığından genellikle uzun benzersiz ad alanlarında bulunur veya karmaşık dize değerleri, XPath filtresi ad tablosu, ad alanları için benzersiz önekleri tanımlamak için kullanmanıza olanak tanır. Ad alanı tablosu hakkında daha fazla bilgi için bkz. [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 XPath sorguları tasarlama hakkında daha fazla bilgi için bkz. [XPath sözdizimi](https://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Nasıl yapılır: Filtreleri Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
