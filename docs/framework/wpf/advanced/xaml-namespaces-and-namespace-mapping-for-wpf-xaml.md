---
title: XAML ad alanları ve ad alanı eşleme
description: Windows Presentation Foundation XAML dosyasının kök etiketinde genellikle bulunan iki XAML ad alanı eşlemesinin varlığı ve amacı hakkında daha fazla bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
ms.openlocfilehash: 42808df8e7483f60b1420fda890fe374493538f1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168375"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
Bu konu, bir WPF XAML dosyasının kök etiketinde genellikle bulunan iki XAML ad alanı eşleştirmelerinin varlığını ve amacını açıklamaktadır. Ayrıca, kendi kodunuzda ve/veya ayrı derlemelerde tanımlanmış öğeleri kullanmak için benzer eşlemelerin nasıl üretileceğini açıklar.  

## <a name="what-is-a-xaml-namespace"></a>XAML ad alanı nedir?  
 XAML ad alanı aslında bir XML ad alanı kavramının uzantısıdır. XAML ad alanı belirtme teknikleri, XML ad alanı tanımlayıcılarını, URI 'Leri ad alanı tanımlayıcıları olarak kullanma kuralını kullanır, aynı biçimlendirme kaynağından birden çok ad alanına başvurmak için bir yol sağlamak üzere ön ekleri kullanır ve bu şekilde devam eder. XML ad alanının XAML tanımına eklenen birincil kavram, bir XAML ad alanının hem biçimlendirme kullanımları için benzersizlik kapsamını, hem de biçimlendirme varlıklarının belirli CLR ad alanları ve başvurulan derlemeler tarafından nasıl desteklenmediğini etkilediğini gösterir. Bu ikinci değerlendirme Ayrıca bir XAML şeması bağlamı kavramından etkilenir. Ancak, WPF 'in XAML ad alanları ile nasıl çalıştığı konusunda, xaml ad alanlarını genellikle varsayılan bir XAML ad alanı, XAML dili ad alanı ve XAML biçiminizle eşleştirilmiş diğer XAML ad alanları ile doğrudan belirli CLR ad alanları ve başvurulan derlemeler açısından düşünebilirsiniz.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF ve XAML ad alanı bildirimleri  
 Birçok XAML dosyasının kök etiketindeki ad alanı bildirimleri içinde, genellikle iki XML ad alanı bildirimi olduğunu görürsünüz. İlk bildirim, genel WPF istemci/çerçeve XAML ad alanını varsayılan olarak eşler:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 İkinci bildirim ayrı bir XAML ad alanını eşler, (genellikle) `x:` ön ekine eşlenir.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Bu bildirimler arasındaki ilişki, `x:` ön ek EŞLEMESININ xaml dil tanımının parçası olan iç bilgileri desteklemesidir ve bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DIL olarak xaml kullanan bir uygulama ve xaml için nesnelerinin bir sözlüğünü tanımlar. WPF sözlüğü kullanımları XAML iç yapı kullanımlarından çok daha yaygın olacak şekilde, WPF sözlüğü varsayılan olarak eşlenir.  
  
 `x:`Xaml dil iç bilgileri desteğini eşlemek için önek kuralı, proje şablonları, örnek kod ve bu SDK içindeki dil özelliklerinin belgeleri tarafından izlenir. XAML ad alanı, temel WPF uygulamaları için bile gerekli olan çok sayıda yaygın kullanılan özelliği tanımlar. Örneğin, bir XAML dosyasının arka plan kodunu kısmi bir sınıf aracılığıyla birleştirmek için, söz konusu sınıfı `x:Class` ılgılı xaml dosyasının kök öğesinde özniteliği olarak vermelisiniz. Ya da bir XAML sayfasında, anahtarlı kaynak olarak erişmek istediğiniz herhangi bir öğenin, `x:Key` söz konusu öğede ayarlanmış özniteliği olmalıdır. Bu ve XAML 'in diğer yönleri hakkında daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [XAML sözdizimi ayrıntılı](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>Özel sınıflar ve derlemelere eşleme  
 XML ad alanlarını `xmlns` , standart WPF ve xaml iç DIZISI xaml ad alanlarının öneklerle nasıl eşlendiğine benzer şekilde, bir önek bildirimi içindeki bir dizi belirteci kullanarak derlemelere eşleyebilirsiniz.  
  
 Sözdizimi aşağıdaki olası adlandırılmış belirteçleri ve aşağıdaki değerleri alır:  
  
 `clr-namespace:`Öğe olarak göstermek için ortak türleri içeren bütünleştirilmiş kod içinde bildirildiği CLR ad alanı.  
  
 `assembly=`Başvurulan CLR ad alanının bazılarını veya tümünü içeren derleme. Bu değer genellikle yalnızca derlemenin adıdır, yol değildir ve uzantıyı içermez (örn. dll veya. exe). Bu derlemenin yolu, eşlemeye çalıştığınız XAML 'yi içeren proje dosyasında bir proje başvurusu olarak oluşturulmalıdır. Sürüm oluşturma ve tanımlayıcı ad imzalamayı birleştirmek için, `assembly` değeri <xref:System.Reflection.AssemblyName> basit dize adı yerine tarafından tanımlanan bir dize olabilir.  
  
 `clr-namespace`Belirteci değerinden ayıran karakterin bir iki nokta üst üste olduğunu unutmayın (:) `assembly`belirteci değerinden ayıran karakter bir eşittir işareti (=) olur. Bu iki belirteç arasında kullanılacak karakter noktalı virgüldür. Ayrıca, bildirimde herhangi bir yere boşluk eklemeyin.  
  
