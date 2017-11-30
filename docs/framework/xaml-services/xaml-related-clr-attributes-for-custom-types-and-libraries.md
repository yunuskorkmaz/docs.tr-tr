---
title: "Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 9a445d7e730ecb743d5e4086ec682b12a7bf3ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri
Bu konuda, .NET Framework XAML Hizmetleri tarafından tanımlanan ortak dil çalışma zamanı (CLR) öznitelikleri açıklanmaktadır. Ayrıca, uygulama türlerini veya derlemeler için XAML ilişkili bir senaryo olan .NET Framework tanımlanan diğer CLR öznitelikleri açıklanmaktadır. Derlemeler, türleri ve üyeleri bu CLR öznitelikleri ile öznitelik atanıyor, türleriyle ilgili XAML tür sistem bilgileri sağlar. XAML düğümü akışı doğrudan işlemek için veya ayrılmış XAML okuyucuları ve XAML yazıcılarının aracılığıyla .NET Framework XAML hizmetleri kullanan tüm XAML tüketici için bilgi sağlanmaktadır.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Özel türler ve özel üyeleri için XAML ilişkili CLR öznitelikleri  
 CLR öznitelikleri kullanarak genel CLR türlerinizi tanımlamak için kullandığınız, aksi takdirde gibi özniteliklere kullanılamaz kapsar. Yedekleme türü tanımlamak için CLR kullanırsanız, .NET Framework XAML Hizmetleri XAML yazarlar tarafından kullanılan varsayılan XAML şema içeriği CLR attribution derlemeleri yedekleme karşı yansıma aracılığıyla okuyabilirsiniz.  
  
 Aşağıdaki bölümlerde, özel türler veya özel üyeler için uygulayabileceğiniz XAML ilgili öznitelikleri açıklanmaktadır. Her CLR özniteliği XAML tür sistemi için ilgili bilgiler iletişim kurar. Yükleme yolu öznitelikli bilgiler, geçerli bir XAML düğümü akışı form XAML okuyucu ya da yardımcı olur veya geçerli bir nesne grafiğinin üretmek XAML yazan yardımcı olur. Kaydetme yolu, öznitelikli bilgilerin XAML türü sistem bilgilerini; reconstitutes geçerli bir XAML düğümü akışı form XAML okuyucu ya da yardımcı olur veya seri hale getirme ipuçlarının ya da XAML yazan veya diğer XAML tüketicileri gereksinimlerini bildirir.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özelliği veya `get` takılabilir özellikleri destekler erişimcisi üyeleri.  
  
 **Bağımsız değişkenler:** yok  
  
 <xref:System.Windows.Markup.AmbientAttribute>özellik veya öznitelikli türüne talepteki tüm özellikleri XAML'de ortam özelliği kavram altında yorumlanması gerektiğini gösterir. XAML işlemcileri üye türü sahipleri nasıl belirlemek için ortam kavram ilişkilendirir. Bir ortam özelliği, değer bir nesne grafiğinin oluştururken, ancak genel tür üyesi arama oluşturulan hemen XAML düğüm kümesi için askıya alınmış ayrıştırıcı bağlamda kullanılabilir olması için beklenirken bir özelliktir.  
  
 Ortam kavram nasıl CLR attribution tanımlar bakımından özellikleri olarak temsil edilmeyen takılabilir üyeleri uygulanabilir <xref:System.AttributeTargets>. Yöntem attribution kullanım yalnızca içinde durumunda, uygulanması gereken bir `get` takılabilir kullanım için XAML destekleyen erişimcisi.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** tek oluşturucu bağımsız değişkeni bir eşleşen özelliğinin adını belirten dize.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>bir nesne varsayılan olmayan Oluşturucusu sözdizimi kullanılarak başlatılabilir ve belirtilen ad özelliği yapım bilgileri sağlayan belirtir. Bu bilgiler, öncelikle XAML serileştirme için olur. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** öznitelikli türünün bir üyesi adını belirten dize.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>adlandırılmış bağımsız değişkeni tarafından olarak özellik türü için XAML içerik özelliği olarak kullanılmalıdır gösterir. Tanımlayıcı türü atanabilir tüm türetilmiş türler için XAML içerik özelliği tanımı devralır. Uygulayarak belirli türetilmiş bir tür tanımı geçersiz kılabilirsiniz <xref:System.Windows.Markup.ContentPropertyAttribute> belirli türetilmiş türü.  
  
 XAML içeriği özelliği olarak hizmet veren özelliği için özellik öğesi özelliği için etiketleme XAML kullanımı atlanabilir. Genellikle, içerik ve kapsama modelleri için kolaylaştırılmış bir XAML biçimlendirme Yükselt XAML İçerik özellikleri belirtin. Yalnızca bir üye XAML içerik özelliği belirlenebilir olduğundan, bazen, birden fazla kapsayıcı türün özelliklerini XAML içerik özelliği olarak belirlenmiş yapmak için tasarım seçeneğiniz vardır. Bir kapsayıcı özellikleri açık özellik öğelerle kullanılması gerekir.  
  
 XAML düğümü akışı XAML İçerik özellikleri hala üretmek `StartMember` ve `EndMember` için özellik adını kullanan düğümleri <xref:System.Xaml.XamlMember>. Üye XAML içerik özelliği olup olmadığını belirlemek için inceleyin <xref:System.Xaml.XamlType> değeri `StartObject` getirin ve değerini edinme <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özellikle koleksiyon türleri.  
  
 **Bağımsız değişkenler:** A <xref:System.Type> yabancı içerik için içerik sarmalayıcı türü olarak kullanılacak türünü belirtir.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>bir veya daha fazla türlerini yabancı içerik sarmalamak için kullanılan ilişkili koleksiyon türünü belirtir. Dış içerik nerede sistem Kısıt türünü içerik özelliğinin türü sahibinin türü için XAML kullanım destekleyecektir olası içerik durumların tümünde yakalamayın çalışmalarını başvurur. Örneğin, XAML destek içerik belirli bir türdeki dizeleri kesin türü belirtilmiş bir genel destekleyebilir <xref:System.Collections.ObjectModel.Collection%601>. İçerik sarmalayıcıları geçirme önceden var olan biçimlendirme kuralları için XAML'ın conception metin ilgili geçirme içerik modelleri gibi koleksiyonlar için atanabilir değerlerin içine faydalıdır.  
  
 Birden fazla içerik sarmalayıcı türünü belirtmek için birden çok kez özniteliğini uygulayın.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Uygulandığı öğe:** özelliği  
  
 **Bağımsız değişkenler:** öznitelikli türünde başka bir üyenin adını belirten dize.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>Öznitelikli özelliği başka bir özellik değerini bağlı olduğunu gösterir. Bu öznitelik için bir özellik tanımını uygulama bağımlı özellikleri XAML nesne yazımda önce işlenir sağlar. Kullanım <xref:System.Windows.Markup.DependsOnAttribute> burada ayrıştırma, belirli bir sırada gelmelidir geçerli nesne oluşturma için türlerinde olağanüstü durumlar özellikleri belirtin.  
  
 Birden çok uygulayabilirsiniz <xref:System.Windows.Markup.DependsOnAttribute> özellik tanımı çalışmalarını.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Uygulandığı öğe:** olması bekleniyor sınıfı bir <xref:System.Windows.Markup.MarkupExtension> türetilmiş türü.  
  
 **Bağımsız değişkenler:** A <xref:System.Type> olarak beklenir en kesin tür belirtiyor `ProvideValue` öznitelikli sonucunu <xref:System.Windows.Markup.MarkupExtension>.  
  
 Daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** attribution iki tür destekler:  
  
