---
title: .NET XAML Hizmetleri için XAML İsim Boşlukları
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071845"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>.NET XAML Hizmetleri için XAML İsim Boşlukları
XAML ad alanı, XML ad alanının tanımını genişleten bir kavramdır. XML ad alanına benzer şekilde, biçimlendirmede bir `xmlns` öznitelik kullanarak bir XAML ad alanı tanımlayabilirsiniz. XAML ad alanları, XAML düğüm akışında ve diğer XAML Hizmetleri API'lerinde de temsil edilir. Bu konu XAML ad alanı kavramını tanımlar ve XAML ad alanlarının nasıl tanımlanabileceğini ve XAML şema bağlamları ve .NET XAML Hizmetlerinin diğer yönleri tarafından nasıl kullanıldığını açıklar.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML Ad Alanı ve XAML Ad Alanı  
 XAML ad alanı, XAML'nin XML'nin özel bir biçimi olması ve biçimlendirmesi için temel XML formunu kullanması gibi, özel leştirilmiş bir XML ad alanıdır. Biçimlendirmede, bir öğeye uygulanan bir `xmlns` öznitelik aracılığıyla bir XAML ad alanı ve eşleçleme bildirirsiniz. Bildirim, `xmlns` XAML ad alanının beyan edildiği aynı öğeye yapılabilir. Bir öğeye yapılan bir XAML ad alanı bildirimi, söz öğenin tüm öznitelikleri ve bu öğenin tüm alt ları için geçerlidir. Öznitelik öznitelik özniteliği içeren öğe ile aynı olmayan bir XAML ad alanı kullanabilirsiniz, öznitelik adı kendisi işaretleme onun öznitelik adının bir parçası olarak önek başvurur sürece.  
  
 XAML ad alanı ile XML ad alanı ayrımı, bir XML ad alanının bir şemaya başvurmak veya yalnızca varlıkları ayırt etmek için kullanılabilmesidir. XAML için, XAML'de kullanılan tür ve üyeler sonuçta destek türlerine göre çözülmelidir ve XML şeması kavramları bu kapasiteye iyi uygulanmaz. XAML ad alanı, bu tür eşleme gerçekleştirmek için XAML şema bağlamı nın bulunması gereken bilgileri içerir.  
  
