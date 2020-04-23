---
title: Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071768"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Özel türleri ve kitaplıkları için XAML ile ilgili CLR öznitelikleri

Bu konu, .NET XAML Hizmetleri tarafından tanımlanan ortak dil çalışma zamanı (CLR) özniteliklerini açıklar. Ayrıca, derlemelere veya türlere uygulama için XAML ile ilgili bir senaryosu olan .NET'te tanımlanan diğer CLR özniteliklerini de açıklar. Bu CLR özniteliklerine sahip derlemelere, türlere veya üyelere atfetmek, türlerinize ilişkin XAML türü sistem bilgilerini sağlar. Bilgi doğrudan veya özel XAML okuyucuları ve XAML yazarlar aracılığıyla XAML düğüm akışı işlemek için .NET XAML Hizmetleri kullanan herhangi bir XAML tüketici sağlanmaktadır.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Özel Türleri ve Özel Üyeler için XAML Ile İlgili CLR Öznitelikleri

CLR özniteliklerini kullanmak, türlerinizi tanımlamak için genel CLR'yi kullandığınızı, aksi takdirde bu tür özniteliklerin kullanılamamasını gerektirir. ClR'yi tür desteğini tanımlamak için kullanırsanız, .NET XAML Services XAML yazarları tarafından kullanılan varsayılan XAML şeması bağlamı, destek derlemelerine karşı yansıma yoluyla CLR atıfını okuyabilir.

Aşağıdaki bölümler, özel türlere veya özel üyelere uygulayabileceğiniz XAML ile ilgili öznitelikleri açıklar. Her CLR özniteliği, XAML türü sistemiyle ilgili bilgileri iletir. Yük yolunda, atfedilen bilgiler XAML okuyucusunun geçerli bir XAML düğüm akışı oluşturmasına veya XAML yazarının geçerli bir nesne grafiği oluşturmasına yardımcı olur. Kaydetme yolunda, atfedilen bilgiler XAML okuyucusunun XAML türü sistem bilgilerini yeniden oluşturan geçerli bir XAML düğüm akışı oluşturmasına yardımcı olur; veya XAML yazarı veya diğer XAML tüketicileri için serileştirme ipuçları veya gereksinimleri bildirir.

### <a name="ambientattribute"></a>Ambientattribute

**Referans Belgeleri:**<xref:System.Windows.Markup.AmbientAttribute>

**Aşağıdakiler için geçerlidir:** Eklenebilir özellikleri `get` destekleyen sınıf, özellik veya erişimci üyeler.

**Bağımsız değişkenler:** Hiçbiri

<xref:System.Windows.Markup.AmbientAttribute>özelliğin veya atfedilen türü alan tüm özelliklerin XAML'deki ortam özelliği kavramı altında yorumlanması gerektiğini gösterir. Ortam kavramı, XAML işlemcilerin üyelerin tür sahiplerini nasıl belirlediğiyle ilgilidir. Ortam özelliği, nesne grafiği oluşturulurken değerin ayrıştırıcı bağlamında bulunmasının beklendiği, ancak oluşturulan hemen XAML düğüm kümesi için tipik tür üyesi aramasının askıya alındığı bir özelliktir.

Ortam kavramı, CLR atıfının tanımladığı gibi özellikler olarak temsil edilmeyen eklenebilir üyelere <xref:System.AttributeTargets>uygulanabilir. Yöntem atıf kullanımı yalnızca XAML `get` için takılabilir kullanımı destekleyen bir erişimci için uygulanmalıdır.

### <a name="constructorargumentattribute"></a>Constructorargumentattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Tek bir oluşturucu bağımsız değişkenle eşleşen özelliğin adını belirten bir dize.

<xref:System.Windows.Markup.ConstructorArgumentAttribute>bir nesnenin parametresiz olmayan bir yapı oluşturucu sözdizimi kullanılarak başharflere alınabileceğini ve belirtilen adın bir özelliğinin inşaat bilgilerini sağladığını belirtir. Bu bilgiler öncelikle XAML serileştirme içindir. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>Contentpropertyattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Atfedilen türden bir üyenin adını belirten bir dize.

