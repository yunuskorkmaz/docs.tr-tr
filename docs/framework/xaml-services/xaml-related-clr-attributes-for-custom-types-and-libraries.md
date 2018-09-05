---
title: Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 13cc4d85a1a4b5c9b1ff61afbf7980a54e3d22d0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563650"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri
Bu konuda, .NET Framework XAML hizmetlerinde tarafından tanımlanan ortak dil çalışma zamanı (CLR) öznitelikleri açıklanmaktadır. Ayrıca, XAML ile ilgili bir senaryo uygulamayı derlemeler veya türler için olan .NET Framework içinde tanımlanan diğer CLR öznitelikleri açıklar. Derlemeleri, türleri veya üyeleri bu CLR öznitelikleri ile öznitelik atanıyor, türleriyle ilgili XAML türü sistem bilgileri sağlar. XAML düğümü akışı doğrudan işlemek veya ayrılmış XAML okuyucular ve yazıcılar XAML aracılığıyla .NET Framework XAML hizmetlerinde kullanan herhangi bir XAML tüketici bilgileri sağlanır.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Özel türler ve özel üyeler için XAML ilişkili CLR öznitelikleri  
 CLR öznitelikleri kullanarak genel CLR türlerinizi tanımlamak için kullandığınız, aksi takdirde bu öznitelikler kullanılamıyor kapsar. Ardından yedekleme türü tanımlamak için CLR kullanırsanız, .NET Framework XAML Hizmetleri XAML yazarlar tarafından kullanılan varsayılan XAML şema içeriği CLR attribution üzerinden erişiyorsanız, derlemeleri yedekleme karşı okuyabilirsiniz.  
  
 Aşağıdaki bölümlerde, özel türler veya özel üyeler için uygulayabileceğiniz XAML ile ilgili özniteliklerini açıklar. Her bir CLR öznitelik, bir XAML tür sistemiyle ilgili bilgileri iletişim kurar. Yükleme yolu öznitelikli bilgiler, geçerli bir XAML düğüm akış form XAML okuyucu ya da yardımcı olur veya geçerli nesne grafiği oluşturmak XAML yazıcı sağlar. Kaydetme yolu, öznitelikli bilgilerin reconstitutes XAML türü sistem bilgileri; geçerli bir XAML düğüm akış form XAML okuyucu ya da yardımcı olur veya seri hale getirme ipuçları veya XAML yazıcı veya diğer XAML tüketiciler gereksinimlerini bildirir.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **İçin geçerlidir:** sınıfı, özelliği veya `get` iliştirilebilir özellikleri için destek erişimci üyeleri.  
  
 **Bağımsız değişkenleri:** yok  
  
 <xref:System.Windows.Markup.AmbientAttribute> özellik veya alan öznitelikli türü tüm özellikleri XAML içinde ortam özelliği kavramı altında yorumlanması gerektiğini gösterir. XAML işlemci türü sahipleri üyelerinin nasıl belirlemek için ortam kavramı ilişkilendirir. Ortam özellikleri, burada değeri bir nesne grafiğinin oluştururken, ancak tipik türü üye araması oluşturulan hemen XAML düğüm kümesi için askıya alındı ayrıştırıcı bağlamda kullanılabilir olması beklenen bir özelliktir.  
  
 Ortam kavramı, CLR attribution nasıl tanımladığını açısından özellikleri olarak temsil edilmeyen iliştirilebilir üyelerine uygulanabilir <xref:System.AttributeTargets>. Yalnızca durumunda, yöntem attribution kullanım uygulanması gereken bir `get` iliştirilebilir kullanım için XAML destekleyen erişimcisi.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** tek oluşturucu bağımsız değişkeni eşleşen özelliğin adını belirten dize.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> Bir nesne bir varsayılan olmayan bir oluşturucu sözdizimi kullanılarak başlatılabilir ve belirtilen adda bir özelliği yapı bilgileri sağlayan belirtir. Bu bilgiler, öncelikle XAML serileştirme için sağlar. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** öznitelik türünün bir üyenin adını belirten dize.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> adlandırılmış bağımsız değişkeni tarafından özellik türü için XAML içerik özelliği olarak kullanılmalıdır gösterir. XAML İçerik özellik tanımı tanımlama türüne atanabilir tüm türetilmiş türlere devralır. Uygulama tarafından belirli bir türetilmiş tür tanımında geçersiz kılabilirsiniz <xref:System.Windows.Markup.ContentPropertyAttribute> belirli türetilmiş tür.  
  
 XAML içerik özelliği hizmet veren özelliği için etiketleme özelliği için özellik öğesi XAML kullanımı atlanabilir. Genellikle, içerik ve kapsama Modellerinizi için kolaylaştırılmış bir XAML biçimlendirmesi Yükselt XAML İçerik özellikleri belirleyin. Tek bir üye XAML içerik özelliği belirtilmiş olduğundan, bazen tasarımı seçimleri yapmak için birden fazla kapsayıcı ile ilgili türün özelliklerini XAML içerik özelliği belirlenmiş da sahip olursunuz. Kapsayıcı özellikleri açık özellik öğelerle kullanılması gerekir.  
  
 XAML düğümü akışı XAML İçerik özellikleri hala üretmek `StartMember` ve `EndMember` için özellik adını kullanarak düğümleri <xref:System.Xaml.XamlMember>. XAML içerik özelliği bir üyesi olup olmadığını belirlemek için inceleyin <xref:System.Xaml.XamlType> değerini `StartObject` getirin ve değeri elde etmek <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **İçin geçerlidir:** sınıfı, özellikle koleksiyon türleri.  
  
 **Bağımsız değişkenleri:** A <xref:System.Type> türü için yabancı içeriği içerik sarmalayıcı türü olarak kullanmak için belirtir.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> Bir veya daha fazla türlerini yabancı içeriğini kaydırmak için kullanılacak olan ilişkili koleksiyon türü belirtir. Yabancı içeriği burada tür sistem kısıtlamalarını içerik özelliği türüne sahip olan türü için XAML kullanım destekleyecektir olası içerik durumların tümünde yakalamayın çalışmalarına ifade eder. Örneğin, XAML desteklemek için belirli bir türün içerik türü kesin belirlenmiş bir genel dizeleri destekleyebilir <xref:System.Collections.ObjectModel.Collection%601>. İçerik sarmalayıcıları geçişini önceden var olan biçimlendirme kuralları için XAML'ın conception koleksiyonları, metin ilgili geçirme içerik modelleri gibi atanabilir değer olarak yararlıdır.  
  
 Birden fazla içerik sarmalayıcı türü belirtmek için birden çok kez özniteliğini uygulayın.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **İçin geçerlidir:** özelliği  
  
 **Bağımsız değişkenleri:** öznitelikli türünün başka bir üyenin adını belirten dize.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> Öznitelikli özelliği başka bir özelliğin değerine bağlı olduğunu gösterir. Bu özniteliği için bir özellik tanımı uygulama bağımlı özellikler önce XAML nesne yazılı olarak işlenmesini sağlar. Açık olan <xref:System.Windows.Markup.DependsOnAttribute> burada ayrıştırma belirli bir sırada gelmelidir için geçerli bir nesne oluşturma türlerinde olağanüstü durumlar özellikleri belirtin.  
  
 Birden çok uygulayabilirsiniz <xref:System.Windows.Markup.DependsOnAttribute> çalışmalarına bir özellik tanımı.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **İçin geçerlidir:** olması beklenir sınıfı bir <xref:System.Windows.Markup.MarkupExtension> türetilmiş tür.  
  
 **Bağımsız değişkenleri:** A <xref:System.Type> olarak beklediğiniz en hassas türünü belirten `ProvideValue` öznitelikli sonucunu <xref:System.Windows.Markup.MarkupExtension>.  
  
 Daha fazla bilgi için [genel XAML işaretleme uzantılarına](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** attribution iki biçimini destekler:  
  
-   Öznitelikli türüne bir özelliğin adını belirten dize.  
  
-   Bir özelliğin adını belirten dize ve bir <xref:System.Type> türünün adlı özelliği tanımlar. Bu form XAML namescope özelliği iliştirilebilir bir üye belirtmek için geçerlidir.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> Öznitelikli sınıf için XAML namescope değer sağlayan bir alan özelliği belirtir. XAML namescope özelliği uygulayan bir nesne başvurusu beklenir <xref:System.Windows.Markup.INameScope> ve gerçek XAML namescope, depolama ve davranışını içerir.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** öznitelikli türüne göre çalışma zamanı adı özelliğin adını belirten dize.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> XAML için eşlenen öznitelikli türünün bir özelliği bildirir [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md). Özellik türü olmalıdır <xref:System.String> ve okuma/yazma olmalıdır.  
  
 Tanımlama türüne atanabilir tüm türetilmiş türlere tanımı devralır. Uygulama tarafından belirli bir türetilmiş tür tanımında geçersiz kılabilirsiniz <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> belirli türetilmiş tür.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **İçin geçerlidir:** türleri  
  
 **Bağımsız değişkenleri:** yok.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> içindeki boşluk önemli içeriği alt öğe olarak görünebilir belirli türlere uygulanır (içeriği içeren bir koleksiyon tarafından tutulan <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> esas olarak Kaydet geçerlidir, ancak yoludur yükleme yolu XAML türü sistemde bulunan inceleyerek <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Daha fazla bilgi için [boşluk XAML içinde işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Başvuru belgeleri:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **İçin geçerlidir:** sınıf, özellik, yöntemi (yalnızca XAML geçerli yöntemi durumda bir `get` iliştirilebilir bir üye destekleyen erişimci).  
  
 **Bağımsız değişkenleri:** <xref:System.Type> , <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> bir XAML içinde özel bağlam başvuran <xref:System.ComponentModel.TypeConverter>. Bu <xref:System.ComponentModel.TypeConverter> özel türleri veya üyeleri bu tür için tür dönüştürme davranış sağlar.  
  
 Uyguladığınız <xref:System.ComponentModel.TypeConverterAttribute> öznitelik, bir tür dönüştürücüsü gerçeklemesi başvuran türünüz için. Sınıflar, yapılar veya arabirimlerini XAML için tür dönüştürücüleri tanımlayabilirsiniz. Numaralandırmalar için tür dönüştürme dönüştürme yerel olarak etkin olduğunu sağlamak gerekmez.  
  
 Bir tür dönüştürücüsü hedeflenen hedef türünüz öznitelikleri ya da başlatma metin biçimlendirme için kullanılan bir dize dönüştürmek başlatabilmeniz gerekir. Daha fazla bilgi için [TypeConverters ve XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Bir türdeki tüm değerlere uygulamak yerine, XAML için tür dönüştürücüsü davranış da belirli bir özellik üzerinde kurulabilir. Bu durumda, uyguladığınız <xref:System.ComponentModel.TypeConverterAttribute> özellik tanımı için (Dış tanımı, söz konusu `get` ve `set` tanımları).  
  
 XAML kullanım özel iliştirilebilir üyesi için türü dönüştürücü davranış uygulayarak atanabilir <xref:System.ComponentModel.TypeConverterAttribute> için `get` yöntemi erişimci, XAML kullanımını destekler.  
  
 Benzer şekilde <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> XAML varlığını önce .NET Framework içinde var ve tür dönüştürücüsünü modeli başka amaçlarla hizmet. Başvuru ve kullanmak için <xref:System.ComponentModel.TypeConverterAttribute>, tam olarak bunu uygun veya sağlayan bir `using` bildirimi <xref:System.ComponentModel>. Bu gibi durumlarda, sistem derlemesi ayrıca projenize eklemelisiniz.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** ilgili özellik adıyla başvuran bir dize.  
  
 Bir sınıfın CLR özelliği bu diğer adları gösterir [x: Uid yönergesi](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** bir Boole değeri. Özniteliğin hedeflenen amaç için kullanıyorsanız, bu her zaman olarak belirtilmelidir `true`.  
  
 Bu tür yukarıdan aşağıya XAML Nesne grafiği oluşturma sırasında kurulmuştur olup olmadığını gösterir. Programlama modelinizin tanımına büyük olasılıkla çok yakından ilgili gelişmiş bir kavram olmasıdır. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **İçin geçerlidir:** sınıf, özellik, yöntemi (yalnızca XAML geçerli yöntemi durumda bir `get` iliştirilebilir bir üye destekleyen erişimci).  
  
 **Bağımsız değişkenleri:** A <xref:System.Type> öznitelikli türü tüm özelliklerde serileştirilirken kullanılacak değeri seri hale getirici destek sınıfı belirtir ya da belirli öznitelikli özelliği.  
  
 <xref:System.Windows.Markup.ValueSerializer> Daha fazla durum ve bağlamını anlamaktan gerektiren bir değer serileştirme sınıfı belirtir bir <xref:System.ComponentModel.TypeConverter> yapar. <xref:System.Windows.Markup.ValueSerializer> uygulayarak iliştirilebilir bir üyeyle ilişkilendirilebilir <xref:System.Windows.Markup.ValueSerializerAttribute> statik özniteliği `get` iliştirilebilir üye erişimci yöntemi. Değer serileştirme geçerli ayrıca numaralandırmalar, arabirimler ve yapıları, ancak temsilciler için değil.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **İçin geçerlidir:** sınıfı, özellikle burada nesne öğeleri beyaz boşluk UI gösterimi için önemli olabilir beklenen karma içerik barındırmak için koleksiyon türleri.  
  
 **Bağımsız değişkenleri:** yok.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> bir koleksiyon türü boşluk önemli XAML düğümü akışın değeri düğümleri koleksiyonundaki oluşumu etkileyen bir XAML işlemcisi tarafından işlenmesi gerektiğini gösterir. Daha fazla bilgi için [boşluk XAML içinde işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **İçin geçerlidir:** sınıf özelliği.  
  
 **Bağımsız değişkenleri:** destekleyen iki attribution forms dizeler olarak türleri veya devre dışı olarak türleri <xref:System.Type>. Bkz: <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Bir sınıf ya da özellik ertelenmiş yük kullanım için XAML (şablon davranış gibi) sahip ve raporları erteleniyor davranışı ve hedef/içerik türünü sağlar sınıfını gösterir.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** geri çağırma adları.  
  
 Bir sınıf bir işaretleme uzantısı, bir veya daha fazla özelliği için bir değer sağlamak için kullanabilirsiniz ve XAML yazan bir sınıfın herhangi bir özellikte işaretleme uzantısı ayarlama işlemi gerçekleştirmeden önce çağırmalıdır bir işleyici başvuruları gösterir.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** geri çağırma adları.  
  
 Bir sınıf bir veya daha fazla özelliği için bir değer sağlamak için bir tür dönüştürücüsü kullanabilirsiniz ve XAML yazan bir sınıfın herhangi bir özellikte türü dönüştürücü ayarlama işlemi gerçekleştirmeden önce çağırmalıdır bir işleyici başvuran gösterir.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **İçin geçerlidir:** sınıfı  
  
 **Bağımsız değişkenleri:** diğer özelliğin adını belirten bir dize `xml:lang` öznitelikli türü.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> bir özelliği eşleyen XML öznitelik türü bildirir `lang` yönergesi. Özelliği değil gerekmeyen türünde <xref:System.String>, ancak bir dizeden (Bu elde edilebilir bir tür dönüştürücüsü özelliğin türü veya belirli bir özellik ile ilişkilendirilmesi yoluyla) atanabilir olmalıdır. Okuma/yazma özelliği olmalıdır.  
  
 Eşleme senaryosu `xml:lang` , böylelikle bir çalışma zamanı nesne modelini XML belirtilen dil bilgileri ile bir XMLDOM özellikle işlemeden erişebilir.  
  
 Tanımlama türüne atanabilir tüm türetilmiş türlere tanımı devralır. Uygulama tarafından belirli bir türetilmiş tür tanımında geçersiz kılabilirsiniz <xref:System.Windows.Markup.XmlLangPropertyAttribute> , seyrek bir senaryo olsa da, belirli türü, türetilmiş.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>XAML ilişkili CLR öznitelikleri derleme düzeyinde  
 Aşağıdaki bölümlerde, tür veya üye tanımları uygulanmaz, ancak bunun yerine derlemeler için uygulanan XAML ile ilgili özniteliklerini açıklar. Bu öznitelikler, ilgili XAML içinde kullanılacak özel türleri içeren bir kitaplık tanımlama, genel amaç için. Bazı öznitelikleri mutlaka etkisi XAML düğümü akışı doğrudan değildir, ancak diğer tüketiciler kullanmak düğüm akışına geçirilir. Tasarım ortamları veya XAML ad alanı bilgisi gerekiyor ve ön ek bilgi ilişkili seri hale getirme işlemleri Tüketiciler için bilgileri içerir. (.NET Framework XAML hizmetlerinde varsayılan dahil) bir XAML şema içeriği de bu bilgileri kullanır.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Bağımsız değişkenleri:**  
  
-   XAML ad alanı listelense tanımlayıcısını belirten bir dize.  
  
-   Önceki bağımsız XAML ad alanı listelense XAML ad alanı tanımlayıcısını belirten bir dize.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> XAML ad alanı tarafından başka bir XAML ad alanı birden fazla yolu eklendi olduğunu belirtir. Genellikle, subsuming XAML ad alanı belirtilirse, önceden tanımlanmış <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Bu bir teknik olabilir bir XAML sözlük bir kitaplıkta ve daha önce tutulan sözlük karşı önceden tanımlanmış biçimlendirme ile uyumlu hale getirmek için sürüm oluşturma için kullanılır.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Bağımsız değişkenleri:**  
  
-   Tanımlamak için XAML ad alanı tanımlayıcısını belirten bir dize.  
  
-   Bir CLR ad alanı adları bir dize. CLR ad uzayı genel türler, derlemede tanımlamanız gerekir ve en az bir CLR ad alanı türleri için XAML kullanım kullanılmaya.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Derleme başına temelinde XAML ad alanı için tür çözümlemesi XAML nesne yazıcısı veya XAML şema içeriği tarafından kullanılan sonra bir CLR ad alanı arasındaki eşlemeyi belirtir.  
  
 Birden fazla <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bir bütünleştirilmiş koda uygulanabilir. Bu, aşağıdaki nedenlerden herhangi bir birleşimini için yapılabilir:  
  
-   Kitaplık tasarım mantıksal organizasyonu çalışma zamanı API erişimi için birden çok CLR ad alanını içerir. Ancak, bu ad alanlarında tüm türleri aynı XAML ad başvurarak XAML kullanılabilir olmasını istersiniz. Bu durumda, birkaç uygulama <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aynı öznitelikleri <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> ancak farklı değer <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> değerleri. Framework veya uygulama varsayılan XAML ad alanı, ortak kullanım olabilir amaçlamaktadır XAML ad alanı eşlemeleri tanımlıyorsanız, bu özellikle yararlıdır.  
  
-   Birden çok CLR ad kitaplığı tasarım içerir ve söz konusu CLR ad alanlarında türleri kullanımları arasında bilinçli bir XAML ad alanı ayrım istediğiniz.  
  
-   Birden fazla XAML ad alanı erişilebilir olmasını istediğiniz ve derlemede bir CLR ad alanı tanımlayın. Bu senaryoda, aynı kod temeli ile birden çok sözcük dağarcıklarını desteklediğiniz oluşur.  
  
-   XAML dil desteği bir veya birden çok CLR ad alanlarında tanımlarsınız. Bu, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değeri `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Bağımsız değişkenleri:**  
  
-   XAML ad alanı tanımlayıcısını belirten bir dize.  
  
-   Bir önerilen ön eki belirten bir dize.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> XAML ad alanı için kullanılacak bir önerilen ön ekini belirtir. .NET Framework XAML hizmetlerinde tarafından seri hale getirilmiş bir XAML dosyasında öğeler ve öznitelikler yazarken önek yararlıdır <xref:System.Xaml.XamlXmlWriter>, veya düzenleme özellikleri ne zaman bir XAML uygulama kitaplığı olan XAML tasarım ortamı ile etkileşim kurar.  
  
 Birden fazla <xref:System.Windows.Markup.XmlnsPrefixAttribute> bir bütünleştirilmiş koda uygulanabilir. Bu, aşağıdaki nedenlerden herhangi bir birleşimini için yapılabilir:  
  
-   Derlemenizi türleri için birden fazla XAML ad alanı tanımlar. Bu durumda her XAML ad alanı için farklı bir önek değerleri tanımlamanız gerekir.  
  
-   Birden çok sözcük dağarcıklarını destekleme ve her bir sözlük ve XAML ad alanı için farklı önekler kullanın.  
  
-   XAML dil desteği derlemesinde tanımlayın ve sahip bir <xref:System.Windows.Markup.XmlnsDefinitionAttribute> için `http://schemas.microsoft.com/winfx/2006/xaml`. Bu durumda, genellikle önek Yükselt `x`.  
  
> [!NOTE]
>  .NET framework XAML hizmetlerinde, ayrıca XAML ile ilgili öznitelik tanımlar <xref:System.Windows.Markup.RootNamespaceAttribute>. Bu öznitelik bir proje sistemi desteği için derleme düzeyi özniteliktir ve XAML özel türleri için uygun değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute>  
 [.NET Framework XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
