---
title: Özel Türler ve Kitaplıkar İçin XAML İlişkili CLR Öznitelikleri
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535403"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Özel türler ve kitaplıklar için XAML ile ilgili CLR öznitelikleri

Bu konuda, .NET XAML Hizmetleri tarafından tanımlanan ortak dil çalışma zamanı (CLR) öznitelikleri açıklanmaktadır. Ayrıca, uygulamalar için derlemeler veya türler için XAML ile ilgili bir senaryoya sahip .NET 'te tanımlanan diğer CLR özniteliklerini açıklar. Bu CLR özniteliklerine sahip Attributing derlemeleri, türleri veya üyeleri, türleriniz ile ilgili XAML türü sistem bilgilerini sağlar. Bilgiler XAML düğüm akışını doğrudan veya adanmış XAML okuyucular ve XAML yazarları aracılığıyla işlemek için .NET XAML Hizmetleri kullanan tüm XAML tüketicisine sağlanır.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Özel türler ve özel Üyeler için XAML ile Ilgili CLR öznitelikleri

CLR özniteliklerinin kullanılması, türlerinizi tanımlamak için genel CLR 'yi kullanmanızı gerektirir, aksi takdirde bu tür öznitelikler kullanılamaz. Tür yedeklemesini tanımlamak için CLR kullanırsanız, .NET XAML Hizmetleri XAML yazarları tarafından kullanılan varsayılan XAML şeması bağlamı, derlemeleri yedeklemeye karşı yansıma aracılığıyla CLR atışı okuyabilir.

Aşağıdaki bölümlerde, özel türlere veya özel üyelere uygulayabileceğiniz XAML ile ilgili öznitelikler açıklanır. Her CLR özniteliği bir XAML tür sistemiyle ilgili bilgileri iletişim kurar. Yükleme yolunda, öznitelikli bilgiler XAML okuyucunun geçerli bir XAML düğüm akışı biçimine yardımcı olur ya da XAML yazıcısının geçerli bir nesne grafiği üretmesine yardımcı olur. Kayıt yolunda, öznitelikli bilgiler XAML okuyucusuna reconstitutes XAML türü sistem bilgileri olan geçerli bir XAML düğüm akışı biçimine yardımcı olur. ya da XAML yazıcı veya diğer XAML tüketicileri için serileştirme ipuçları veya gereksinimler bildirir.

### <a name="ambientattribute"></a>AmbientAttribute

**Başvuru belgeleri:**<xref:System.Windows.Markup.AmbientAttribute>

**Uygulama hedefi:** Eklenebilir özellikleri destekleyen sınıf, özellik veya `get` erişimci üyeleri.

**Bağımsız değişkenler:** Seçim

<xref:System.Windows.Markup.AmbientAttribute> özelliğin veya öznitelikli türü alan tüm özelliklerin XAML 'deki çevresel Özellik kavramı altında yorumlanması gerektiğini gösterir. Çevresel kavram, XAML işlemcilerin üye tür sahiplerini nasıl belirlemeleriyle ilgilidir. Ambient özelliği, bir nesne grafiği oluştururken değerin ayrıştırıcı bağlamında kullanılabilir olması beklenen bir özelliktir, ancak normal tür-üye aramasının oluşturulan hemen XAML düğüm kümesi için askıya alındığı yer.

Çevresel kavram, CLR atışının nasıl tanımladığına ilişkin özellikler olarak temsil edilmeyen eklenebilir üyelere uygulanabilir <xref:System.AttributeTargets> . Yöntem attributıon kullanımı, yalnızca `get` XAML için eklenebilir kullanımı destekleyen bir erişimci için uygulanmalıdır.

### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Tek bir Oluşturucu bağımsız değişkeniyle eşleşen özelliğin adını belirten bir dize.

