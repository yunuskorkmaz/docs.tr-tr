---
title: .NET Framework XAML Hizmetleri İçin XAML Ad Uzayları
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837174"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML Hizmetleri İçin XAML Ad Uzayları
XAML ad alanı, bir XML ad alanı tanımını genişleten bir kavramdır. XML ad alanına benzer şekilde, biçimlendirme içinde bir `xmlns` özniteliği kullanarak XAML ad alanı tanımlayabilirsiniz. Xaml ad alanları, XAML düğüm akışı ve diğer XAML Hizmetleri API 'Lerinde de temsil edilir. Bu konu xaml ad alanı kavramını tanımlar ve xaml ad alanlarının nasıl tanımlanabileceğini ve xaml şema bağlamları tarafından .NET Framework XAML hizmetlerinin diğer yönlerini açıklar.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML ad alanı ve XAML ad alanı  
 Xaml ad alanı özelleştirilmiş bir XML ad alanıdır. tıpkı XAML, özelleşmiş bir XML biçimidir ve biçimlendirmesi için temel XML formunu kullanır. Biçimlendirme ' de bir XAML ad alanı ve eşlemesini bir öğesine uygulanan `xmlns` özniteliği aracılığıyla bildirirsiniz. `xmlns` bildirimi, XAML ad alanının bildirildiği aynı öğeye yapılabilir. Bir öğe için yapılan XAML ad alanı bildirimi, bu öğe için geçerli, bu öğenin tüm öznitelikleri ve bu öğenin tüm alt öğeleri için geçerlidir. Öznitelikler, özniteliği içeren öğeyle aynı olmayan XAML ad alanlarını kullanabilir, bu nedenle öznitelik adının kendisi, biçimlendirme içindeki öznitelik adının bir parçası olarak önekte başvuruda bulunur.  
  
 Bir XAML ad alanının bir XML ad alanı ile ayırt edilmesi, bir şemaya başvurmak için bir XML ad alanının kullanılmasına veya yalnızca varlıkları ayırt etmek için kullanılmasına izin verebilir. XAML için XAML 'de kullanılan türlerin ve üyelerin, sonunda, son olarak türleri yedeklemek için çözümlenmesi ve XML şema kavramlarının bu özelliğe iyi uygulanmamalıdır. XAML ad alanı, bu tür eşlemesini gerçekleştirmek için XAML şema bağlamının kullanılabilir olması gereken bilgileri içerir.  
  
