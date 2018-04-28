---
title: UriTemplate ve UriTemplateTable
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b0fedb812cee5cfa1e4c2ff921a78beb2a6c1beb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable
Web geliştiricileri şekli ve kendi Hizmetleri yanıt URI düzeni tanımlamak için gerektirir. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Geliştiriciler kendi URI'ler üzerinde denetime iki yeni sınıflar eklendi. <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI tabanlı gönderme altyapısında temelini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu sınıfların de kendi izin geliştiricilere şablonları ve URI eşleme mekanizması uygulamadan yararlanmak için kullanılabilir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
## <a name="templates"></a>Şablonlar  
 Bir şablon göreli URI'ler kümesini tanımlamak için bir yoldur. Aşağıdaki tabloda URI şablonları kümesini çeşitli hava durumu bilgi türlerini alır. bir sistem nasıl tanımlanabilir gösterir.  
  
|Veri|Şablon|  
|----------|--------------|  
|Ulusal tahmin|hava durumu/Ulusal|  
|Durum tahmin|hava durumu / {state}|  
|Şehir tahmin|hava durumu / {state} / {Şehir}|  
|Etkinlik tahmin|hava durumu / {state} / {Şehir} / {etkinliği}|  
  
 Bu tablo bir yapısal olarak benzer URI'ler açıklar. Her girişin bir URI şablonudur. Süslü ayraçlar segmentlerinde değişkenleri tanımlayın. Süslü ayraçlar içinde değil kesimleri değişmez değer dizeleri açıklanmaktadır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Şablon sınıfları, örneğin, "/ hava durumu/wa/seattle/dönüşüm", bir gelen URI alıp, açıklayan bir şablona eşleşen bir geliştirici izin ver "/weather/ {state} / {Şehir} / {etkinlik}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> bir URI şablonu kapsülleyen bir sınıftır. Oluşturucusu şablon tanımlayan bir dize parametresi alan. Bu dize sonraki bölümde açıklanan biçimde şablonu içerir. <xref:System.UriTemplate> Sınıfı sağlar izin yöntemleri eşleşen bir şablon için gelen bir URI, bir şablondan bir URI oluşturmayı, şablonda kullanılan değişken adları topluluğu almak, iki şablonları eşdeğerdir ve şablonun dönüş olup olmadığını belirler dize.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> taban adresi ve bir aday URI ve şablona URI'si eşleştirmeyi dener alır. Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örneği döndürülür. <xref:System.UriTemplateMatch> Nesnesini içeren temel bir URI, URI sorgu parametreleri, göreli yol kesimleri dizisi, bir ad/değer koleksiyonu eşleştirildiklerinden, değişkenlerin ad/değer koleksiyonu adayı <xref:System.UriTemplate> eşleştirme gerçekleştirmek için kullanılan örneği , URI (şablon bir joker karakter olduğunda kullanılır) adayı eşleşmeyen herhangi bir bölümünü içeren bir dize ve şablonuyla ilişkili bir nesne.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Sınıfı bir şablona URI'si aday eşleştirirken düzeni ve bağlantı noktası numarası yok sayar.  
  
 Bir şablondan bir URI oluşturmayı sağlayan iki yöntem vardır <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> Temel adres ve parametreleri ad/değer koleksiyonunu alır. Şablon bağlandığında bu parametreler için değişkenleri yerine kullanılır. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> ad/değer çiftlerini alır ve bunları soldan sağa değiştirir.  
  
 <xref:System.UriTemplate.ToString> Şablon dizesini döndürür.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Özellik adları şablon dizesinde yol kesimleri içinde kullanılan değişkenlerinin koleksiyonunu içerir.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> alan bir <xref:System.UriTemplate> bir parametre olarak ve iki şablonları eşdeğer olup olmadığını belirten bir Boole değeri döndürür. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde şablon eşdeğer bölümüne bakın.  
  
 <xref:System.UriTemplate> HTTP URI dilbilgisi uyan herhangi bir URI şeması ile çalışmak üzere tasarlanmıştır. Desteklenen URI şemaları örnekleri verilmiştir.  
  
-   http://  
  
-   https://  
  
-   net.tcp://  
  
-   net.pipe://  
  
-   SB: / /  
  
 Düzenleri gibi file:// ve urn: / / değil HTTP URI dilbilgisi uygun ve URI şablonları ile kullanıldığında öngörülemeyen sonuçlara neden.  
  
