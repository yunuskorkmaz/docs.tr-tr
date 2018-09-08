---
title: .NET Framework XAML Hizmetleri İçin XAML Ad Uzayları
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: ac6554cbdeb5bc6e0fe7fb96ea95d0143c293d22
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137466"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML Hizmetleri İçin XAML Ad Uzayları
XAML ad alanı tanımını bir XML ad alanı üzerinde genişleten bir kavramdır. Benzer şekilde bir XML ad alanı, XAML ad alanını kullanarak tanımlayabilirsiniz bir `xmlns` biçimlendirme özniteliği. XAML ad alanları, XAML düğümü akışı ve diğer XAML hizmetler API'lerini de temsil edilir. Bu konu, XAML ad alanı kavramını tanımlar ve XAML ad alanları'nın tanımlanabilir ve XAML şema bağlamları ve .NET Framework XAML hizmetlerinde diğer yönleri tarafından kullanılan nasıl açıklanmaktadır.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML Namespace ve XAML Namespace  
 Yalnızca XAML özel XML biçimi ve temel XML biçimi, biçimlendirme için kullanılıyorsa bir XAML ad alanı özel bir XML ad alanı aynıdır. XAML ad alanı ve kendi eşleme aracılığıyla biçimlendirmesinde, bildirdiğiniz bir `xmlns` bir öğeye uygulanan bir öznitelik. `xmlns` Bildirimi, XAML ad alanı içinde bildirildiği aynı öğeye yapılabilir. Bir öğeye yapılan bir XAML ad alanı bildirimi, bu öğe, bu öğenin tüm öznitelikleri ve bu öğenin tüm alt öğeleri için geçerlidir. Öznitelikleri, öznitelik adı ön eki biçimlendirme öznitelik adında bir parçası olarak başvuruyor. sürece öznitelik içeren öğe ile aynı değil bir XAML ad alanları kullanabilirsiniz.  
  
 XAML ad alanı bir XML ad alanı karşı farkı bir XML ad alanı şema başvurmak için kullanılan veya yalnızca varlık ayırt etmek için kullanılabilir ' dir. XAML, türler ve üyeler XAML içinde kullanılan en sonunda yedekleme türleri için çözülmelidir ve XML Şeması kavramları de bu özellik için geçerli değildir. XAML ad alanı, XAML şema içeriği kullanılabilir bu türü eşleme gerçekleştirmek için sahip olmanız gereken bilgileri içerir.  
  
