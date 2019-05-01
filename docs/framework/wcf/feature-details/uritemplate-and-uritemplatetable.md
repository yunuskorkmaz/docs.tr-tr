---
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918638"
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable
Web geliştiricileri şekil ve hizmetlerini yanıt bir URI'leri düzenini açıklayan olanağına sahip olmalıdır. Windows Communication Foundation (WCF), geliştiricilerin kendi bir URI'leri denetiminin kendilerinde olmasına iki yeni sınıflar eklendi. <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI tabanlı dağıtım altyapısı WCF'de temelini oluşturur. Bu sınıflar, bir WCF Hizmeti uygulamadan kendi şablonlarını ve URI yararlanmak geliştiricilerin eşleme mekanizmasını de kullanılabilir.  
  
## <a name="templates"></a>Şablonlar  
 Şablon, göreli bir URI'leri bir kümesini tanımlamak için kullanılan bir yoldur. Dizi URI şablonu aşağıdaki tabloda yer alan çeşitli türlerde hava durumu bilgileri sistem nasıl tanımlanabilir gösterir.  
  
|Veri|Şablon|  
|----------|--------------|  
|Ulusal tahmin|hava durumu/Ulusal|  
|Durum tahmin|hava durumu / {state}|  
|Şehir tahmin|hava durumu / {state} / {Şehir}|  
|Etkinlik tahmin|hava durumu / {state} / {Şehir} / {etkinliği}|  
  
 Bu tablo, yapısal olarak benzer bir URI'leri kümesini açıklar. Her girişin bir URI Şablonu ' dir. Küme ayracı segmentler değişkenleri tanımlayın. Segment kaşlı ayraçlar içinde değil, değişmez değer dizeleri açıklar. WCF şablon sınıfları, örneğin, "/ hava durumu/wa/seattle/dönüşüm", gelen bir URI olması ve onu tanımlayan bir şablon eşleştirmek bir geliştirici izin ver "/weather/ {state} / {Şehir} / {etkinlik}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> bir URI şablonu kapsülleyen bir sınıftır. Oluşturucusu şablon tanımlayan bir dize parametresi alır. Bu dize sonraki bölümde açıklanan biçimde şablonu içerir. <xref:System.UriTemplate> SAX olanak sağlayan yöntemleri eşleşen bir şablon için gelen bir URI, bir şablondan bir URI oluşturmayı, değişken adı şablonda kullanılan koleksiyonu alma, iki şablonu eşdeğerdir ve şablonun dönüş olup olmadığını belirlemek dize.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> Temel adres ve bir aday URI ve şablon URI'si eşleşmeyi dener alır. Eşleşmenin başarılı olması durumunda bir <xref:System.UriTemplateMatch> örneği döndürülür. <xref:System.UriTemplateMatch> Nesnesini içeren temel bir URI, URI sorgu parametreleri, bir dizi göreli yol parçalarının, eşleştirilmiş olan değişkenler ad/değer koleksiyonu ad/değer koleksiyonunu aday <xref:System.UriTemplate> eşleştirme uygulamak için kullanılan örneği , URI (şablon bir joker karakter varsa kullanılır) aday eşleşmeyen herhangi bir bölümünü içeren bir dize ve şablonu ile ilişkili bir nesne.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Sınıfı bir şablon için bir aday URI eşleştirirken düzenini ve bağlantı noktası numarası yok sayar.  
  
 Bir şablondan bir URI oluşturmayı sağlayan iki farklı yöntemle <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> Temel adres ve parametrelerin ad/değer koleksiyonunu alır. Şablon bağlandığında bu parametreler için değişkenleri yerine kullanılır. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> ad/değer çiftlerini alır ve bunları soldan sağa yerini alır.  
  
 <xref:System.UriTemplate.ToString> Şablon dizeyi döndürür.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Özelliği, şablonu dizedeki yol kesimleri içinde kullanılan değişkenlerin adlarını koleksiyonunu içerir.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> alan bir <xref:System.UriTemplate> bir parametre olarak ve iki şablon eşdeğer olup olmadığını belirten bir Boole değeri döndürür. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde şablon denkliği bölümüne bakın.  
  
 <xref:System.UriTemplate> HTTP URI dilbilgisi uyan herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır. Desteklenen URI düzenleri örnekleri aşağıda verilmiştir.  
  
- http://  
  
- https://  
  
- net.tcp://  
  
- net.pipe://  
  
- sb://  
  
 Düzenleri gibi file:// ve urn: / / değil HTTP URI dilbilgisi uygun ve URI şablonları ile kullanıldığında öngörülemeyen sonuçlara neden.  
  
