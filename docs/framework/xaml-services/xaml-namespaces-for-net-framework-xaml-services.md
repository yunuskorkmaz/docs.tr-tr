---
title: ".NET Framework XAML Hizmetleri İçin XAML Ad Uzayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: e09279209bf3d6925b61d55d6988b5af658f5aab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML Hizmetleri İçin XAML Ad Uzayları
XAML ad uzayı bir XML ad alanı tanımını genişleten bir kavramdır. Benzer şekilde bir XML ad alanı, XAML ad alanını kullanarak tanımlayabileceğiniz bir `xmlns` biçimlendirme özniteliği. XAML ad uzayları, XAML düğümü akışı ve diğer XAML Hizmetleri API'lerini de temsil edilir. Bu konuda XAML ad alanı kavram tanımlar ve XAML ad uzayları tanımlanabilir ve XAML şema bağlamları ve .NET Framework XAML hizmetlerinde diğer yönlerini tarafından kullanılan nasıl açıklanmaktadır.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML Namespace ve XAML Namespace  
 Yalnızca XAML özel XML biçimi temel XML form için kendi biçimlendirmesini kullandığı ve XAML ad uzayı özel bir XML ad alanı aynıdır. XAML ad uzayı ve kendi eşleme aracılığıyla bildirdiğiniz biçimlendirme içinde bir `xmlns` özniteliği bir öğe olarak uygulanmıştır. `xmlns` Bildirimi, XAML ad uzayı içinde bildirilen aynı öğeye yapılabilir. Bir öğe olarak yapılan bir XAML ad alanı bildirimi, bu öğe, bu öğenin tüm öznitelikleri ve bu öğenin tüm alt öğeleri için geçerlidir. Öznitelik, biçimlendirmede öznitelik adı bir parçası olarak öznitelik adı öneki başvuran sürece, özniteliği içeren öğe ile aynı olmayan bir XAML ad uzayları kullanabilirsiniz.  
  
 XAML ad uzayı bir XML ad alanı karşı fark bir XML ad alanı bir şema başvurmak için kullanılan veya yalnızca varlıklar ayırt etmek için kullanılabilir değil. XAML için türleri ve XAML içinde kullanılan üyeler sonuçta türleri yedeklenmesini çözümlenmesi gerekir ve XML Şeması kavramları de bu özellik için geçerli değildir. XAML ad uzayı XAML şema içeriği kullanılabilir bu tür eşlemeyi gerçekleştirmek için gereken bilgileri içerir.  
  