## <a name="xaml-namespace-components"></a>XAML ad alanı bileşenleri  
 XAML ad alanı tanımında iki bileşen vardır: önek ve tanımlayıcı. Bu bileşenlerin her biri, bir XAML ad alanı biçimlendirme içinde bildirildiğinde veya XAML tür sisteminde tanımlanmadığında bulunur.  
  
 Ön ek, [XML 1,0 belirtiminde W3C ad alanları](https://www.w3.org/TR/REC-xml-names/) tarafından izin verilen herhangi bir dize olabilir. Kural gereği, ön ekler genellikle çok kısa dizelerdir, çünkü önek tipik bir biçimlendirme dosyasında birçok kez tekrarlanıyor. Birden çok XAML uygulamasında kullanılması amaçlanan bazı XAML ad alanları, belirli geleneksel önekleri kullanır. Örneğin, XAML Language XAML ad alanı genellikle `x`ön eki kullanılarak eşleştirilir. Varsayılan bir XAML ad alanı tanımlayabilirsiniz, burada ön ek, tanım içinde verilmez ancak tanımlanmışsa veya sorgulanan by.NET Framework XAML Hizmetleri API 'SI için boş bir dize olarak gösterilir. Genellikle, XAML uygulayan bir teknolojinin ve onun senaryolarından ve sözcük dağarcıklarını bir dizi ön eki atlama sayısını yükseltmek için varsayılan XAML ad alanı kasıtlı olarak seçilir.  
  
 Tanımlayıcı, [XML 1,0 belirtiminde W3C ad alanları](https://www.w3.org/TR/REC-xml-names/)tarafından izin verilen herhangi bir dize olabilir. Kurala göre, XML ad alanları veya XAML ad alanları için tanımlayıcılar genellikle, genellikle protokol nitelikli mutlak bir URI olarak URI biçiminde verilir. Genellikle, belirli bir XAML sözlüğünü tanımlayan sürüm bilgileri yol dizesinin parçası olarak kapsanır. XAML ad alanları, XML URI kuralının ötesinde ek bir tanımlayıcı kuralı ekler. XAML ad alanları için, tanımlayıcı, xaml ad alanı altında öğe olarak belirtilen türleri çözümlemek ya da üyelerin özniteliklerini çözümlemek için bir XAML şeması bağlamı için gereken bilgileri iletişim kurar.  
  
 XAML şeması bağlamına bilgi iletişim sağlamak amacıyla XAML ad alanı için tanımlayıcı yine de URI biçiminde olabilir. Ancak, bu durumda URI aynı zamanda belirli bir derlemede veya derlemeler listesinde eşleşen bir tanımlayıcı olarak da bildirilmiştir. Bu derleme, bütünleştirilmiş koda <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Attributing tarafından yapılır. XAML ad alanını tanımlama ve öznitelikli derlemede CLR tabanlı tür çözümleme davranışını destekleme yöntemi, .NET Framework XAML hizmetlerinde varsayılan XAML şeması bağlamı tarafından desteklenir. Daha genel olarak, bu kural XAML şema bağlamının CLR 'yi hangi durumlarda veya clr derlemelerinden CLR özniteliklerini okumak için gerekli olan varsayılan XAML şema bağlamını temel alarak kullanılabilir.  
  
 XAML ad alanları, CLR ad alanını ve tür tanımlama derlemesini iletişim kuran bir kural tarafından da tanımlanabilir. Bu kural, türler içeren derlemelerde <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributıon olmadığı durumlarda kullanılır. Bu kural, URI kuralına kıyasla büyük olasılıkla daha karmaşıktır ve bir derlemeye başvurmanın birden çok yolu olduğundan belirsizlik ve çoğaltma için de potansiyeli olur.  
  
 CLR ad alanını ve derleme kuralını kullanan bir tanımlayıcının en temel biçimi aşağıdaki gibidir:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *AssemblyShortName*  
  
 `clr-namespace:` ve `; assembly=`, sözdiziminin sabit bileşenleridir.  
  
 *clrnsName* , bir clr ad alanını tanımlayan dize adıdır. Bu dize adı, CLR ad alanı ve diğer CLR ad alanlarıyla ilişkisi hakkında ipuçları sağlayan herhangi bir iç nokta karakterini (.) içerir.  
  
 *AssemblyShortName* , XAML 'de yararlı olan türleri tanımlayan bir derlemenin dize adıdır. Tanımlanan XAML ad alanı üzerinden erişilecek türlerin derleme tarafından tanımlanması ve özel olarak *clrnsName*tarafından belirtilen clr ad alanı içinde bildirilmesini bekleniyor. Bu dize adı, genellikle <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>tarafından bildirilen bilgileri paraleller.  
  
 CLR ad alanı ve derleme kuralının daha kapsamlı bir tanımı aşağıdaki gibidir:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *AssemblyName*  
  
 *assemblyName* <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> girişi olarak geçerli olan herhangi bir dizeyi temsil eder. Bu dize kültür, ortak anahtar veya sürüm bilgilerini içerebilir (bu kavramların tanımları <xref:System.Reflection.Assembly>) için başvuru konusunda tanımlanmıştır. COFF biçimi ve kanıt (<xref:System.Reflection.Assembly.Load%2A>diğer aşırı yüklemeleri tarafından kullanılan) XAML derleme yükleme amaçlarıyla ilgili değildir; Tüm yükleme bilgileri bir dize olarak sunulmalıdır.  
  
 Derleme için bir ortak anahtar belirtmek, XAML güvenliği için yararlı bir tekniktir veya derlemeler basit ad veya bir önbellekte ya da uygulama etki alanında önceden mevcut olduğunda var olabilecek belirsizliği ortadan kaldırır. Daha fazla bilgi için bkz. [xaml güvenlik konuları](xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML ad alanı bildirimleri XAML Hizmetleri API 'SI  
 XAML Hizmetleri API 'sinde, bir XAML ad alanı bildirimi bir <xref:System.Xaml.NamespaceDeclaration> nesnesi tarafından temsil edilir. Kodda bir XAML ad alanı bildirirken <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> oluşturucusunu çağırın. `ns` ve `prefix` parametreleri dizeler olarak belirtilir ve bu parametreler için sağlanacak giriş, bu konuda daha önce sağlandığı gibi XAML ad alanı tanımlayıcısının ve XAML ad alanı ön ekinin tanımına karşılık gelir.  
  
 Xaml ad alanı bilgilerini bir XAML düğüm akışının parçası olarak veya XAML türü sistemine yönelik diğer erişimle inceleyerek, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> XAML ad alanı tanımlayıcısını raporlar ve <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> XAML ad alanı önekini raporlar.  
  
 XAML düğüm akışında XAML ad alanı bilgileri, uygulandığı varlıktan önce gelen bir XAML düğümü olarak görünebilir. Bu, XAML ad alanı bilgilerinin XAML kök öğesinin `StartObject` önündeki durumları içerir. Daha fazla bilgi için bkz. [xaml düğüm akışı yapılarını ve kavramlarını anlama](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 .NET Framework XAML Hizmetleri API 'SI kullanan birçok senaryo için, en az bir XAML ad alanı bildiriminin bulunması beklenir ve bildirimin bir XAML şeması bağlamı için gereken bilgileri içermesi veya başvurması gerekir. XAML ad alanları yüklenecek derlemeleri belirtmeli ya da ad alanları ve XAML şeması bağlamı tarafından zaten yüklenmiş veya bilinen derlemeler içindeki belirli türleri çözümlemede yardımcı olmalıdır.  
  
 Xaml düğüm akışı oluşturmak için xaml şema bağlamı aracılığıyla XAML tür bilgilerinin kullanılabilir olması gerekir. XAML tür bilgileri, oluşturulacak her düğüm için ilgili XAML ad alanı belirlenmeden belirlenemez. Bu noktada, henüz bir tür örneği oluşturulmaz, ancak XAML şema bağlamının, tanımlama bilgisi ve yedekleme türünden bilgi araması gerekebilir. Örneğin, biçimlendirme `<Party><PartyFavor/></Party>`işlemek için XAML şeması bağlamı `Party``ContentProperty` adını ve türünü belirleyebilmelidir ve ayrıca `Party` ve `PartyFavor`için XAML ad alanı bilgilerini bilmelidir. Varsayılan XAML şema bağlamı durumunda, statik yansıma düğüm akışında XAML türü düğümleri oluşturmak için gereken XAML türü sistem bilgilerinin çoğunu raporlar.  
  
 Xaml düğüm akışından bir nesne grafiği oluşturmak için, XAML ad alanı bildirimlerinin özgün İşaretlemede kullanılan her XAML öneki için mevcut olması ve XAML düğüm akışına kaydedilmeleri gerekir. Bu noktada örnekler oluşturulur ve true tür eşleme davranışı oluşur.  
  
 Xaml ad alanı bilgilerini önceden almanız gerekiyorsa, xaml şema bağlamını kullanmak istediğiniz XAML ad alanının biçimlendirmede tanımlanmadığı durumlarda kullanabileceğiniz bir teknik, <xref:System.Xml.XmlReader>için <xref:System.Xml.XmlParserContext> XML ad alanı bildirimleri bildirmektir. Daha sonra bu <xref:System.Xml.XmlReader> XAML okuyucu Oluşturucusu için giriş olarak kullanın veya <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 .NET Framework XAML hizmetlerinde XAML ad alanı işlemesi için uygun olan diğer iki API, <xref:System.Windows.Markup.XmlnsDefinitionAttribute> ve <xref:System.Windows.Markup.XmlnsPrefixAttribute>öznitelikleridir. Bu öznitelikler derlemeler için geçerlidir. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, bir XAML şema bağlamı tarafından URI içeren herhangi bir XAML ad alanı bildirimini yorumlamak için kullanılır. <xref:System.Windows.Markup.XmlnsPrefixAttribute>, XAML 'yi sunan araçlar tarafından kullanılır, böylece belirli bir XAML ad alanı öngörülebilir bir ön ek ile seri hale getirilebilir. Daha fazla bilgi için bkz. [özel türler ve kitaplıklar Için xaml ıle ılgılı clr öznitelikleri](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama](understanding-xaml-node-stream-structures-and-concepts.md)