<xref:System.Windows.Markup.ContentPropertyAttribute>bağımsız değişken tarafından adlandırılmış özelliğin bu tür için XAML içerik özelliği olarak hizmet vermesi gerektiğini gösterir. XAML içerik özelliği tanımı, tanımlayıcı türe atabilen tüm türlere devralınır. Belirli türemiş <xref:System.Windows.Markup.ContentPropertyAttribute> türe uygulayarak tanımı belirli bir türetilmiş türde geçersiz kılabilirsiniz.

XAML içerik özelliği olarak hizmet veren özellik için, özellik için etiketleme özellik öğesi XAML kullanımında atlanabilir. Tipik olarak, içeriğiniz ve kapsama modelleriniz için kolaylaştırılmış XAML biçimlendirmesi tanıtan XAML içerik özelliklerini belirlersiniz. Yalnızca bir üye XAML içerik özelliği olarak atanabildiği için, bazen bir türün birkaç kapsayıcı özelliğinden hangisinin XAML içerik özelliği olarak atanması gerektiğine ilişkin tasarım seçenekleriniz vardır. Diğer kapsayıcı özellikleri açık özellik öğeleri ile kullanılmalıdır.

XAML düğüm akışında, XAML içerik `StartMember` özellikleri `EndMember` hala üretmek ve düğümleri, için <xref:System.Xaml.XamlMember>özelliğin adını kullanarak . Bir üyenin XAML içerik özelliği olup <xref:System.Xaml.XamlType> olmadığını belirlemek `StartObject` için, konumdaki <xref:System.Xaml.XamlType.ContentProperty%2A>değeri inceleyin ve değerini elde edin.

### <a name="contentwrapperattribute"></a>Contentwrapperattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**Aşağıdakiler için geçerlidir:** Sınıf, özellikle toplama türleri.

**Bağımsız değişkenler:** Yabancı <xref:System.Type> içerik için içerik sarıcı türü olarak kullanılacak türü belirten bir tür.

<xref:System.Windows.Markup.ContentWrapperAttribute>yabancı içeriği sarmak için kullanılacak ilişkili koleksiyon türünde bir veya daha fazla tür belirtir. Yabancı içerik, içerik özelliğinin türündeki tür sistemi kısıtlamalarının, sahip sahibi türü için XAML kullanımının destekleyeceği olası içerik örneklerinin tümlerini yakalamadığı durumlar anlamına gelir. Örneğin, belirli bir tür içeriği için XAML desteği güçlü bir şekilde <xref:System.Collections.ObjectModel.Collection%601>yazılan genel dizeleri destekleyebilir. İçerik paketleyicileri, metinle ilgili içerik modellerini geçirme gibi, önceden varolan biçimlendirme kurallarını XAML'ın koleksiyonlar için atabilen değerler anlayışına geçirmek için yararlıdır.

Birden fazla içerik sarıcı türü belirtmek için özniteliği birden çok kez uygulayın.

### <a name="dependsonattribute"></a>Bağlı Bağlı

**Referans Belgeleri:**  <xref:System.Windows.Markup.DependsOnAttribute>

**Aşağıdakiler için geçerlidir:** Özellik

**Bağımsız değişkenler:** Atfedilen türün başka bir üyesinin adını belirten bir dize.

<xref:System.Windows.Markup.DependsOnAttribute>atfedilen özelliğin başka bir özelliğin değerine bağlı olduğunu gösterir. Bu özniteliği bir özellik tanımına uygulamak, bağımlı özelliklerin ilk olarak XAML nesne yazımında işlenmesini sağlar. Geçerli nesne <xref:System.Windows.Markup.DependsOnAttribute> oluşturma için belirli bir ayrıştırma sırasının izlenmesi gereken türlerdeki istisnai özellikler in kullanımları.

Birden çok <xref:System.Windows.Markup.DependsOnAttribute> servis örneğini özellik tanımına uygulayabilirsiniz.