### <a name="a-basic-custom-mapping-example"></a>Temel bir özel eşleme örneği  
 Aşağıdaki kod örnek bir özel sınıf tanımlar:  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 Bu özel sınıf daha sonra proje ayarları (gösterilmez) başına bir kitaplığa derlenir `SDKSampleLibrary` .  
  
 Bu özel sınıfa başvurmak için, Ayrıca, Visual Studio 'da Çözüm Gezgini Kullanıcı arabirimini kullanarak genellikle geçerli projeniz için bir başvuru olarak dahil etmeniz gerekir.  
  
 Artık bir sınıf içeren bir kitaplığınız ve proje ayarları 'nda buna bir başvuru olduğuna göre, XAML 'de kök öğenizin bir parçası olarak aşağıdaki önek eşlemesini ekleyebilirsiniz:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Tümünü bir araya koymak için aşağıdaki XAML, kök etiketindeki tipik varsayılan ve x: eşlemeleriyle birlikte özel eşlemeyi de içeren XAML 'dir, ardından bu kullanıcı arabiriminde örnek oluşturmak için bir ön ek başvurusu kullanır `ExampleClass` :  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>Geçerli derlemelere eşleme  
 `assembly``clr-namespace`başvurulan, özel sınıflara başvuran uygulama koduyla aynı derleme içinde tanımlanmışsa atlanabilir. Ya da bu durum için eşdeğer bir sözdizimi `assembly=` , eşittir işaretinden sonra dize belirteci olmadan belirtmektir.  
  
 Özel sınıflar, aynı derlemede tanımlanmışsa bir sayfanın kök öğesi olarak kullanılamaz. Kısmi sınıfların eşlenmesi gerekmez; yalnızca uygulamanızdaki bir sayfanın kısmi sınıfı olmayan sınıfların, XAML 'de öğe olarak başvurmak istiyorsanız eşlenmesi gerekir.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>CLR ad alanlarını bir derlemede XML ad alanları ile eşleme  
 WPF, birden çok CLR ad alanını tek XAML ad alanına eşlemek için XAML işlemcileri tarafından tüketilen bir CLR özniteliği tanımlar. Bu öznitelik, derlemeyi <xref:System.Windows.Markup.XmlnsDefinitionAttribute> üreten kaynak kodundaki derleme düzeyine yerleştirilir. WPF derleme kaynak kodu, ve gibi çeşitli ortak ad alanlarını ad alanına eşlemek için bu özniteliği <xref:System.Windows> kullanır <xref:System.Windows.Controls> `http://schemas.microsoft.com/winfx/2006/xaml/presentation` .  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>İki parametre alır: XML/xaml ad alanı adı ve clr ad alanı adı. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Birden çok clr ad alanını aynı XML ad alanı ile eşlemek için birden fazla bulunabilir. Eşlendikten sonra, bu ad alanlarının üyelerine, isterseniz `using` kısmi sınıf arka plan kod sayfasında uygun deyim sağlanarak tam nitelik olmadan da başvurulabilir. Daha ayrıntılı bilgi için bkz <xref:System.Windows.Markup.XmlnsDefinitionAttribute> ..  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>XAML şablonlarından tasarımcı ad alanları ve diğer ön ekler  
 WPF XAML için geliştirme ortamları ve/veya tasarım araçları ile çalışıyorsanız XAML biçimlendirmesinde diğer tanımlı XAML ad alanları/önekleri olduğunu fark edebilirsiniz.  
  
 Visual Studio için WPF Tasarımcısı, genellikle önekle eşleştirilmiş bir tasarımcı ad alanı kullanır `d:` . WPF için daha yeni proje şablonları, Visual Studio için WPF Tasarımcısı ve diğer tasarım ortamları arasında XAML değişimi desteklemek üzere bu XAML ad alanını önceden eşlemenizi gerektirebilir. Bu tasarım XAML ad alanı, tasarımcıda XAML tabanlı kullanıcı arabirimine gidiş dönüş sırasında tasarım durumunu aktarmak için kullanılır. Ayrıca `d:IsDataSource` , bir Tasarımcıda çalışma zamanı veri kaynaklarını etkinleştiren gibi özellikler için de kullanılır.  
  
 Eşlenmiş olarak gördüğünüz başka bir ön ek vardır `mc:` . `mc:`, biçimlendirme uyumluluğuna yöneliktir ve XAML 'e özgü olmayan bir biçimlendirme uyumluluğu deseninin üzerinde bulunur. Biçimlendirme uyumluluğu özellikleri, bazı bir ölçüde, çerçeveler arasında XAML veya yedekleme uygulamasının diğer sınırları arasında XAML alışverişi yapmak, XAML şema bağlamları arasında çalışmak, tasarımcılar için sınırlı modlar için uyumluluk sağlamak ve bu şekilde devam etmek için kullanılabilir. Biçimlendirme uyumluluğu kavramları ve WPF ile nasıl ilişkilendirildikleri hakkında daha fazla bilgi için bkz. [Biçimlendirme uyumluluğu (MC:) Dil özellikleri](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF ve derleme yükleme  
 WPF için XAML şeması bağlamı WPF uygulama modeliyle tümleştirilir ve bu da CLR tanımlı kavramını kullanır <xref:System.AppDomain> . Aşağıdaki sıra, XAML şema bağlamının, <xref:System.AppDomain> ve diğer FAKTÖRLERIN WPF kullanımına bağlı olarak, çalışma zamanında veya tasarım zamanında derlemelerin nasıl yükleneceğini ya da türlerin nasıl bulunacağını nasıl yorumlayacağını tanımlar.  
  