-   Öznitelikli türünde bir özellik adını belirten bir dize.  
  
-   Bir özelliğin adını belirten dize ve bir <xref:System.Type> türünün adlandırılmış özelliği tanımlar. Bu form, takılabilir bir üye XAML isim alanı özelliği belirtmek için geçerlidir.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Öznitelikli sınıfı için XAML isim alanı değeri sağlayan bir özellik belirtir. XAML isim alanı özelliği uygulayan bir nesneye başvuru beklenen <xref:System.Windows.Markup.INameScope> ve gerçek XAML isim alanı, depolama ve davranışını tutar.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** öznitelikli türünde çalışma zamanı adı özelliğinin adını belirten dize.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>XAML eşlemeleri öznitelikli türünde bir özellik raporları [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md). Özellik türü olmalıdır <xref:System.String> ve okuma/yazma olmalıdır.  
  
 Tanımlayıcı türü atanabilir tüm türetilmiş türler için tanımı devralır. Uygulayarak belirli türetilmiş bir tür tanımı geçersiz kılabilirsiniz <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> belirli türetilmiş türü.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Uygulandığı öğe:** türleri  
  
 **Bağımsız değişkenler:** yok.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>boşluk önemli içeriği içinde alt öğeleri olarak görünebilir belirli türlerine uygulanır (içeriğe sahip bir koleksiyonun tarafından tutulan <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>Kaydet çoğunlukla geçerlidir, ancak yoludur yükleme yolu XAML türü sistemde bulunan inceleyerek <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Daha fazla bilgi için bkz: [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Başvuru belgeleri:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özelliği, yöntemi (yalnızca XAML geçerli yöntemi durumdur bir `get` takılabilir bir üye destekleyen erişimcisi).  
  
 **Bağımsız değişkenler:** <xref:System.Type> , <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>XAML içinde özel bir bağlam başvuran <xref:System.ComponentModel.TypeConverter>. Bu <xref:System.ComponentModel.TypeConverter> özel türler veya bu türün üyeleri için tür dönüştürme davranış sağlar.  
  
 Uyguladığınız <xref:System.ComponentModel.TypeConverterAttribute> öznitelik türü dönüştürücü uygulamanızı başvuran türünüz için. XAML için tür dönüştürücüleri sınıflar, yapılar veya arabirimler tanımlayabilirsiniz. Numaralandırmalar, tür dönüştürme dönüştürme yerel olarak etkin olduğunu sağlamak gerekmez.  
  
 Tür dönüştürücü hedeflenen hedef türünüz öznitelikleri ya da başlatma metin biçimlendirme için kullanılan bir dizeden dönüştürebilir olmalıdır. Daha fazla bilgi için bkz: [TypeConverters ve XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Bir türdeki tüm değerlere uygulamak yerine XAML için tür dönüştürücü davranış, ayrıca, belirli bir özellik kurulabilir. Bu durumda, uyguladığınız <xref:System.ComponentModel.TypeConverterAttribute> özelliği tanımı (Dış tanımı, özel `get` ve `set` tanımları).  
  
 XAML kullanımı özel takılabilir üyesi için bir tür dönüştürücü davranış uygulayarak atanabilir <xref:System.ComponentModel.TypeConverterAttribute> için `get` XAML kullanımı destekleyen yöntemi erişimcisi.  
  
 Benzer şekilde <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> XAML varlığını önce .NET Framework içinde var ve diğer amaçlar türü dönüştürücü modeli hizmet. Başvuru ve kullanmak için <xref:System.ComponentModel.TypeConverterAttribute>, tam olarak bunu nitelemek veya sağlayan bir `using` bildirimi <xref:System.ComponentModel>. Projenizde sistem derlemesi de dahil etmelisiniz.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** ilgili özellik adıyla başvuran bir dize.  
  
 Bir sınıfın CLR özelliği bu diğer adları gösterir [x: Uid yönergesi](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** bir Boole değeri. Özniteliğin hedeflenen amaç için kullanılan, bu her zaman olarak belirtilmemelidir `true`.  
  
 Bu tür XAML nesne grafik oluşturma sırasında yukarıdan aşağı yerleşik olup olmadığını gösterir. Programlama modeli tanımına büyük olasılıkla yakından ilgili gelişmiş bir kavram olmasıdır. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özelliği, yöntemi (yalnızca XAML geçerli yöntemi durumdur bir `get` takılabilir bir üye destekleyen erişimcisi).  
  
 **Bağımsız değişkenler:** A <xref:System.Type> belirli öznitelikli özelliği veya öznitelikli türü tüm özelliklerde serileştirilirken kullanılacak değer seri hale getirici destek sınıfı belirtir.  
  
 <xref:System.Windows.Markup.ValueSerializer>Daha fazla durum ve içerik daha gerektiren bir değer serileştirme sınıfı belirtir bir <xref:System.ComponentModel.TypeConverter> yapar. <xref:System.Windows.Markup.ValueSerializer>uygulayarak takılabilir bir üyesiyle ilişkili olabilir <xref:System.Windows.Markup.ValueSerializerAttribute> statik öznitelikte `get` takılabilir üye erişimci yöntemi. Değer serileştirme geçerli ayrıca numaralandırmalar, arabirimleri ve yapıları, ancak temsilciler için değil.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özellikle burada boşluk nesne öğelerinin etrafında UI gösterimi için önemli olabilir beklenen karma içeriğini barındırmak için koleksiyon türleri.  
  
 **Bağımsız değişkenler:** yok.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>Koleksiyon türü boşluk önemli XAML düğüm akışın değeri düğümleri koleksiyonundaki yapımı etkileyen bir XAML işlemcisi tarafından işlenmesi gerektiğini gösterir. Daha fazla bilgi için bkz: [XAML'de boşluk işleme](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Uygulandığı öğe:** sınıfı, özellik.  
  
 **Bağımsız değişkenler:** desteklediği iki attribution forms türleri dize olarak veya olarak türleri <xref:System.Type>. Bkz: <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Bir sınıf veya özellik ertelenmiş yük kullanım için XAML (şablon davranışı gibi) sahip ve erteleniyor davranışı ve hedef/içerik türünü sağlayan sınıfı raporlar gösterir.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** geri çağırma adları.  
  
 Bir sınıf biçimlendirme uzantısı bir veya daha fazla özelliği için bir değer sağlamak için kullanabilirsiniz ve XAML yazıcısı sınıfının herhangi bir özellikte biçimlendirme uzantısı kümesi işlemi gerçekleştirmeden önce çağırmalıdır bir işleyici başvuran gösterir.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** geri çağırma adları.  
  
 Bir sınıf türü dönüştürücü bir veya daha fazla özelliği için bir değer sağlamak için kullanabilirsiniz ve XAML yazıcısı sınıfının herhangi bir özellikte türü dönüştürücü ayarlama işlemi gerçekleştirmeden önce çağırmalıdır bir işleyici başvurur gösterir.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Uygulandığı öğe:** sınıfı  
  
 **Bağımsız değişkenler:** diğer özelliğinin adını belirten dize `xml:lang` öznitelikli türü.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>XML eşlemeleri öznitelikli türünde bir özellik raporları `lang` yönergesi. Özellik mutlaka türü değil <xref:System.String>, ancak bir dizeden (bu yapılabilir özelliğin türü ile veya belirli özelliği ile bir tür dönüştürücüsünü ilişkilendirerek) atanabilir. Özelliği okuma/yazma olmalıdır.  
  
 Senaryo eşleme için `xml:lang` , böylelikle bir çalışma zamanı nesne modeli XML belirtilen dil bilgileri ile bir XMLDOM özellikle işlemeden erişebilir.  
  
 Tanımlayıcı türü atanabilir tüm türetilmiş türler için tanımı devralır. Uygulayarak belirli türetilmiş bir tür tanımı geçersiz kılabilirsiniz <xref:System.Windows.Markup.XmlLangPropertyAttribute> , seyrek bir senaryo olsa belirli türetilmiş türünde.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Derleme düzeyinde XAML ilişkili CLR öznitelikleri  
 Aşağıdaki bölümlerde türleri veya üye tanımları için uygulanmaz, ancak bunun yerine derlemeler için uygulanan XAML ilişkili öznitelikleri açıklanmaktadır. Bu öznitelikler XAML'de kullanılacak özel türleri içeren bir kitaplık tanımlama genel amacı için ilgili. Bazı özniteliklerin mutlaka etkisi XAML düğümü akışı doğrudan desteklemez, ancak kullanmak diğer tüketicilerin düğümü akışında geçirilir. Tüketiciler bilgileri için tasarım ortamları veya XAML ad alanı bilgilere gereksinim ve önek bilgi ilişkili seri hale getirme işlemler içerir. (.NET Framework XAML Hizmetleri varsayılan dahil) bir XAML şema içeriği ayrıca bu bilgileri kullanır.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Bağımsız değişkenler:**  
  
-   Sınıflandırılması için XAML ad uzayı tanıtıcısı belirten bir dize.  
  
-   XAML ad alanından önceki bağımsız değişkeni sınıflandırılması XAML ad uzayı tanıtıcısı belirten bir dize.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>XAML ad uzayı tarafından başka bir XAML ad uzayı birden fazla yolu eklendi olduğunu belirtir. Genellikle, subsuming XAML ad uzayı belirtilen önceden tanımlanmış içinde <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Bu teknik olabilir bir Kitaplığı'nda ve önceki sürümü tutulan sözlük karşı önceden tanımlanmış biçimlendirme ile uyumlu hale getirmek için XAML sözlük sürüm oluşturma için kullanılır.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Bağımsız değişkenler:**  
  
-   Tanımlamak için XAML ad uzayı tanıtıcısı belirten bir dize.  
  
-   Bir CLR ad alanı adları bir dize. CLR ad genel türleri, derlemenizi tanımlamanız gerekir ve en az bir CLR ad alanı türleri için XAML kullanım kullanılmaya.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML ad uzayı türü çözümlemesi için XAML nesne yazıcısı ya da XAML şema içeriği tarafından kullanılan sonra bir CLR ad arasındaki derleme başına temelinde bir eşlemeyi belirtir.  
  
 Birden fazla <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bir derlemeye uygulanabilir. Bu, aşağıdaki nedenlerden herhangi bir bileşimini için yapılabilir:  
  
-   Kitaplık tasarımı çalışma zamanı API erişim mantıksal kuruluş için birden çok CLR ad alanını içerir; Ancak, bu ad alanları içindeki tüm türler aynı XAML ad uzayı başvurarak XAML kullanılabilir olmasını istiyorsunuz. Bu durumda, birkaç uygulama <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aynı kullanarak öznitelikleri <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> ancak farklı değer <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> değerleri. Varsayılan XAML ad uzayı ortak kullanımı olacak şekilde framework veya uygulama oranla XAML ad uzayı eşlemelerini tanımlıyorsanız, bu özellikle yararlıdır.  
  
-   Bu CLR ad alanlarında türleri kullanımları arasında bilinçli bir XAML ad alanı ayırmayı istediğiniz ve kitaplık tasarımı birden çok CLR ad alanları içerir.  
  
-   Birden fazla XAML ad alanı aracılığıyla erişilebilir olmasını istiyorsanız ve bütünleştirilmiş kodunda bir CLR ad tanımlayın. Bu senaryo, aynı kod temeli ile birden çok sözcük dağarcıklarını desteklediğiniz oluşur.  
  
-   XAML dil desteği bir veya daha fazla CLR ad alanları tanımlayın. Bu, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değeri `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Bağımsız değişkenler:**  
  
-   XAML ad uzayı tanıtıcısı belirten bir dize.  
  
-   Önerilen bir önek belirten bir dize.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML ad uzayı için kullanılacak önerilen önek belirtir. Öğeleri ve öznitelikleri .NET Framework XAML Hizmetleri tarafından seri hale getirilmiş bir XAML dosyasına yazılırken öneki yararlıdır <xref:System.Xaml.XamlXmlWriter>, veya ne zaman bir XAML uygulama kitaplığı, XAML olan bir tasarım ortamında ile etkileşim düzenleme özellikleri.  
  
 Birden fazla <xref:System.Windows.Markup.XmlnsPrefixAttribute> bir derlemeye uygulanabilir. Bu, aşağıdaki nedenlerden herhangi bir bileşimini için yapılabilir:  
  
-   Derlemenizi türleri için birden fazla XAML ad uzayı tanımlar. Bu durumda her XAML ad alanı için farklı önek değerleri tanımlamanız gerekir.  
  
-   Birden çok sözcük dağarcıklarını destekleyen ve her bir sözlük ve XAML ad uzayı için farklı önekleri kullanın.  
  
-   XAML dil desteği derlemede tanımlamasına ve bir <xref:System.Windows.Markup.XmlnsDefinitionAttribute> için `http://schemas.microsoft.com/winfx/2006/xaml`. Bu durumda, genellikle önekini Yükselt `x`.  
  
> [!NOTE]
>  .NET framework XAML hizmetleri de XAML ilişkili öznitelik tanımlar <xref:System.Windows.Markup.RootNamespaceAttribute>. Bu öznitelik bir proje sistem desteği için derleme düzeyi özniteliktir ve XAML özel türler için ilgili değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute>  
 [.NET Framework XAML Hizmetleri ile kullanmak için özel türleri tanımlama](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