### <a name="markupextensionreturntypeattribute"></a>Markupextensionreturntypeattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**Aşağıdakiler için geçerlidir:** Türemiş bir <xref:System.Windows.Markup.MarkupExtension> tür olması beklenen sınıf.

**Bağımsız değişkenler:** Atfedilen <xref:System.Type> `ProvideValue` <xref:System.Windows.Markup.MarkupExtension>sonucu olarak beklenebilir en kesin türü belirtir .

Daha fazla bilgi [için XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.

### <a name="namescopepropertyattribute"></a>Namescopepropertyattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** İki tür atıfta bulunmayı destekler:

- Atfedilen türdeki bir özelliğin adını belirten dize.

- Bir özelliğin adını belirten bir dize <xref:System.Type> ve adlandırılmış özelliği tanımlayan tür için bir dize. Bu form, XAML adayır özelliği olarak eklenebilir bir üye belirtmek içindir.

<xref:System.Windows.Markup.NameScopePropertyAttribute>atfedilen sınıf için XAML adskop değeri sağlayan bir özellik belirtir. XAML adskop özelliğinin gerçek XAML <xref:System.Windows.Markup.INameScope> adskopunu, deposunu ve davranışını uygulayan ve tutan bir nesneye başvurması beklenir.

### <a name="runtimenamepropertyattribute"></a>Runtimenamepropertyattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Atfedilen türde çalışma zamanı adı özelliğinin adını belirten bir dize.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>XAML [x:Ad Yönergesi](xname-directive.md)ile eşleyen atfedilen türün bir özelliğini bildirir. Özellik türde <xref:System.String> olmalı ve okuma/yazma olmalıdır.

Tanım, tanımlayıcı türe atabilen tüm türlere devralınır. Belirli türemiş <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> türe uygulayarak tanımı belirli bir türetilmiş türde geçersiz kılabilirsiniz.

### <a name="trimsurroundingwhitespaceattribute"></a>Trimsurroundingwhitespaceattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**Aşağıdakiler için geçerlidir:** Tür

**Bağımsız değişkenler:** Hiçbiri.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>beyaz alan önemli içerik (içerik olan <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>bir koleksiyon tarafından düzenlenen) içinde alt öğeler olarak görünebilir belirli türlere uygulanır. <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>çoğunlukla kaydet yolu ile ilgilidir, ancak xaml tipi sistemde yük yolunda <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>inceleyerek kullanılabilir. Daha fazla bilgi için [XAML'deki Beyaz alan işleme](white-space-processing.md)ye bakın.

### <a name="typeconverterattribute"></a>Typeconverterattribute

**Referans Belgeleri:**  <xref:System.ComponentModel.TypeConverterAttribute>

**Aşağıdakiler için geçerlidir:** Sınıf, özellik, yöntem (yalnızca XAML geçerliliği `get` olan yöntem örneği, takılabilir bir üyeyi destekleyen bir erişimcidir).

**Bağımsız değişkenler:** Bunun <xref:System.Type> gibi <xref:System.ComponentModel.TypeConverter>bir şey.

<xref:System.ComponentModel.TypeConverterAttribute>Bir XAML bağlamında özel <xref:System.ComponentModel.TypeConverter>bir başvurur. Bu, <xref:System.ComponentModel.TypeConverter> özel türler veya bu tür üyeleri için tür dönüştürme davranışı sağlar.

<xref:System.ComponentModel.TypeConverterAttribute> Tür dönüştürücü uygulamabaşvurarak, türüne öznitelik uygulayın. Sınıflarda, yapılarda veya arabirimlerde XAML için tür dönüştürücüler tanımlayabilirsiniz. Sayısallaştırmalar için tür dönüştürmesi sağlamanız gerekmez, bu dönüştürme yerel olarak etkinleştirilir.

Tür dönüştürücünüz, işaretlemedeki öznitelikler veya başlatma metni için kullanılan bir dizeden hedeflenen hedef türünüze dönüştürebilmeli. Daha fazla bilgi için [TypeConverters ve XAML'ye](../../framework/wpf/advanced/typeconverters-and-xaml.md)bakın.

Bir türün tüm değerlerine başvurmak yerine, belirli bir özellik üzerinde XAML için bir tür dönüştürücü davranışı da oluşturulabilir. Bu durumda, özellik <xref:System.ComponentModel.TypeConverterAttribute> tanımına (belirli ve `get` `set` tanımları değil dış tanım) uygulanır.

XAML kullanımını destekleyen <xref:System.ComponentModel.TypeConverterAttribute> `get` yöntem aksesuarına uygulanarak, özel bir eklenebilir üyenin XAML kullanımı için bir tür dönüştürücü davranışı atanabilir.

<xref:System.ComponentModel.TypeConverter>XAML'nin varlığından önce .NET'te <xref:System.ComponentModel.TypeConverterAttribute> var olan benzer ve tür dönüştürücü modeli başka amaçlara hizmet etti. Başvuru ve kullanım <xref:System.ComponentModel.TypeConverterAttribute>için, tam olarak nitelemek `using` veya <xref:System.ComponentModel>için bir ifade sağlamak gerekir. Projenize Sistem derlemesini de ekleyin.

### <a name="uidpropertyattribute"></a>Uidpropertyattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** İlgili özelliğe ada göre başvuran bir dize.

[X:Uid](xuid-directive.md)Yönergesi'ni diğer adlayan bir sınıfın CLR özelliğini gösterir.

### <a name="usableduringinitializationattribute"></a>Usableduringınitializationattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Bir Boolean. Özniteliğin amaçlanan amacı için kullanılırsa, değer `true`.

XAML nesne grafiği oluşturma sırasında türün yukarıdan aşağıya oluşturulup oluşturulmadığını gösterir. Bu, muhtemelen programlama modelinizin tanımıyla yakından ilişkili olan gelişmiş bir kavramdır. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>Valueserializerattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**Aşağıdakiler için geçerlidir:** Sınıf, özellik, yöntem (yalnızca XAML geçerliliği `get` olan yöntem örneği, takılabilir bir üyeyi destekleyen bir erişimcidir).

**Bağımsız değişkenler:** Atfedilen <xref:System.Type> türün tüm özelliklerini veya belirli atfedilen özelliği serihale ederken kullanılacak değer serileştirici destek sınıfını belirten bir değer.

<xref:System.Windows.Markup.ValueSerializer>bir değer serileştirme sınıfı, bir değerden daha <xref:System.ComponentModel.TypeConverter> fazla durum ve bağlam gerektiren bir değer serileştirme sınıfı belirtir. <xref:System.Windows.Markup.ValueSerializer>eklenebilir üye için statik <xref:System.Windows.Markup.ValueSerializerAttribute> `get` erişimci yöntemine öznitelik uygulanarak eklenebilir bir üye ile ilişkilendirilebilir. Değer serileştirme, sayısallaştırmalar, arabirimler ve yapılar için de geçerlidir, ancak temsilciler için geçerli değildir.

### <a name="whitespacesignificantcollectionattribute"></a>Whitespacesignificantcollectionattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**Aşağıdakiler için geçerlidir:** Sınıf, özellikle nesne öğeleri etrafında beyaz boşluk UI gösterimi için önemli olabilir karışık içerik barındırmak için beklenen toplama türleri.

**Bağımsız değişkenler:** Hiçbiri.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>bir koleksiyon türünün, koleksiyoniçindeki XAML düğümünin değer düğümlerinin yapımını etkileyen bir XAML işlemci tarafından önemli ölçüde beyaz boşluk olarak işlenmesi gerektiğini gösterir. Daha fazla bilgi için [XAML'deki Beyaz alan işleme](white-space-processing.md)ye bakın.

### <a name="xamldeferloadattribute"></a>Xamldeferloadattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**Aşağıdakiler için geçerlidir:** Sınıf, mülk.

**Bağımsız değişkenler:** Dize olarak iki atıf formları türleri destekler <xref:System.Type>veya türleri gibi . Bkz. <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Bir sınıfın veya özelliğin XAML (şablon davranışı gibi) için ertelenmiş bir yük kullanımına sahip olduğunu gösterir ve erteleme davranışını ve hedef/içerik türünü etkinleştiren sınıfı raporlar.

### <a name="xamlsetmarkupextensionattribute"></a>Xamlsetmarkupextensionattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Geri aramanın adını vereb.

Bir sınıfın özelliklerinden biri veya daha fazlası için değer sağlamak için biçimlendirme uzantısı kullanabileceğini gösterir ve sınıfın herhangi bir özelliği üzerinde biçimlendirme uzantısı kümesi işlemi gerçekleştirmeden önce bir XAML yazarının araması gereken bir işleyiciye başvurur.

### <a name="xamlsettypeconverterattribute"></a>Xamlsettypeconverterattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Geri aramanın adını vereb.

Bir sınıfın, özelliklerinden biri veya daha fazlası için değer sağlamak için bir tür dönüştürücü sevesi kullanabileceğini gösterir ve sınıfın herhangi bir özelliğiüzerinde bir tür dönüştürücü kümesi çalışması gerçekleştirmeden önce bir XAML yazarının araması gereken bir işleyiciye başvurur.

### <a name="xmllangpropertyattribute"></a>Xmllangpropertyattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**Aşağıdakiler için geçerlidir:** Sınıfı

**Bağımsız değişkenler:** Özellik adını atfedilen türde takma ad `xml:lang` olarak belirten bir dize.

<xref:System.Windows.Markup.XmlLangPropertyAttribute>XML `lang` yönergesine eşleyen atfedilen türdeki bir özelliği bildirir. Özellik mutlaka tür <xref:System.String> de değildir, ancak bir dizeden atanabilir olmalıdır (atama, bir tür dönüştürücüsünün özelliğin türüyle veya belirli özelliğiyle ilişkilendirilerek gerçekleştirilebilir). Özellik okuma/yazma olmalıdır.

Eşleme `xml:lang` senaryosu, çalışma zamanı nesne modelinin xmldom ile özel olarak işlenmeden XML tarafından belirtilen dil bilgilerine erişebilmesidir.

Tanım, tanımlayıcı türe atabilen tüm türlere devralınır. Nadir bir senaryo olmasına rağmen, belirli türetilmiş <xref:System.Windows.Markup.XmlLangPropertyAttribute> türe uygulayarak tanımı belirli bir türetilmiş türde geçersiz kılabilirsiniz.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Montaj Düzeyinde XAML Ile İlgili CLR Öznitelikleri

Aşağıdaki bölümlerde, türlere veya üye tanımlara uygulanmayan, bunun yerine derlemelere uygulanan XAML ile ilgili öznitelikleri açıklanmaktadır. Bu öznitelikler, XAML'de kullanılacak özel türleri içeren bir kitaplık tanımlamanın genel hedefiyle ilgilidir. Bazı öznitelikler xaml düğüm akışını doğrudan etkilemez, ancak diğer tüketicilerin kullanması için düğüm akışına aktarılır. Bilgi için tüketiciler, XAML ad alanı bilgileri ve ilişkili önek bilgileri ne ihtiyaç duyan tasarım ortamlarını veya serileştirme işlemlerini içerir. Bir XAML şeması bağlamı (.NET XAML Hizmetleri varsayılanı dahil) da bu bilgileri kullanır.

### <a name="xmlnscompatiblewithattribute"></a>Xmlnscompatiblewithattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Bağımsız değişken:**

- XAML ad alanının tanımlayıcısını subsume olarak belirten bir dize.

- XAML ad alanının tanımlayıcısını belirten ve XAML ad alanını önceki bağımsız değişkenden suylayabilen dize.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>bir XAML ad alanının başka bir XAML ad alanı tarafından alt toplamına alınabileceğini belirtir. Genellikle, alt toplamxaml ad alanı daha önce tanımlanmış <xref:System.Windows.Markup.XmlnsDefinitionAttribute>bir . Bu teknik, bir kitaplıkta xaml kelime sürümü ve önceki sürümdeki kelime karşı daha önce tanımlanmış biçimlendirme ile uyumlu hale getirmek için kullanılabilir.

### <a name="xmlnsdefinitionattribute"></a>Xmlnsdefinitionattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Bağımsız değişken:**

- Tanımlamak için XAML ad alanının tanımlayıcısını belirten bir dize.

- CLR ad alanı adını veren bir dize. CLR ad alanı derlemenizde ortak türleri tanımlamalı ve CLR ad alanı türlerinden en az biri XAML kullanımı için tasarlanmalıdır.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>bir XAML ad alanı ile CLR ad alanı arasında montaj başına eşleme belirtir ve bu eşleme, daha sonra bir XAML nesne yazarı veya XAML şema bağlamı tarafından tür çözümü için kullanılır.

  Bir derlemeye birden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> fazla uygulanabilir. Bu, aşağıdaki nedenlerden herhangi biri için yapılabilir:

- Kitaplık tasarımı, çalışma zamanı API erişiminin mantıksal organizasyonu için birden çok CLR ad alanı içerir; ancak, bu ad alanlarındaki tüm türlerin aynı XAML ad alanına başvurarak XAML'de kullanılabilir olmasını istiyorsunuz. Bu durumda, aynı <xref:System.Windows.Markup.XmlnsDefinitionAttribute> <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değeri ancak farklı <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> değerleri kullanarak birkaç öznitelikleri uygularsınız. Bu, özellikle, çerçevenizin veya uygulamanızın ortak kullanımda varsayılan XAML ad alanı olmayı amaçladığını niçin XAML ad alanı için eşlemeler tanımlıyorsanız kullanışlıdır.

- Kitaplık tasarımı birden çok CLR ad alanı içerir ve bu CLR ad alanlarındaki türlerin kullanımları arasında kasıtlı bir XAML ad alanı ayrımı istiyorsunuz.

- Derlemede bir CLR ad alanı tanımlarsınız ve birden fazla XAML ad alanı üzerinden erişilebilir olmasını istersiniz. Bu senaryo, aynı kod tabanıile birden çok kelime yi destekliyorsanız oluşur.

- XAML dil desteğini bir veya daha fazla CLR ad alanında tanımlarsınız. Bu durumda, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değer . `http://schemas.microsoft.com/winfx/2006/xaml`

### <a name="xmlnsprefixattribute"></a>Xmlnsprefixattribute

**Referans Belgeleri:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Bağımsız değişken:**

- XAML ad alanının tanımlayıcısını belirten bir dize.

- Önerilen önek belirten bir dize.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML ad alanı için kullanılacak önerilen bir önek belirtir. Önek, .NET XAML Hizmetleri <xref:System.Xaml.XamlXmlWriter>tarafından seri hale getirilen bir XAML dosyasındaki öğeleri ve öznitelikleri yazarken veya XAML uygulama kitaplığı XAML düzenleme özelliklerine sahip bir tasarım ortamıyla etkileşime girdiğinde yararlıdır.

  Bir derlemeye birden <xref:System.Windows.Markup.XmlnsPrefixAttribute> fazla uygulanabilir. Bu, aşağıdaki nedenlerden herhangi biri için yapılabilir:

- Derlemeniz birden fazla XAML ad alanı için türleri tanımlar. Bu durumda, her XAML ad alanı için farklı önek değerleri tanımlayın.

- Birden çok kelime dağarcığı nızı destekliyorsunuz ve her sözcük dağarcığı ve XAML ad alanı için farklı önekler kullanıyorsunuz.

- Derlemede XAML dil desteğini tanımlarsınız <xref:System.Windows.Markup.XmlnsDefinitionAttribute> `http://schemas.microsoft.com/winfx/2006/xaml`ve için bir . Bu durumda, genellikle önek `x`tanıtmalısınız.

> [!NOTE]
> .NET XAML Hizmetleri de XAML ile <xref:System.Windows.Markup.RootNamespaceAttribute>ilgili özniteliği tanımlar. Bu öznitelik, proje sistemi desteği için montaj düzeyinde bir özniteliktir ve XAML özel türleri için geçerli değildir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- [.NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](define-custom-types.md)