<xref:System.Windows.Markup.ConstructorArgumentAttribute> bir nesnenin parametresiz bir Oluşturucu sözdizimi kullanılarak başlatıla, ve belirtilen adın bir özelliğinin ise oluşturma bilgilerini sağladığı belirtir. Bu bilgiler öncelikle XAML serileştirme içindir. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>ContentPropertyAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Öznitelikli türdeki bir üyenin adını belirten bir dize.

<xref:System.Windows.Markup.ContentPropertyAttribute> bağımsız değişken tarafından adlandırılan özelliğin, bu tür için XAML içerik özelliği olarak işlev görmesi gerektiğini gösterir. XAML içerik özelliği tanımı, tanımlama türüne atanabilen tüm türetilmiş türlere devralınır. Belirli türetilmiş tür üzerine uygulayarak, belirli bir türetilmiş tür üzerinde tanımlamayı geçersiz kılabilirsiniz <xref:System.Windows.Markup.ContentPropertyAttribute> .

XAML içerik özelliği olarak hizmet veren özelliği için, özelliği için özellik öğesi etiketleme XAML kullanımında atlanabilir. Genellikle, içerik ve kapsama modelleriniz için kolaylaştırılmış XAML işaretlemesini yükselterek XAML içerik özelliklerini belirlersiniz. Yalnızca bir üye XAML içerik özelliği olarak atanabileceğinden, bazen bir türün çeşitli kapsayıcı özelliklerinden hangisinin XAML içerik özelliği olarak belirlenmesi gerektiğine ilişkin tasarım seçimlerine sahip olursunuz. Diğer kapsayıcı özelliklerinin açık özellik öğeleriyle kullanılması gerekir.

XAML düğüm akışında XAML içerik özellikleri, `StartMember` `EndMember` için özelliğinin adını kullanarak hala ve düğümleri üretir <xref:System.Xaml.XamlMember> . Bir üyenin XAML içerik özelliği olup olmadığını anlamak için, <xref:System.Xaml.XamlType> konumundan değeri inceleyin `StartObject` ve değerini alın <xref:System.Xaml.XamlType.ContentProperty%2A> .

### <a name="contentwrapperattribute"></a>ContentWrapperAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**Uygulama hedefi:** Sınıf, özellikle koleksiyon türleri.

**Bağımsız değişkenler:** <xref:System.Type> Yabancı içerik için içerik sarmalayıcı türü olarak kullanılacak türü belirten bir.

<xref:System.Windows.Markup.ContentWrapperAttribute> yabancı içeriği kaydırmak için kullanılacak, ilişkili koleksiyon türünde bir veya daha fazla türü belirtir. Yabancı içerik özelliği, içerik özelliğinin türü sistem kısıtlamalarının, sahip olan türdeki XAML kullanımının desteklediği tüm olası içerik durumlarını yakalamamasıdır. Örneğin, belirli bir türün içeriği için XAML desteği, kesin tür belirtilmiş bir genel içindeki dizeleri destekleyebilir <xref:System.Collections.ObjectModel.Collection%601> . İçerik sarmalayıcıları, önceden var olan biçimlendirme kurallarını XAML için, metin ile ilgili içerik modellerini geçirme gibi, koleksiyonlara yönelik atanabilir değerlerin daha da bu şekilde geçirilmesi için yararlıdır.

Birden fazla içerik sarmalayıcı türü belirtmek için, özniteliği birden çok kez uygulayın.

### <a name="dependsonattribute"></a>Bağımlıdsonattribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.DependsOnAttribute>

**Uygulama hedefi:** Özelliði

**Bağımsız değişkenler:** Öznitelikli türdeki başka bir üyenin adını belirten bir dize.

<xref:System.Windows.Markup.DependsOnAttribute> Öznitelikli özelliğin başka bir özelliğin değerine bağlı olduğunu gösterir. Bu özniteliği bir özellik tanımına uygulamak, bağımlı özelliklerin öncelikle XAML nesne yazma içinde işlenmesini sağlar. <xref:System.Windows.Markup.DependsOnAttribute>Belirli bir ayrıştırma sırasının geçerli nesne oluşturmak için izlenmesi gereken türlerin özelliklerinin olağanüstü durumlarını belirtme kullanımları.