## <a name="xaml-namespace-components"></a>XAML Namespace bileşenleri  
 XAML ad alanı tanımını iki bileşenden oluşur: bir önek ve bir tanımlayıcı. Bu bileşenlerin her birini bir XAML ad alanı biçimlendirme içinde bildirilen veya XAML türü sistemde mevcut.  
  
 Önek tarafından izin verilen herhangi bir dize olabilir [W3C XML 1.0 belirtimi alanlarında](https://go.microsoft.com/fwlink/?LinkID=161735) . Tipik biçimlendirme dosyasında yinelenen öneki birçok kez olduğundan kural olarak, genellikle çok kısa dizeler ön eklerdir. Birden fazla XAML uygulamalarında kullanılmak üzere tasarlanmıştır belirli XAML ad alanları, belirli geleneksel önekleri kullanın. Örneğin, XAML dili XAML ad alanı genellikle önekini kullanarak eşlenmiş `x`. Burada öneki tanımında verilmedi ancak tanımlı veya by.NET Framework XAML Hizmetleri API sorgulanan boş bir dize temsil edilen bir varsayılan XAML ad tanımlayabilirsiniz. Genellikle, varsayılan XAML ad alanı kasıtlı olarak ön ekini attığınızda ekranı miktarını yükseltmek için seçilen bir XAML uygulama teknoloji ve senaryo ve sözcük dağarcıklarını biçimlendirme.  
  
 Tanımlayıcı tarafından izin verilen herhangi bir dize olabilir [W3C XML 1.0 belirtimi alanlarında](https://go.microsoft.com/fwlink/?LinkID=161735). Kural gereği, XML ad alanları veya XAML ad alanları için tanımlayıcı genellikle URI biçiminde Protokolü nitelenmiş bir mutlak URI olarak genellikle verilir. Genellikle, belirli bir XAML sözlük tanımlar ve sürüm bilgileri yol dizesini bir parçası olarak yapılmamaktadır. XAML ad alanları XML URI kuralının ötesinde bir ek tanımlayıcı kuralı ekleyin. XAML ad alanları için tanımlayıcı XAML şema içeriği tarafından bu XAML ad alanı altında öğeleri olarak belirttiğiniz türlerini çözmek için ya da üye öznitelikleri çözmek için gereken bilgileri iletişim kurar.  
  
 XAML şema içeriği bilgileri iletişim kurmak amacıyla bir XAML ad alanı için olan tanımlayıcıyla hala URI biçiminde olabilir. Ancak, bu durumda URI Ayrıca belirli bir derleme veya derlemelerin listesini eşleşen bir tanımlayıcı olarak bildirilir. Bu derleme ile öznitelik atanıyor tarafından derlemelerde yapılır <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. XAML ad alanı tanımlama ve CLR tabanlı tür çözümleme davranışı öznitelikli derlemesinde desteklemek için bu yöntemi, .NET Framework XAML hizmetlerinde varsayılan XAML şema içeriği tarafından desteklenir. Daha genel olarak, bu kural, XAML şema içeriği burada CLR içerir veya CLR öznitelikleri CLR derlemeleri okumak için gerekli olan varsayılan XAML şema içeriği dayalı çalışması için kullanılabilir.  
  
 XAML ad alanları, bir CLR ad alanı ve türü tanımlayan bir derleme iletişim kuran bir kural olarak da tanımlanabilir. Bu kuralı durumlarda yok burada kullanılan <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attribution var. türlerini içeren derlemeler. Bu kural, URI kuralının büyük olasılıkla daha karmaşıktır ve bir derlemeye başvuran birden çok yolu olduğundan belirsizlik ve çoğaltma olasılığı da vardır.  
  
 CLR ad alanını ve derlemeyi kuralı kullanan bir tanımlayıcının en temel biçimi aşağıdaki gibidir:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` ve `; assembly=` sözdizimini sabit değer bileşenleridir.  
  
 *clrnsName* bir CLR ad alanını tanımlayan dize adı. Bu dize adı CLR ad alanı ve diğer CLR ad alanlarına ilişkisi hakkında ipuçları sağlayın herhangi iç nokta karakteri (.) içerir.  
  
 *assemblyShortName* XAML içinde yararlı olan türlerini tanımlayan bir derlemeye dize adı. Bildirilen XAML ad alanı erişilmesini türleri derlemesi tarafından tanımlanması ve özellikle tarafından belirtilen CLR ad uzayı içinde bildirilmesi için beklenen *clrnsName*. Bu dize adı genellikle tarafından raporlanan bilgileri parallels <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Daha eksiksiz bir CLR ad alanını ve derlemeyi kuralı tanımı aşağıdaki gibidir:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* yasal olarak bir dize temsil eden bir <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> giriş. Bu dize, kültür, ortak anahtarı ve sürüm bilgileri içerebilir (Bu kavramların tanımlarını için başvuru konusu tanımlanmış <xref:System.Reflection.Assembly>). COFF biçimi ve kanıt (diğer aşırı yüklemeleri tarafından kullanılan <xref:System.Reflection.Assembly.Load%2A>) yükleme amacıyla; XAML derlemesi için ilgili olmayan bir dize olarak tüm yük bilgileri sunulmalıdır.  
  
 Derleme için bir ortak anahtar belirterek XAML güvenlik veya derlemeleri basit adıyla yüklenen ya da bir önbellek ya da uygulama etki alanında önceden mevcut olan bulunabilir olası belirsizliğini kaldırmak için kullanışlı bir yöntem var. Daha fazla bilgi için [XAML güvenlik konuları](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML Namespace bildirimlerinde XAML Hizmetleri API'si  
 XAML Services API, bir XAML ad alanı bildirimi tarafından temsil edilen bir <xref:System.Xaml.NamespaceDeclaration> nesne. XAML ad alanında kod bildiriliyorsa, çağrı <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> Oluşturucusu. `ns` Ve `prefix` parametreleri dize olarak belirtildi ve giriş için şu parametreleri sağlamak için XAML ad alanı tanımlayıcısı ve XAML ad alanı öneki tanımına bu konuda daha önce sağlanan karşılık gelir.  
  
 XAML ad alanı bilgi parçası olarak bir XAML düğümü akışı veya diğer erişim XAML tür sistemi, İncelemekte olduğunuz varsa <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> XAML ad alanı tanımlayıcısı, rapor ve <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> XAML ad alanı öneki bildirir.  
  
 XAML düğümü akışı XAML ad alanı bilgisi geçerli olduğu varlık önündeki bir XAML düğüm olarak görünür. Bu XAML ad alanı bilgileri burada önündeki servis taleplerini içerir `StartObject` XAML kök öğe. Daha fazla bilgi için [anlama XAML düğüm Stream yapılarını ve kavramlarını](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 .NET Framework XAML Hizmetleri API kullanan birçok senaryo için en az bir XAML ad alanı bildiriminin bulunması bekleniyordu ve bildirimi içeren veya XAML şema içeriği tarafından gerekli bilgilere bakın. XAML ad alanları yüklenmesine veya ad alanları ve önceden yüklenmiş veya XAML şema içeriği tarafından bilinen bütünleştirilmiş kodlar içindeki belirli türlerini çözümlemek için derlemeleri ya da belirtmeniz gerekir.  
  
 XAML düğümü akışı oluşturmak için XAML türü bilgilerini ile XAML şema içeriği kullanılabilir olması gerekir. XAML tür bilgisi, ilgili XAML ad alanı oluşturmak her bir düğümün ilk belirleme olmadan belirlenemiyor. Bu noktada, hiçbir örnek türleri henüz oluşturulur, ancak derleme tanımlama ve yedekleme türü bilgileri aramak XAML şema içeriği gerekebilir. Örneğin, biçimlendirme işlemek için `<Party><PartyFavor/></Party>`, XAML şema içeriği adını ve türünü belirlemek mümkün `ContentProperty` , `Party`ve bu nedenle ayrıca XAML ad alanı bilgilerini bilmeniz gerekir `Party` ve `PartyFavor`. Varsayılan XAML şema içeriği söz konusu olduğunda, statik yansıma XAML türü düğümler düğüm akışında oluşturmak için gereken XAML türü sistem bilgilerin çoğunu bildirir.  
  
 XAML düğümü akıştan Nesne grafiği oluşturmak için özgün biçimlendirmede kullanılan ve XAML düğüm akış kaydedilen her XAML ön eki için XAML ad alanı bildirimi bulunmalıdır. Bu noktada, örnekleri oluşturulur ve doğru tür eşlemesi davranış oluşur.  
  
 XAML ad alanı bilgisi nerede XAML şema içeriği kullanmak için istediğinize XAML ad alanı tanımlı değil biçimlendirmede durumlarda önceden doldurmak gerekiyorsa kullanabileceğiniz bir XML ad alanı bildirimi bildirmek için bir tekniktir <xref:System.Xml.XmlParserContext> bir için<xref:System.Xml.XmlReader>. Ardından, kullanan <xref:System.Xml.XmlReader> XAML okuyucu oluşturucusu için giriş olarak veya <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 XAML ad alanı .NET Framework XAML hizmetlerinde işleme için uygun olan diğer iki API olan öznitelikleri <xref:System.Windows.Markup.XmlnsDefinitionAttribute> ve <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Bu öznitelikler, derlemelere uygulanır. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bir URI içeren herhangi bir XAML ad alanı bildirimi yorumlamak için XAML şema içeriği tarafından kullanılır. <xref:System.Windows.Markup.XmlnsPrefixAttribute> belirli bir XAML ad alanı tahmin edilebilir bir önek ile seri hale getirilebilir, böylece bu XAML yayma araçları tarafından kullanılır. Daha fazla bilgi için [özel türler ve Kitaplıkar için CLR öznitelikleri XAML-Related](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