### <a name="template-string-syntax"></a>Şablon dizesi söz dizimi  
 Bir şablon üç bölümden oluşur: bir yol, isteğe bağlı bir sorgu ve isteğe bağlı bir parçası. Örneğin, aşağıdaki şablonu bakın:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Yolun oluşan "/weather/ {state} / {Şehir}", sorgu oluşan"? tahmini {length} ="#frag1"parça oluşur.  
  
 Baştaki ve sondaki eğik çizgi yolu ifade isteğe bağlıdır. Sorgu ve parça ifadeler tamamen atlanabilir. Segment tarafından ayrılmış bir dizi yol oluşan '/', her bir kesim değişmez değer, bir değişken adı ({küme ayraçları içine} yazılmış) veya bir joker karakter olabilir (yazılmış olarak\*'). Önceki şablonda "\weather\ segmenttir bir değişmez değer"{state}"ve"{city}"olan değişkenler. Değişkenleri alabilir, küme ayracı içeriğini kendi adından ve oluşturmak için somut bir değer daha sonra değiştirilebilir bir *URI kapalı*. Joker karakter isteğe bağlıdır, ancak yalnızca burada "yolun rest" mantıksal olarak eşleşen bir URI sonunda görünebilir.  
  
 Sırasız ad/değer çiftleri tarafından ayrılmış bir dizi varsa, sorgu ifadesi belirtir '&'. Sorgu ifadesinin öğeleri değişmez değer çifti olabilir (x = 2) veya bir değişken çifti (x = {var}). Sorgu yalnızca sağ tarafında bir değişken bir ifadeye sahip olabilir. ({birad} = {in değeri Birdeğer} izin verilmiyor. Değerleri bitiştirilen (? x) izin verilmez. Boş sorgu ifadesi yalnızca bir tek oluşan bir sorgu ifadesi arasındaki fark yoktur '?' (her ikisi de "herhangi bir sorgu" anlamına gelir).  
  
 Parça ifadesi değişmez değer oluşabilir, değişken izin verilir.  
  
 Bir şablon dize içindeki tüm şablon değişken adları benzersiz olmalıdır. Şablon değişkeni adları büyük/küçük harfe duyarsızdır.  
  
 Geçerli şablon dizeleri örnekleri:  
  
- ""  
  
- "/shoe"  
  
- "/shoe/\*"  
  
- "{ayakkabı} / bot"  
  
- "{ayakkabı} / {{quilt} /bed/ bot}"  
  
- "ayakkabı / {bot}"  
  
- "ayakkabı / {bot} /\*"  
  
- "shoe/boat?x=2"  
  
- "shoe/{boat}?x={bed}"  
  
- "ayakkabı / {bot}? = {yatak} & y x bant ="  
  
- "?x={shoe}"  
  
- "shoe?x=3&y={var}  
  
 Geçersiz şablon dizeleri örnekleri:  
  
- "{ayakkabı} / {AYAKKABI} / x 2 =" – Yinelenen değişken adları.  
  
- "{ayakkabı} /boat/? yatak {ayakkabı} =" – Yinelenen değişken adları.  
  
- "? x = 2 & x 3 =" – değişmez değerleri olsalar bile bir sorgu dizesi içinde ad/değer çiftleri benzersiz olmalıdır.  
  
- "? x 2 = &" – sorgu dizesi yanlış biçimlendirilmiş.  
  
- "? 2 & x = {ayakkabı}" – ad/değer çiftleri sorgu dizesi olması gerekir.  
  
- "? y = 2 & & X = 3" – adları ile başlayamaz, sorgu dizesi olmalıdır ad değer çiftleri '&'.  
  
### <a name="compound-path-segments"></a>Bileşik yol kesimleri  
 Bileşik yol kesimleri değişmez değerler ile birleştirilmiş değişkenleri yanı sıra birden çok değişkenleri içerecek şekilde tek bir URI yol kesimi izin verir. Geçerli bir bileşik yol kesimleri örnekleri aşağıda verilmiştir.  
  
- /filename. {ext} /  
  
- /{filename}.jpg/  
  
- / {filename}. {ext} /  
  
- / {bir}. {b}someLiteral{c}({d}) /  
  
 Geçersiz yol kesimleri örnekleri aşağıda verilmiştir.  
  
- /{} -Değişkenler adlandırılmış.  
  
- / {ayakkabı} {bot} - değişkenleri, bir sabit değer ayrılmalıdır.  
  
### <a name="matching-and-compound-path-segments"></a>Eşleşen ve bileşik yol kesimleri  
 Bileşik yol kesimleri tek bir yol kesimi içinde birden fazla değişken olan UriTemplate tanımlamanızı sağlar. Örneğin, aşağıdaki şablonu dizesi: "Adresleri / {state}. {Şehir} "(durumu ve şehir) iki değişken aynı kesim içinde tanımlanır. Bu şablon bir URL gibi BC `http://example.com/Washington.Redmond` ancak gibi bir URL eşleşecektir `http://example.com/Washington.Redmond.Microsoft`. İkinci durumda, "Washington" durumu değişkenini içerir ve "Redmond.Microsoft" Şehir değişkeni içerir. Bu durumda herhangi bir metin (dışında '/') {Şehir} değişkeni eşleşir. "Ek" metin eşleşmeyeceği bir şablon istiyorsanız, değişken içinde ayrı bir şablon segment, örneğin yerleştirin: "Adresleri / {state} / {şehir}.  
  
### <a name="named-wildcard-segments"></a>Adlandırılmış bir joker karakter segmentleri  
 Değişken adı joker karakteri ile başlayan yol değişkeni kesimini bir adlandırılmış joker segmenttir '\*'. Aşağıdaki şablonu dizesi "ayakkabı" adlı bir adlandırılmış bir joker karakter segmenti içerir.  
  
```  
"literal/{*shoe}"  
```  
  
 Joker karakter kesimleri, aşağıdaki kurallara uymalıdır:  
  
- En fazla olabilir her şablon dizesi için bir adlandırılmış bir joker karakter segmenti.  
  
- Bir adlandırılmış bir joker karakter segmenti yolun en sağdaki kesimi sırasında yer almalıdır.  
  
- Bir adlandırılmış bir joker karakter segmenti aynı şablon dize içindeki bir anonim bir joker karakter segmenti ile bir arada bulunamaz.  
  
- Bir adlandırılmış bir joker karakter segmenti adı benzersiz olmalıdır.  
  
- Joker adlı segmentleri varsayılan değerlere sahip olamaz.  
  
- Adlandırılmış bir joker karakter kesimleri ile bitemez "/".  
  
### <a name="default-variable-values"></a>Varsayılan değişken değerleri  
 Değişken değerleri varsayılan şablonu içindeki değişkenleri için varsayılan değerlere belirtmenizi sağlar. Varsayılan değişkenleri değişkenini tanımlamak ve küme ayraçlarının veya bir koleksiyon olarak belirtilebilir UriTemplate oluşturucuya geçirilen. Aşağıdaki şablonu belirlemek için iki yolunu gösterir bir <xref:System.UriTemplate> varsayılan değerlerle değişkenleriyle.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Bu şablon adında bir değişken bildirir `a` varsayılan değerini `1` ve adlı bir değişken `b` varsayılan değerini `5`.  
  
> [!NOTE]
>  Yalnızca yol kesimi değişkenleri varsayılan değerlere sahip izin verilir. Sorgu dizesi değişkenlerinin, bileşik bir segment değişkenleri ve adlandırılmış joker değişkenleri varsayılan değerlere sahip izin verilmez.  
  
 Aşağıdaki kod, bir aday URI eşleştirirken varsayılan değişken değerleri nasıl işleneceğini gösterir.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> Bir URI gibi `http://localhost:8000///` önceki kodda, ancak listelenen şablonu eşleşmiyor gibi bir URI `http://localhost:8000/` yapar.  
  
 Aşağıdaki kod, bir URI ile bir şablon oluştururken varsayılan değişken değerleri nasıl işleneceğini gösterir.  
  
```csharp
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
  
Ne zaman bir değişkeni verilir varsayılan değerini `null` bazı ek kısıtlamalar vardır. Bir değişken varsayılan değerine sahip olabilir `null` değişken şablon dizesi doğru çoğu Segmentte içeriyorsa veya segment sağındaki tüm parçaları varsayılan değerleri varsa `null`. Varsayılan değerleri ile geçerli şablon dizeleri şunlardır `null`:  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Varsayılan değerler ile geçersiz şablon dizeleri şunlardır `null`:  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Varsayılan değerleri ve eşleştirme  
 Bir aday URI varsayılan değerlere sahip bir şablon ile eşleştirme yapılırken varsayılan değerleri yerleştirilir <xref:System.UriTemplateMatch.BoundVariables%2A> değerleri adayı URI'nda belirtilmezse koleksiyonu.  
  
### <a name="template-equivalence"></a>Şablon eşdeğerlik  
 İki şablon söylediğiniz olmasını *yapısal olarak eşdeğer* aynı segmentler değişkenleriniz ve ne zaman tüm şablonları değişmez değerleri eşleşmiyor. Örneğin aşağıdaki şablonlardan yapısal olarak eşdeğerdir:  
  
- /b b /a/ {var1} / {var2}? x = 1 & y = 2  
  
- a/{x}/b%20b/{var1}?y=2&x=1  
  
- a/{y}/B%20B/{z}/?y=2&x=1  
  
 Fark gereken bazı noktalar:  
  
- Bir şablon önde gelen eğik çizgiler içeriyorsa, yalnızca ilki göz ardı edilir.  
  
- Yapısal denklik için şablon dizeleri karşılaştırırken çalışması için değişken adları yok sayılır ve yol kesimleri, sorgu dizeleri büyük/küçük harfe duyarlıdır.  
  
- Sorgu dizeleri, sırasız.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Sınıfı temsil eder, ilişkili bir tablosu <xref:System.UriTemplate> bağlı olan nesneleri geliştirici bir nesne seçme. A <xref:System.UriTemplateTable> en az bir içeren <xref:System.UriTemplate> çağrılmadan önce <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. İçeriği bir <xref:System.UriTemplateTable> kadar değiştirilebilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılır. Doğrulama işlemi gerçekleştirildiğinde, <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılır. Değerin doğrulaması türüne bağlıdır `allowMultiple` parametresi <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `false`, <xref:System.UriTemplateTable> denetler tablosunda hiçbir şablon olmadığından emin olun. Bu yapısal olarak eşdeğer herhangi bir şablon bulunursa, bir özel durum oluşturur. Bu ile birlikte kullanılan <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> yalnızca tek bir şablonda sağlamak istediğinizde bir gelen URI ile eşleşir.  
  
 Zaman <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> tümleştirilmesidir adlı `true`, <xref:System.UriTemplateTable> birden çok, yapısal olarak eşdeğer şablonlarını kapsamında yer alan bir <xref:System.UriTemplateTable>.  
  
 Bir dizi <xref:System.UriTemplate> eklenen nesneleri bir <xref:System.UriTemplateTable> bunlar olmamalıdır belirsiz sorgu dizelerini içerir. Aynı sorgu dizelerine izin verilir.  
  
> [!NOTE]
>  Sırada <xref:System.UriTemplateTable> temel adreslerinin dışındaki HTTP düzenini, kullanım düzenleri ve bağlantı noktası numarası yok sayılır şablonları için aday URI'ler eşleştirirken sağlar.  
  
### <a name="query-string-ambiguity"></a>Sorgu dizesi belirsizlik  
 Birden fazla şablon eşleşen bir URI ise paylaşımına eşdeğer bir yol şablonları belirsiz sorgu dizelerini içerir.  
  
 Sorgu dizeleri aşağıdaki kümesi içinde kendilerini durumdaysalar:  
  
- ?x=1  
  
- ?x=2  
  
- ?x=3  
  
- ?x=1&y={var}  
  
- ?x=2&z={var}  
  
- ?x=3  
  
- ?x=1  
  
- ?  
  
- ? x={var}  
  
- ?  
  
- ? m = get & c rss =  
  
- ? m = put & c rss =  
  
- ? m = get & c atom =  
  
- ? m = put & c atom =  
  
 Aşağıdaki sorgu dizesi şablonları kümesi içinde kendilerini belirsizdir:  
  
- ?x=1  
  
- ?x={var}  
  
 "x = 1"-iki şablon eşleşir.  
  
- ?x=1  
  
- ? y = 2  
  
 "x = 1 & y = 2" iki şablon eşleşir. Şablon ile eşleşen sonra daha fazla sorgu dizesi değişkenlerinin bir sorgu dizesi içerebilir olmasıdır.  
  
- ?x=1  
  
- ?x=1&y={var}  
  
 "x = 1 & y 3 =" iki şablon eşleşir.  
  
- ?x=3&y=4  
  
- ?x=3&z=5  
  
> [!NOTE]
> Karakter á ve Á bir URI yolu bir parçası olarak görünürler, farklı karakterler olarak değerlendirilir veya <xref:System.UriTemplate> yol kesimi değişmez değer (ancak karakterler a ve A ile aynı olarak kabul edilir). Karakter á ve Á bir parçası olarak görünürler, aynı karakterler olarak değerlendirilir <xref:System.UriTemplate> {variableName} ya da bir sorgu dizesi (ve a ve bir de kabul edilir aynı karakterler olabilir).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [UriTemplate Tablosu](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate Tablosu Dağıtıcısı](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