<xref:System.Windows.Markup.DependsOnAttribute>Bir özellik tanımına birden çok durum uygulayabilirsiniz.

### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**Uygulama hedefi:** Türetilmiş bir tür olması beklenen sınıf <xref:System.Windows.Markup.MarkupExtension> .

**Bağımsız değişkenler:** <xref:System.Type> Bu, öznitelik sonucu olarak beklenen kesin türü belirten bir `ProvideValue` <xref:System.Windows.Markup.MarkupExtension> .

Daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** İki tür atısyonu destekler:

- Öznitelikli türdeki bir özelliğin adını belirten bir dize.

- Bir özelliğin adını belirten bir dize ve <xref:System.Type> adlandırılmış özelliği tanımlayan tür için. Bu form, XAML namescope özelliği olarak eklenebilir bir üye belirtmek içindir.

<xref:System.Windows.Markup.NameScopePropertyAttribute> Öznitelikli sınıf için XAML namescope değerini sağlayan bir özelliği belirtir. XAML namescope özelliğinin <xref:System.Windows.Markup.INameScope> , gerçek xaml namescope, mağazasının ve davranışını uygulayan ve tutan bir nesneye başvurması beklenir.

### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Öznitelikli türdeki çalışma zamanı adı özelliğinin adını belirten bir dize.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> XAML [X:Name yönergesiyle](xname-directive.md)eşleşen öznitelikli türün bir özelliğini raporlar. Özellik türünde olmalı <xref:System.String> ve okuma/yazma olmalıdır.

Tanım, tanımlama türüne atanabilen tüm türetilmiş türlere devralınır. Belirli türetilmiş tür üzerine uygulayarak, belirli bir türetilmiş tür üzerinde tanımlamayı geçersiz kılabilirsiniz <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> .

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**Uygulama hedefi:** Türü