### <a name="template-string-syntax"></a>Şablon dizesi söz dizimi  
 Bir şablon üç bölümden oluşur: bir yolu, isteğe bağlı bir sorgu ve isteğe bağlı bir parçası. Örneğin, aşağıdaki şablonu bakın:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Yolun oluşan "/weather/ {state} / {Şehir}", sorgu oluşan"? Tahmin = {uzunluk} ve"#frag1"parça oluşur.  
  
 Baştaki ve sondaki eğik çizgi yol ifadesinde isteğe bağlıdır. Sorgu ve parça ifadeleri tamamen atlanabilir. Bir yol kesimleri tarafından ayrılmış bir dizi oluşur '/', her segmentinde bir hazır değer, ({süslü ayraçlar içinde} yazılmış) bir değişken adı ya da bir joker karakter içerebilir (yazılmış olarak\*'). Önceki şablondaki "\weather\ kesimi ise bir hazır değer değeri"{durumu}"ve"{Şehir}"olan değişkenler. Değişkenleri alabilir, süslü ayraçlar içeriğini kendi adından ve oluşturmak için somut bir değer daha sonra değiştirilebilir bir *URI kapalı*. Joker karakter isteğe bağlıdır, ancak yalnızca, mantıksal olarak "yolu rest" eşleştiği URI, sonunda yer alabilir.  
  
 Sorgu ifadesi varsa, sırasız ad/değer çiftleri tarafından ayrılmış bir dizi belirtir '&'. Sorgu ifadesi öğeleri ya da değişmez değer çiftleri olacak (x = 2) veya bir değişken çifti (x = {var}). Sorguyu yalnızca sağ tarafındaki değişken bir ifade olabilir. ({birad} = {someValue} izin verilmez. Değerleri eşlenmemiş (? x) izin verilmez. Boş sorgu ifadesi ve yalnızca bir tek oluşan bir sorgu ifadesi arasında fark yoktur '?' (her ikisi de "herhangi bir sorgu" anlamına gelir).  
  
 Parça ifadesi değişmez değer oluşabilir, değişken izin verilir.  
  
 Tüm şablon değişken adları şablon dize içinde benzersiz olmalıdır. Şablon değişkeni adları büyük/küçük harfe duyarsızdır.  
  
 Geçerli şablon dizesi örnekleri:  
  
-   ""  
  
-   "/ ayakkabı"  
  
-   "/ ayakkabı / *"  
  
-   "{ayakkabı} / bot"  
  
-   "{ayakkabı} / {{quilt} /bed/ bot}"  
  
-   "ayakkabı / {bot}"  
  
-   "ayakkabı / {bot} / *"  
  
-   "ayakkabı/bot? x 2 ="  
  
-   "ayakkabı / {bot}? x = {yatak}"  
  
-   "ayakkabı / {bot}? = {yatak} & y x bant ="  
  
-   "? x = {ayakkabı}"  
  
-   "ayakkabı? x 3 & y = {var} =  
  
 Geçersiz şablon dizesi örnekleri:  
  
-   "{ayakkabı} / {AYAKKABI} / x 2 =" – Yinelenen değişken adları.  
  
-   "{ayakkabı} /boat/? yatak {ayakkabı} =" – Yinelenen değişken adları.  
  
-   "? x = 2 & x 3 =" – değişmez değerleri olsalar bile, ad/değer çiftleri bir sorgu dizesi içinde benzersiz olmalıdır.  
  
-   "? x 2 = &" – sorgu dizesi hatalı biçimlendirilmiş.  
  
-   "? 2 & x = {ayakkabı}" – sorgu dizesi, ad/değer çiftleri olmalıdır.  
  
-   "? y = 2 & & X = 3" – sorgu dizesi ad değer çifti olmalıdır, adları ile başlatamıyor '&'.  
  
### <a name="compound-path-segments"></a>Yol kesimleri bileşik  
 Bileşik yol kesimleri değişmez değerler ile birleştirilmiş değişkenlerinin yanı sıra birden çok değişkenleri içerecek şekilde tek bir URI yol kesimi izin verir. Geçerli bileşik yol kesimleri örnekleri verilmiştir.  
  
-   /filename. {ext} /  
  
-   /{filename}.jpg/  
  
-   / {filename}. {ext} /  
  
-   / {a}. {b}someLiteral{c}({d}) /  
  
 Geçersiz bir yol kesimleri örnekleri verilmiştir.  
  
-   /{} -Değişkenleri adlı.  
  
-   / {ayakkabı} {bot} - değişkenleri bir hazır değer ile ayrılmalıdır.  
  
### <a name="matching-and-compound-path-segments"></a>Eşleşen ve bileşik yol kesimleri  
 Bileşik yol kesimleri, tek bir yol kesimi içinde birden çok değişkenleri olan bir UriTemplate tanımlamanıza olanak sağlar. Örneğin, aşağıdaki şablonu dizesinde: "adresleri / {state}. {Şehir} "(durumu ve şehir) iki değişken aynı kesim içinde tanımlanmıştır. Bu şablon bir URL gibi eşleşir "http://example.com/Washington.Redmond"ancak bir URL gibi eşleşir"http://example.com/Washington.Redmond.Microsoft". İkinci durumda, "Washington" durumu değişkenini içerir ve şehir değişkeni "Redmond.Microsoft" içerir. Bu durumda herhangi bir metin (dışında '/') {Şehir} değişkeni ile eşleşir. "Ek" metin eşleşmez bir şablon istiyorsanız, değişkeni ayrı bir şablon kesimdeki örneğin koyun: "adresleri / {state} / {şehir}.  
  
### <a name="named-wildcard-segments"></a>Adlandırılmış joker parçaları  
 Değişken adı joker karakteriyle başlayan yol değişken kesimi adlandırılmış joker kesimi ise ' *'. Aşağıdaki şablonu dizesi "ayakkabı" adlı bir adlandırılmış joker karakter kesiminin içerir.  
  
```  
"literal/{*shoe}"  
```  
  
 Joker karakter kesimleri aşağıdaki kurallara uymalıdır:  
  
-   Olabilir en çok her şablon dize için bir adlandırılmış joker kesim.  
  
-   Bir adlandırılmış joker karakter kesiminin yolu en sağdaki kesimdeki adresindeki görünmesi gerekir.  
  
-   Bir adlandırılmış joker karakter kesiminin aynı şablonu dizesi anonim joker Segmentte ile birlikte çalışamaz.  
  
-   Bir adlandırılmış joker karakter kesiminin adı benzersiz olmalıdır.  
  
-   Joker karakter adlı kesimleri varsayılan değerlere sahip olamaz.  
  
-   Adlandırılmış joker kesimleri ile bitemez "/".  
  
### <a name="default-variable-values"></a>Varsayılan değişken değerleri  
 Değişken değerleri varsayılan bir şablon içindeki değişkenleri için varsayılan değerleri belirtmenizi sağlar. Bir koleksiyon veya değişkeni bildirme süslü ayraçlar olan varsayılan değişkenlerini belirtilebilir UriTemplate oluşturucuya geçirilen. Aşağıdaki şablonu belirtmek için iki yolunu gösterir bir <xref:System.UriTemplate> varsayılan değerlerle değişkenleriyle.  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Bu şablon adlı bir değişken bildiren `a` varsayılan değerini `1` ve adlı bir değişkende `b` varsayılan değerini `5`.  
  
> [!NOTE]
>  Yalnızca yol kesimi değişkenleri varsayılan değerlere sahip olmasına izin verilir. Sorgu dizesi değişkenlerinin, bileşik kesim değişkenleri ve adlandırılmış joker değişkenleri varsayılan değerlere sahip izin verilmez.  
  
 Aşağıdaki kod bir aday URI eşleştirirken varsayılan değişken değerleri nasıl işleneceğini gösterir.  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  Bir URI gibi http://localhost:8000/// önceki kod, ancak listelenen şablon eşleşmiyor gibi bir URI http://localhost:8000/ yapar.  
  
 Aşağıdaki kod, bir URI ile bir şablon oluştururken, varsayılan değişken değerleri nasıl işleneceğini gösterir.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 Bir değişken varsayılan değerini verilen zaman `null` ek bazı kısıtlamalar vardır. Varsayılan değer olarak bir değişken olabilir `null` değişkeni şablonu dizesi sağ çoğu kesim içinde yer alıyorsa veya kesim sağındaki tüm parçaları varsayılan değerleri, varsa `null`. Geçerli şablon dizelerdir varsayılan değerlerle aşağıdaki `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 Aşağıdaki varsayılan değerlerle geçersiz şablon dizelerdir `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>Varsayılan değerler ve eşleştirme  
 Aday URI varsayılan değerlerine sahip bir şablon ile eşleştirme yapılırken varsayılan değerleri yerleştirilir <xref:System.UriTemplateMatch.BoundVariables%2A> değerleri adayı URI belirtilmezse koleksiyonu.  
  
### <a name="template-equivalence"></a>Şablon eşdeğer  
 İki şablonları olmasını denirse *yapısal olarak eşdeğer* zaman tüm şablonları değişmez değerleri eşleşmesi ve aynı segmentlerinde değişkenleriniz. Örneğin aşağıdaki şablonlardan yapısal olarak eşdeğerdir:  
  
-   /b b /a/ {var1} / {var2}? x = 1 & y = 2  
  
-   a/{x}/b%20b/{var1}?y=2&x=1  
  
-   a/{y}/B%20B/{z}/?y=2 & x = 1  
  
 Fark edilecek bazı noktalar:  
  
-   Bir şablon başında bir eğik çizgi varsa, yalnızca ilk dizine göz ardı edilir.  
  
-   Yapısal eşdeğer şablon dizeleri karşılaştırma, çalışması için değişken adları yok sayılır ve yol kesimleri, sorgu dizeleri büyük/küçük harfe duyarlıdır.  
  
-   Sorgu dizeleri sırasız.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Sınıfı temsil eden bir ilişkilendirilebilir tablosu <xref:System.UriTemplate> bağlı nesneleri nesneyi geliştiricinin seçme. A <xref:System.UriTemplateTable> en az birini içermelidir <xref:System.UriTemplate> çağrılmadan önce <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. İçeriği bir <xref:System.UriTemplateTable> kadar değiştirilebilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> olarak adlandırılır. Doğrulama gerçekleştirilir zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> olarak adlandırılır. Değerin doğrulaması türüne bağlıdır `allowMultiple` parametresi <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `false`, <xref:System.UriTemplateTable> tablosunda hiçbir şablon olduğundan emin olmak için denetler. Bu yapısal olarak eşdeğer şablonlardan bulunursa, bir özel durum oluşturur. Bu ile birlikte kullanılır <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> yalnızca tek bir şablonda sağlamak istediğinizde bir gelen URI ile eşleşir.  
  
 Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `true`, <xref:System.UriTemplateTable> birden çok, yapısal olarak eşdeğer şablonları içerilmesini bir <xref:System.UriTemplateTable>.  
  
 Bir dizi <xref:System.UriTemplate> eklenen nesneleri bir <xref:System.UriTemplateTable> bunlar olmamalıdır belirsiz sorgu dizeleri içerir. Aynı sorgu dizelerine izin verilir.  
  
> [!NOTE]
>  Sırada <xref:System.UriTemplateTable> temel adresleri, kullanım düzenleri HTTP, düzeni dışındaki ve bağlantı noktası numarası yok sayılır adayı URI'ler şablonlarına eşleştirirken sağlar.  
  
### <a name="query-string-ambiguity"></a>Sorgu dizesi belirsizlik  
 Birden fazla şablon eşleşen bir URI ise paylaşımına eşdeğer bir yol şablonları belirsiz sorgu dizeleri içerir.  
  
 Aşağıdaki sorgu dizeleri kendilerini içinde anlaşılır şunlardır:  
  
-   ?x=1  
  
-   ?x=2  
  
-   ?x=3  
  
-   ? x = 1 & y = {var}  
  
-   ?x=2&z={var}  
  
-   ?x=3  
  
-   ?x=1  
  
-   ?  
  
-   ? x={var}  
  
-   ?  
  
-   ? m = get & c = rss  
  
-   ? m = put & c = rss  
  
-   ? m = get & c atom =  
  
-   ? m put & c = atom =  
  
 Aşağıdaki sorgu dizesi şablonları kendilerini içinde belirsiz şunlardır:  
  
-   ?x=1  
  
-   ?x={var}  
  
 "x 1 ="-iki şablonları ile eşleşir.  
  
-   ?x=1  
  
-   ? y = 2  
  
 "x 1 & y = 2 =" her iki şablonları ile eşleşir. Eşleşen şablonu sonra daha fazla sorgu dizesi değişkenlerinin bir sorgu dizesi içerebilir olmasıdır.  
  
-   ?x=1  
  
-   ? x = 1 & y = {var}  
  
 "x 1 & y = 3 =" her iki şablonları ile eşleşir.  
  
-   ? x 3 & y = 4 =  
  
-   ?x=3&z=5  
  
> [!NOTE]
>  Karakter á ve Á bir URI yolu bir parçası olarak görüntülendiğinde farklı karakter olduğu kabul edilir veya <xref:System.UriTemplate> yol kesimi değişmez değer (ancak karakterler a ve A aynı olduğu varsayılır). Karakter á ve Á bir parçası olarak görüntülendiğinde aynı karakterler olduğu kabul edilir <xref:System.UriTemplate> {variableName} veya bir sorgu dizesi (ve a ve bir de değerlendirilir aynı karakter olmalı).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [UriTemplate Tablosu](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate Tablosu Dağıtıcısı](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