## <a name="xaml-namespace-components"></a>XAML Namespace bileşenleri  
 XAML ad alanı tanımını iki bileşenden oluşur: bir önek ve bir tanımlayıcı. Bu bileşenlerin her birini XAML ad uzayı biçimlendirme içinde bildirilen veya XAML türü sistemde tanımlanmış olduğunda mevcut.  
  
 Önek tarafından izin verilen gibi herhangi bir dize olabilir [XML 1.0 belirtimi W3C ad alanları](http://go.microsoft.com/fwlink/?LinkID=161735) . Önek tipik biçimlendirme dosyasında pek çok kere yinelenir olmadığından kurala göre önekleri genellikle çok kısa, dizelerdir. Birden çok XAML uygulamalarında kullanılmak üzere tasarlanmıştır belirli XAML ad uzayları belirli geleneksel önekleri kullanın. Örneğin, XAML dili XAML ad uzayı genellikle önekini kullanarak eşlenmiş `x`. Burada önek tanımında verilmedi ancak tanımlı veya by.NET Framework XAML Hizmetleri API sorgulanan olarak boş bir dize temsil edilen bir varsayılan XAML ad tanımlayabilirsiniz. Genellikle, varsayılan XAML ad uzayı kasıtlı olarak önek atlama ekranı kaplamış miktarını yükseltmek için seçilen bir XAML uygulama teknoloji ve senaryo ve sözcük dağarcıklarını tarafından biçimlendirme.  
  
 Tanımlayıcı tarafından izin verilen gibi herhangi bir dize olabilir [XML 1.0 belirtimi W3C ad alanları](http://go.microsoft.com/fwlink/?LinkID=161735). Kurala göre XML ad alanları veya XAML ad uzayları tanımlayıcıları genellikle URI biçiminde genellikle Protokolü tam bir mutlak URI olarak verilir. Genellikle, belirli bir XAML sözlüğü tanımlar sürüm bilgilerini yol dizesi bir parçası olarak kapsanır. XAML ad uzayları XML URI kuralının ötesinde ek tanımlayıcı kuralı ekleyin. XAML ad uzayları için tanımlayıcısı tarafından XAML şema içeriği o XAML ad alanı altındaki öğeleri olarak belirttiğiniz türlerini çözümlemek amacıyla ya da öznitelikleri üyelerine çözümlemek için gerekli bilgileri iletişim kurar.  
  
 XAML şema içeriği bilgileri iletişim amaçlar için XAML ad uzayı tanımlayıcısını hala URI biçiminde olabilir. Ancak, bu durumda URI Ayrıca belirli derleme veya derleme listesi eşleşen bir tanımlayıcı olarak bildirildi. Bu derlemede derleme öznitelik atanıyor tarafından yapılır <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. XAML ad uzayı ve öznitelikli bütünleştirilmiş kodunda bir CLR tabanlı türü çözümleme davranışı destekleyen bu yöntem .NET Framework XAML hizmetlerinde varsayılan XAML şema içeriği tarafından desteklenir. Daha fazla genel olarak, bu kural, XAML şema içeriği CLR içerir veya CLR derlemelerden CLR öznitelikleri okumak için gerekli olan varsayılan XAML şema içeriği dayalı olduğu durumlarda kullanılabilir.  
  
 XAML ad uzayları ayrıca bir CLR ad alanı ve türü tanımlayan derleme iletişim kuran bir kurala göre tanımlanabilir. Bu kural Hayır olduğu durumlarda kullanılır <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attribution türlerini içeren bütünleştirilmiş bulunmaktadır. Bu kural URI kuralının büyük olasılıkla daha karmaşıktır ve bir derlemeye başvuran birden çok yolu olduğundan belirsizlik ve çoğaltma için olasılığına da sahiptir.  
  
 En basit biçimiyle CLR ad alanı ve derleme kuralı kullanan bir tanımlayıcı aşağıdaki gibidir:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:`ve `; assembly=` sözdizimi değişmez değer bileşenleridir.  
  
 *clrnsName* bir CLR ad alanını tanımlayan dize adı. Bu dize adı CLR ad alanı ve diğer CLR ad ilişkisi konusunda ipuçları sağlayan herhangi iç nokta karakteri (.) içerir.  
  
 *assemblyShortName* XAML'de yararlı türü tanımlayan derleme dize adı. Bildirilen XAML ad alanı aracılığıyla erişilmesini türleri derlemesi tarafından tanımlanmış olması ve özellikle tarafından belirtilen CLR ad alanı içindeki bildirilmesi için beklenen *clrnsName*. Bu dize adı genellikle tarafından bildirilen bilgilerin parallels <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Daha eksiksiz bir CLR ad alanı ve derleme kuralı tanımını aşağıdaki gibidir:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* yasal olarak herhangi bir dize temsil eden bir <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> giriş. Bu dize kültür, ortak anahtar veya sürüm bilgileri içerebilir (Bu kavramlar tanımları için başvuru konusunun tanımlanmış <xref:System.Reflection.Assembly>). COFF biçimi ve kanıt (diğer aşırı tarafından kullanılan <xref:System.Reflection.Assembly.Load%2A>) amacıyla; yüklenirken XAML derleme için ilgili olmayan tüm yük bilgileri bir dize olarak sunulmalıdır.  
  
 Derleme için bir ortak anahtar belirterek bir yararlı XAML güvenlik ya da derlemeleri basit bir ad tarafından yüklenen ya da bir önbellek veya uygulama etki alanında önceden mevcut bulunabilir olası karışıklığı kaldırmak için bir tekniktir. Daha fazla bilgi için bkz: [XAML güvenlik konuları](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML Namespace bildirimlerinde XAML Hizmetleri API'si  
 XAML Hizmetleri API XAML ad alanı bildirimi tarafından temsil edilen bir <xref:System.Xaml.NamespaceDeclaration> nesnesi. XAML ad uzayı kodda bildiriyorsanız çağırmanız <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> Oluşturucusu. `ns` Ve `prefix` parametreleri dize olarak belirtildi ve bu parametrelerin sağlamak için giriş tanımını XAML ad tanımlayıcısı ve XAML ad alanı öneki için bu konuda daha önce sağlanan karşılık gelir.  
  
 XAML ad alanı bilgisi parçası olarak bir XAML düğüm akış veya diğer erişimi XAML tür sistemi aracılığıyla İncelemekte olduğunuz varsa <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> XAML ad tanımlayıcısı raporları ve <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> XAML ad alanı öneki bildirir.  
  
 XAML düğümü akışı XAML ad alanı bilgisi geçerli olduğu varlık önündeki XAML düğümü olarak görünebilir. Bu durumlarda burada XAML ad alanı bilgisi önündeki içerir `StartObject` XAML kök öğesinin. Daha fazla bilgi için bkz: [anlama XAML düğüm akış yapılarını ve kavramlarını](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 .NET Framework XAML Hizmetleri API kullanan çok sayıda senaryoları için en az bir XAML ad alanı bildiriminin bulunması bekleniyordu ve bildirimi içeren veya XAML şema içeriği tarafından gerekli bilgilere bakın. XAML ad uzayları yüklenmesi veya ad alanları ve önceden yüklenen veya XAML şema içeriği tarafından bilinen bütünleştirilmiş kodlar içindeki belirli tür çözümlenmesine yardımcı olmak için derlemeleri ya da belirtmeniz gerekir.  
  
 XAML düğümü akışı oluşturmak için XAML tür bilgileri XAML şema içeriği kullanılabilir olmalıdır. XAML tür bilgilerini ilgili XAML ad alanı oluşturmak her düğüm için ilk belirleme olmadan belirlenemiyor. Bu noktada, hiçbir türlerin örnekleri henüz oluşturulur, ancak XAML şema içeriği derleme tanımlama ve türü yedekleme bilgileri aramak gerekebilir. Örneğin, biçimlendirme işlenmesi için `<Party><PartyFavor/></Party>`, XAML şema içeriği adını ve türünü belirlemek mümkün `ContentProperty` , `Party`ve bu nedenle de XAML ad alanı bilgilerini bilmeniz gerekir `Party` ve `PartyFavor`. Varsayılan XAML şema içeriği söz konusu olduğunda statik yansıma XAML tür düğümleri düğüm akışta oluşturmak için gereken XAML tür sistem bilgilerin büyük bölümünü bildirir.  
  
 Bir nesne grafiğinin öğesinden bir XAML düğümü akışı oluşturmak için özgün biçimlendirmede kullanılan ve XAML düğüm akış kaydedilen her XAML öneki için XAML ad uzayları bildirimleri bulunmalıdır. Bu noktada, örnekleri oluşturulur ve doğru türü eşlemesi davranış gerçekleşir.  
  
 XAML ad alanı bilgilerini burada kullanmak için XAML şema içeriği düşündüğünüz XAML ad uzayı tanımlı değil biçimlendirmede durumlarda önceden gerekiyorsa kullanabileceğiniz bir XML ad alanı bildirimleri bildirmek için tekniktir <xref:System.Xml.XmlParserContext> bir için<xref:System.Xml.XmlReader>. Ardından, kullanan <xref:System.Xml.XmlReader> XAML okuyucu oluşturucusu için giriş olarak veya <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 XAML ad alanı .NET Framework XAML hizmetlerinde işleme için uygun olan diğer iki API olan öznitelikleri <xref:System.Windows.Markup.XmlnsDefinitionAttribute> ve <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Bu öznitelikler derlemeler için geçerlidir. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML şema içeriği tarafından bir URI içeren XAML ad alanı bildiriminin yorumlamak için kullanılır. <xref:System.Windows.Markup.XmlnsPrefixAttribute>XAML yayma ve böylece belirli XAML ad uzayı tahmin edilebilir bir önek ile seri hale araçları tarafından kullanılır. Daha fazla bilgi için bkz: [özel türler ve Kitaplıkar için XAML-Related CLR öznitelikleri](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML düğüm akış yapılarını ve kavramlarını anlama](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