**Bağımsız değişkenler:** Seçim.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> , boşluk açısından önemli içerik (sahip olan bir koleksiyon tarafından tutulan içerik) içinde alt öğe olarak görünebilen belirli türlere uygulanır <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> . <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> genellikle kaydetme yoluyla ilgilidir, ancak inceleyerek yükleme yolundaki XAML tür sisteminde kullanılabilir <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [xaml 'de beyaz boşluk işleme](white-space-processing.md).

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**Başvuru belgeleri:**  <xref:System.ComponentModel.TypeConverterAttribute>

**Uygulama hedefi:** Class, Property, Method (tek XAML-geçerli yöntem durumu `get` eklenebilir bir üyeyi destekleyen bir erişimdir).

**Bağımsız değişkenler:** <xref:System.Type> Öğesinin <xref:System.ComponentModel.TypeConverter> .

<xref:System.ComponentModel.TypeConverterAttribute> XAML bağlamında özel bir başvurusu vardır <xref:System.ComponentModel.TypeConverter> . Bu <xref:System.ComponentModel.TypeConverter> , özel türler veya bu türdeki Üyeler için tür dönüştürme davranışı sağlar.

Türüne <xref:System.ComponentModel.TypeConverterAttribute> , tür dönüştürücü uygulamanıza başvurarak özniteliğini uygulayın. Sınıflarda, yapılarda veya arabirimlerde XAML için tür dönüştürücüleri tanımlayabilirsiniz. Numaralandırmalar için tür dönüştürmesi sağlamanız gerekmez, bu dönüştürme yerel olarak etkinleştirilir.

Tür dönüştürüceniz, biçimlendirme içindeki öznitelikler veya başlatma metni için kullanılan bir dizeden amaçlanan hedef türüne dönüştürebilmelidir. Daha fazla bilgi için bkz. [TypeConverters ve xaml](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml).

Bir türün tüm değerlerine uygulamak yerine, XAML için bir tür dönüştürücü davranışı belirli bir özellik üzerinde de oluşturulabilir. Bu durumda, <xref:System.ComponentModel.TypeConverterAttribute> özellik tanımına (özel ve tanımları değil, dış tanım `get` `set` ) uygularsınız.

Özel eklenebilir bir üyenin XAML kullanımına yönelik bir tür dönüştürücü davranışı <xref:System.ComponentModel.TypeConverterAttribute> `get` , XAML kullanımını destekleyen Yöntem erişimcisine uygulanarak atanabilir.

Benzer şekilde <xref:System.ComponentModel.TypeConverter> , <xref:System.ComponentModel.TypeConverterAttribute> xaml varlığına ve tür dönüştürücü modeliyle başka amaçlar sunulmadan önce .net 'te de vardı. Başvurmak ve kullanmak için <xref:System.ComponentModel.TypeConverterAttribute> , tam olarak nitelemeniz veya için bir ifade sağlamanız gerekir `using` <xref:System.ComponentModel> . Ayrıca, projenize sistem derlemesini de dahil edin.

### <a name="uidpropertyattribute"></a>Uıdpropertyattribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Ada göre ilgili özelliğe başvuran bir dize.

[X:Uid yönergesine](xuid-directive.md)diğer adı olan BIR sınıfın clr özelliğini gösterir.

### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Boole değeri. Özniteliğin hedeflenen amacı için kullanılırsa, değer olarak ayarlanmalıdır `true` .

XAML nesne grafiğinin oluşturulması sırasında türün üst alta oluşturulup oluşturulmayacağını gösterir. Bu, büyük olasılıkla programlama modelinizin tanımıyla yakından ilgili olan gelişmiş bir kavramdır. Daha fazla bilgi için bkz. <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>ValueSerializerAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**Uygulama hedefi:** Class, Property, Method (tek XAML-geçerli yöntem durumu `get` eklenebilir bir üyeyi destekleyen bir erişimdir).

**Bağımsız değişkenler:** <xref:System.Type> Öznitelik atanmış türün tüm özellikleri serileştirilirken kullanılacak değer seri hale getirici desteği sınıfını ya da öznitelikli özelliği belirtir.

<xref:System.Windows.Markup.ValueSerializer> bir öğesinden daha fazla durum ve bağlam gerektiren bir değer serileştirme sınıfını belirtir <xref:System.ComponentModel.TypeConverter> . <xref:System.Windows.Markup.ValueSerializer> eklenebilir <xref:System.Windows.Markup.ValueSerializerAttribute> üyenin statik erişimci metoduna özniteliği uygulanarak eklenebilir bir üyeyle ilişkilendirilebilir `get` . Değer serileştirme Ayrıca, numaralandırmalar, arabirimler ve yapılar için de geçerlidir, ancak temsilciler için değildir.

### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**Uygulama hedefi:** Sınıf, özellikle nesne öğelerinde beyaz boşluk Kullanıcı arabirimi gösterimi için önemli olabilecek, karışık içeriği barındırmak beklenen koleksiyon türleri.

**Bağımsız değişkenler:** Seçim.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> bir koleksiyon türünün, bir XAML işlemcisi tarafından, koleksiyonda XAML düğüm akışının değer düğümlerinin oluşturulmasını etkileyen, bir XAML işlemcisi tarafından bir boşluk olarak işlenmesi gerektiğini gösterir. Daha fazla bilgi için bkz. [xaml 'de beyaz boşluk işleme](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**Uygulama hedefi:** Sınıf, özellik.

**Bağımsız değişkenler:** , Dize veya tür olarak iki atfı form türünü destekler <xref:System.Type> . Bkz. <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Bir sınıf veya özelliğin XAML için ertelenmiş yük kullanımına sahip olduğunu belirtir (örneğin, bir şablon davranışı) ve erteleme davranışını ve hedef/içerik türünü sağlayan sınıfı raporlar.

### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Geri aramayı adlandırır.

Bir sınıfın bir veya daha fazla özelliği için bir değer sağlamak üzere bir biçimlendirme uzantısı kullanabilir ve sınıfın herhangi bir özelliğinde bir biçimlendirme uzantısı kümesi işlemi gerçekleştirmeden önce bir XAML yazıcısının çağrı gerçekleştirmesi gereken bir işleyiciye başvuruda bulunduğunu gösterir.

### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Geri aramayı adlandırır.

Bir sınıfın bir veya daha fazla özelliği için bir değer sağlamak üzere tür dönüştürücüsü kullanabilir ve sınıfın herhangi bir özelliğinde bir tür dönüştürücü ayarlama işlemi gerçekleştirmeden önce bir XAML yazıcısının çağrı gerçekleştirmesi gereken bir işleyiciye başvuruda bulunabilir.

### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**Uygulama hedefi:** Sınıfı

**Bağımsız değişkenler:** Öznitelikli tür üzerinde diğer ad olarak kullanılacak özelliğin adını belirten bir dize `xml:lang` .

<xref:System.Windows.Markup.XmlLangPropertyAttribute> XML yönergesiyle eşleşen öznitelikli türün bir özelliğini raporlar `lang` . Özelliğin türü olması gerekmez, <xref:System.String> ancak bir dizeden atanabilir olması gerekir (atama, bir tür dönüştürücüsünün özelliğin türüyle veya belirli bir özellik ile ilişkilendirilmesi yoluyla gerçekleştirilebilir). Özelliğin okuma/yazma olması gerekir.

Eşleme senaryosu, `xml:lang` bir çalışma zamanı nesne MODELININ xml tarafından belirtilen dil bilgilerine BIR XMLDOM ile özellikle işlenmeksizin erişmesini sağlar.

Tanım, tanımlama türüne atanabilen tüm türetilmiş türlere devralınır. Belirli türetilmiş tür üzerinde uygulayarak, belirli bir türetilmiş tür için tanımı geçersiz kılabilirsiniz <xref:System.Windows.Markup.XmlLangPropertyAttribute> , ancak bu durum yaygın olmayan bir senaryodur.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Derleme düzeyinde XAML ile Ilgili CLR öznitelikleri

Aşağıdaki bölümler, türlere veya üye tanımlarına uygulanmamış, ancak derlemeler için uygulanan XAML ile ilgili öznitelikleri tanımlar. Bu öznitelikler XAML 'de kullanmak için özel türler içeren bir kitaplık tanımlamanın genel hedefi ile ilgili değildir. Özniteliklerin bazıları XAML düğüm akışını doğrudan etkilemeyebilir, ancak diğer tüketicilerin kullanması için düğüm akışında geçirilir. Bilgiler için tüketiciler, XAML ad alanı bilgilerine ve ilişkili önek bilgilerine ihtiyacı olan tasarım ortamlarını veya serileştirme süreçlerini içerir. XAML şeması bağlamı (.NET XAML Hizmetleri varsayılanı dahil) bu bilgileri de kullanır.

### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Değişkenlerinden**

- Alt sume için XAML ad alanının tanımlayıcısını belirten bir dize.

- Önceki bağımsız değişkenden XAML ad alanını engelleyen XAML ad alanı tanımlayıcısını belirten bir dize.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> XAML ad alanının başka bir XAML ad alanı tarafından bir alt grup olarak adlandırılmış olduğunu belirtir. Genellikle, Subsuming XAML ad alanı önceden tanımlanmış olarak belirtilir <xref:System.Windows.Markup.XmlnsDefinitionAttribute> . Bu teknik, bir kitaplıkta XAML sözlüğüne sürüm oluşturmak ve önceki sürümlü sözlük için önceden tanımlanmış biçimlendirme ile uyumlu hale getirmek için kullanılabilir.

### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Değişkenlerinden**

- Tanımlanacak XAML ad alanının tanımlayıcısını belirten bir dize.

- CLR ad alanı adında bir dize. CLR ad alanı, derlemenizin ortak türlerini tanımlamalıdır ve CLR ad alanı türlerinden en az birinin XAML kullanımı için tasarlanmış olması gerekir.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> xaml ad alanı ile CLR ad alanı arasında derleme temelinde bir eşlemeyi belirtir, daha sonra bir XAML nesne yazıcısı veya XAML şeması bağlamı tarafından tür çözümlemesi için kullanılır.

  Bir derlemeye birden fazla tane <xref:System.Windows.Markup.XmlnsDefinitionAttribute> uygulanabilir. Bu işlem aşağıdaki nedenlerden herhangi bir bileşim için yapılabilir:

- Kitaplık tasarımı, çalışma zamanı API 'SI erişiminin mantıksal organizasyonu için birden çok CLR ad alanı içerir; Ancak, aynı XAML ad alanına başvurarak bu ad alanındaki tüm türlerin XAML ile kullanılabilir olmasını istersiniz. Bu durumda, <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aynı <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değeri ancak farklı değerleri kullanarak birkaç öznitelik uygularsınız <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> . Bu, özellikle Framework veya uygulamanızın ortak kullanımda varsayılan XAML ad alanı olmasını amaçladığı XAML ad alanı için eşlemeler tanımlıyorsanız yararlıdır.

- Kitaplık tasarımı birden çok CLR ad alanı içerir ve bu CLR ad alanlarında türlerin kullanımları arasında bir bilinçli XAML ad alanı ayrımı istiyorsanız.

- Derlemede bir CLR ad alanı tanımlarsınız ve bunun birden çok XAML ad alanı üzerinden erişilebilir olmasını istersiniz. Bu senaryo, aynı kod temeli ile birden çok sözcük dağarcıklarını desteklerken oluşur.

- XAML dil desteğini bir veya daha fazla CLR ad alanında tanımlarsınız. Bu durumda, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> değer olmalıdır `http://schemas.microsoft.com/winfx/2006/xaml` .

### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute

**Başvuru belgeleri:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Değişkenlerinden**

- XAML ad alanının tanımlayıcısını belirten dize.

- Önerilen öneki belirten bir dize.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> XAML ad alanı için kullanılmak üzere önerilen bir ön ek belirtir. Ön ek, .NET XAML Hizmetleri tarafından seri hale getirilen bir XAML dosyasına öğe ve öznitelik yazarken <xref:System.Xaml.XamlXmlWriter> veya xaml uygulayan bir kitaplık, XAML düzenlemesi özelliklerine sahip bir tasarım ortamıyla etkileşime geçtiğinde yararlı olur.

  Bir derlemeye birden fazla tane <xref:System.Windows.Markup.XmlnsPrefixAttribute> uygulanabilir. Bu işlem aşağıdaki nedenlerden herhangi bir bileşim için yapılabilir:

- Derlemeniz birden fazla XAML ad alanı için türleri tanımlıyor. Bu durumda, her XAML ad alanı için farklı önek değerleri tanımlayın.

- Birden çok sözcük dağarcıklarını destekliyorsanız ve her bir sözlük ve XAML ad alanı için farklı ön ekler kullanıyorsunuz.

- Derlemede XAML dil desteği tanımlarsınız ve için bir öğesine sahip olursunuz <xref:System.Windows.Markup.XmlnsDefinitionAttribute> `http://schemas.microsoft.com/winfx/2006/xaml` . Bu durumda, genellikle öneki yükseltmeniz gerekir `x` .

> [!NOTE]
> .NET XAML Hizmetleri XAML ile ilgili özniteliği de tanımlar <xref:System.Windows.Markup.RootNamespaceAttribute> . Bu öznitelik, proje sistemi desteği için derleme düzeyi bir özniteliktir ve XAML özel türleri için uygun değildir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- [.NET XAML Hizmetlerinde Kullanılacak Özel Türleri Tanımlama](define-custom-types.md)