1. <xref:System.AppDomain>En son yüklenen derlemeden başlayarak, adının tüm yönlerini karşılayan, önceden yüklenmiş bir derlemeyi arayarak ' de yineleyin.  
  
2. Ad nitelikli ise, <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı çağırın.  
  
3. Nitelenmiş bir adın kısa ad + ortak anahtar belirteci, biçimlendirmenin yüklendiği derlemeyle eşleşiyorsa, bu derlemeyi döndürün.  
  
4. Çağırmak için kısa ad + ortak anahtar belirtecini kullanın <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> .  
  
5. Ad nitelenmemiş ise, çağırın <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> .  
  
 Gevşek XAML 3. adımı kullanmaz; yüklenen derleme yok.  
  
 WPF için derlenen XAML (XamlBuildTask aracılığıyla oluşturulur), ' den önceden yüklenmiş derlemeleri kullanmaz <xref:System.AppDomain> (adım 1). Ayrıca, ad hiçbir durumda XamlBuildTask çıktısından nitelenmemelidir, bu nedenle 5. adım uygulanmaz.  
  
 Derlenen BAML (PresentationBuildTask aracılığıyla oluşturulur) tüm adımları kullanır, ancak BAML de nitelenmemiş derleme adları içermemelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanlarını anlama](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