## <a name="xaml-namespace-components"></a>XAML İsim Alanı Bileşenleri  
 XAML ad alanı tanımının iki bileşeni vardır: bir önek ve tanımlayıcı. Bu bileşenlerin her biri, bir XAML ad alanı biçimlendirmede bildirildiğinde veya XAML türü sisteminde tanımlandığında bulunur.  
  
 [Önek, XML 1.0 belirtiminde W3C Ad Alanları](https://www.w3.org/TR/REC-xml-names/)tarafından izin verilen herhangi bir dize olabilir. Önek, tipik bir biçimlendirme dosyasında birçok kez yineleninden, önekler genellikle kısa dizeleri dir. Birden çok XAML uygulamalarında kullanılmak üzere tasarlanan belirli XAML ad alanları belirli geleneksel önekleri kullanır. Örneğin, XAML dili XAML ad alanı genellikle önek `x`kullanılarak eşlenir. Önek tanımda verilmez ancak XAML Hizmetleri API'by.NET tanımlanmış veya sorgulanırsa boş bir dize olarak temsil edilen varsayılan bir XAML ad alanı tanımlayabilirsiniz. Genellikle, varsayılan XAML ad alanı, xaml uygulayan bir teknoloji ve onun senaryoları ve kelime leri tarafından en üst düzeye çıkarılan bir türek atlayış biçimlendirmesini tanıtmak için kasıtlı olarak seçilir.  
  
 Tanımlayıcı, [XML 1.0 belirtiminde W3C Namespaces](https://www.w3.org/TR/REC-xml-names/)tarafından izin verilen herhangi bir dize olabilir. Kural olarak, XML ad alanları veya XAML ad alanları için tanımlayıcılar genellikle URI formunda, genellikle protokol nitelikli mutlak URI olarak verilir. Genellikle, belirli bir XAML sözcük dağarcığı tanımlayan sürüm bilgileri yol dizesinin bir parçası olarak ima edilir. XAML ad alanları, XML URI kuralının ötesinde ek bir tanımlayıcı kuralı ekler. XAML ad alanları için tanımlayıcı, xaml ad alanı altında öğe olarak belirtilen türleri çözmek veya üyelere öznitelikleri ni çözmek için XAML şeması bağlamı tarafından gereken bilgileri iletir.  
  
 Bilgileri XAML şema bağlamına iletmek amacıyla, XAML ad alanı tanımlayıcısı hala URI formunda olabilir. Ancak, bu durumda URI de belirli bir derleme veya derlemeler listesinde eşleşen bir tanımlayıcı olarak ilan edilir. Bu, derlemeye atfederek montajlarda <xref:System.Windows.Markup.XmlnsDefinitionAttribute>yapılır. XAML ad alanını tanımlama ve atfedilen derlemede CLR tabanlı bir tür çözümleme davranışını destekleme yöntemi,.NET XAML Hizmetleri'ndeki varsayılan XAML şeması bağlamı tarafından desteklenir. Daha genel olarak, bu kural XAML şema bağlamınınCLR'yi dahil ettiği veya CLR derlemelerinden CLR özniteliklerini okumak için gerekli olan varsayılan XAML şema bağlamını temel aldığı durumlar için kullanılabilir.  
  
 XAML ad alanları, clr ad alanı ve tür tanımlayıcı derleme ile iletişim sağlayan bir kuralkuralı yla da tanımlanabilir. Bu kural, türleri içeren <xref:System.Windows.Markup.XmlnsDefinitionAttribute> derlemelerde atıfta bulunulan durumlarda kullanılır. Bu sözleşme uri konvansiyonundan potansiyel olarak daha karmaşıktır ve aynı zamanda bir derlemeye atıfta bulunulmanın birden çok yolu olduğundan belirsizlik ve yineleme potansiyeline de sahiptir.  
  
 CLR ad alanı ve derleme kuralını kullanan bir tanımlayıcının en temel biçimi aşağıdaki gibidir:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`ve `; assembly=` sözdiziminin gerçek bileşenleridir.  
  
 *clrnsName,* CLR ad alanını tanımlayan dize adıdır. Bu dize adı, CLR ad alanı ve diğer CLR ad alanlarıyla ilişkisi hakkında ipuçları sağlayan tüm dahili nokta karakterleri (.) içerir.
  
 *assemblyShortName,* XAML'de yararlı olan türleri tanımlayan bir derlemenin dize adıdır. Bildirilen XAML ad alanı üzerinden erişilecek türlerin derleme tarafından tanımlanması ve *clrnsName*tarafından belirtilen CLR ad alanı içinde bildirilmesi beklenmektedir. Bu dize adı genellikle tarafından <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>bildirilen bilgileri paralellikler.  
  
 CLR ad alanı ve montaj kuralının daha eksiksiz bir tanımı aşağıdaki gibidir:  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *assemblyName,* giriş olarak yasal <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> olan herhangi bir dizeyi temsil eder. Bu dize kültür, ortak anahtar veya sürüm bilgilerini içerebilir (bu kavramların <xref:System.Reflection.Assembly>tanımları başvuru konusuolarak tanımlanır). COFF biçimi ve kanıtı (diğer aşırı <xref:System.Reflection.Assembly.Load%2A>yükler tarafından kullanıldığı gibi) XAML montaj yükleme amaçları için ilgili değildir; tüm yük bilgileri bir dize olarak sunulmalıdır.  
  
 Derleme için ortak anahtar belirtmek XAML güvenliği veya derlemeler basit bir adla yüklendiğinde veya önbellek veya uygulama etki alanında önceden varsa var olabilecek olası belirsizliği gidermek için yararlı bir tekniktir. Daha fazla bilgi için [XAML Güvenlik](security-considerations.md)Hususları'na bakın.  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML Hizmetleri API'sinde XAML Namespace Bildirimleri  
 XAML Hizmetleri API'sinde, XAML ad alanı bildirimi <xref:System.Xaml.NamespaceDeclaration> bir nesne tarafından temsil edilir. Kodda bir XAML ad alanı beyan ediyorsanız, oluşturucuyu <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> çağırırsınız. Ve `ns` `prefix` parametreler dizeleri olarak belirtilir ve bu parametreleri sağlamak için giriş xaml ad alanı tanımlayıcısı ve XAML ad alanı öneki tanımına karşılık gelir bu konuda daha önce sağlanan.  
  
 XAML ad alanı bilgilerini Bir XAML düğüm akışının parçası olarak veya XAML türü <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> sistemine başka erişim yoluyla inceliyorsanız, XAML ad alanı tanımlayıcısını raporlar ve <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> XAML ad alanı önekini raporlar.  
  
 XAML düğümü akışında, XAML ad alanı bilgileri uygulandığı varlıköncesinde bir XAML düğümü olarak görünebilir. Bu, XAML ad alanı `StartObject` bilgilerinin XAML kök öğesinden önce geldiği durumları içerir. Daha fazla bilgi için Bkz. [XAML Düğüm Akışı Yapılarını ve Kavramlarını Anlama.](understanding-xaml-node-stream-structures-and-concepts.md)  
  
 .NET XAML Hizmetleri API'sini kullanan birçok senaryoiçin, en az bir XAML ad alanı bildiriminin bulunması beklenir ve bildirim, XAML şeması bağlamı tarafından gerekli olan bilgileri içermeli veya bu bilgilere atıfta bulunmalıdır. XAML ad alanları, yüklenecek derlemeleri belirtmeli veya XAML şema bağlamı tarafından zaten yüklenmiş veya bilinen ad alanları ve derlemeler içinde belirli türleri çözmeye yardımcı olmalıdır.  
  
 XAML düğümü akışı oluşturmak için XAML yazı bilgisinin XAML şeması bağlamında kullanılabilmesi gerekir. XAML türü bilgileri, oluşturulacak her düğüm için ilgili XAML ad alanı belirlenemez. Bu noktada, henüz tür örnekleri oluşturulmaz, ancak XAML şema bağlamının tanımlayıcı derleme ve destek türünden bilgilere bakması gerekebilir. `<Party><PartyFavor/></Party>`Örneğin, biçimlendirmeyi işlemek için, XAML şema bağlamının adını ve türünü `ContentProperty` `Party`belirleyebilmesi ve böylece XAML ad alanı bilgilerini `Party` bilmesi `PartyFavor`gerekir. Varsayılan XAML şeması bağlamında statik yansıma, düğüm akışında XAML türü düğümleri oluşturmak için gereken XAML türü sistem bilgilerinin çoğunu raporlar.  
  
 XAML düğümü akışından bir nesne grafiği oluşturmak için, özgün biçimlendirmede kullanılan ve XAML düğüm akışında kaydedilen her XAML öneki için XAML ad alanı bildirimleri bulunması gerekir. Bu noktada, örnekler oluşturuluyor ve gerçek tür eşleme davranışı oluşur.  
  
 XAML ad alanı bilgilerini önceden doldurmanız gerekiyorsa, kullanmak istediğiniz XAML ad alanının biçimlendirmede XAML şema bağlamının tanımlanmadığı durumlarda, kullanabileceğiniz tek şey <xref:System.Xml.XmlParserContext> XML <xref:System.Xml.XmlReader>ad alanı bildirimlerini bir . Sonra bir <xref:System.Xml.XmlReader> XAML okuyucu oluşturucu, ya <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>da giriş olarak kullanın.  
  
 .NET XAML Hizmetleri'nde XAML ad alanı işleme sa¤lamakla ilgili di¤er iki API öznitelikleri <xref:System.Windows.Markup.XmlnsDefinitionAttribute> ve <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Bu öznitelikler derlemeler için geçerlidir. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Uri içeren herhangi bir XAML ad alanı bildirimini yorumlamak için xaml şeması bağlamı tarafından kullanılır. <xref:System.Windows.Markup.XmlnsPrefixAttribute>belirli bir XAML ad alanının öngörülebilir bir önek ile serihale edilebilmeleri için XAML yayan araçlar tarafından kullanılır. Daha fazla bilgi için, [Özel Türler ve Kitaplıklar için XAML ile ilgili CLR Öznitelikleri'ne](clr-attributes-with-custom-types-and-libraries.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama](understanding-xaml-node-stream-structures-and-concepts.md)
