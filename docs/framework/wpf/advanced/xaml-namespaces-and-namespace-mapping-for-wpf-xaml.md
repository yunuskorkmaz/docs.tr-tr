---
title: WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
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
ms.openlocfilehash: 4fc88f1e32b8ddce6abccad085b0c44a5c716e8b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400809"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
Bu konu, bir WPF XAML dosyasının kök etiketinde genellikle bulunan iki XAML ad alanı eşleştirmelerinin varlığını ve amacını açıklamaktadır. Ayrıca, kendi kodunuzda ve/veya ayrı derlemelerde tanımlanmış öğeleri kullanmak için benzer eşlemelerin nasıl üretileceğini açıklar.  

## <a name="what-is-a-xaml-namespace"></a>XAML ad alanı nedir?  
 XAML ad alanı aslında bir XML ad alanı kavramının uzantısıdır. XAML ad alanı belirtme teknikleri, XML ad alanı tanımlayıcılarını, URI 'Leri ad alanı tanımlayıcıları olarak kullanma kuralını kullanır, aynı biçimlendirme kaynağından birden çok ad alanına başvurmak için bir yol sağlamak üzere ön ekleri kullanır ve bu şekilde devam eder. XML ad alanının XAML tanımına eklenen birincil kavram, bir XAML ad alanının hem biçimlendirme kullanımları için benzersizlik kapsamını, hem de biçimlendirme varlıklarının belirli CLR ad alanları tarafından nasıl desteklenen ve başvurulan kodları. Bu ikinci değerlendirme Ayrıca bir XAML şeması bağlamı kavramından etkilenir. Ancak, WPF 'in XAML ad alanları ile nasıl çalıştığı konusunda, xaml ad alanlarını genellikle varsayılan XAML ad alanı, XAML dili ad alanı ve XAML biçiminizle eşleştirilmiş diğer XAML ad alanları açısından doğrudan belirli bir CLR ile eşleştirirken düşünebilirsiniz ad alanları ve başvurulan derlemeler.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF ve XAML ad alanı bildirimleri  
 Birçok XAML dosyasının kök etiketindeki ad alanı bildirimleri içinde, genellikle iki XML ad alanı bildirimi olduğunu görürsünüz. İlk bildirim, genel WPF istemci/çerçeve XAML ad alanını varsayılan olarak eşler:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 İkinci bildirim ayrı bir xaml ad alanını eşler, (genellikle) `x:` ön ekine eşlenir.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Bu bildirimler arasındaki ilişki, `x:` ön ek eşlemesinin XAML dil tanımının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parçası olan iç bilgileri desteklemesidir ve bir dil olarak xaml kullanan bir uygulama ve onun bir sözlüğünü tanımlar XAML nesneleri. WPF sözlüğü kullanımları XAML iç yapı kullanımlarından çok daha yaygın olacak şekilde, WPF sözlüğü varsayılan olarak eşlenir.  
  
 XAML dil yapı içlerini eşlemek için [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] önekkuralı,projeşablonları,örnekkodvebununiçindekidilözelliklerininbelgeleritarafındanizlenir.`x:` XAML ad alanı, temel WPF uygulamaları için bile gerekli olan çok sayıda yaygın kullanılan özelliği tanımlar. Örneğin, bir xaml dosyasının arka plan kodunu kısmi bir sınıf aracılığıyla birleştirmek için, söz konusu sınıfı ilgili xaml dosyasının kök öğesinde `x:Class` özniteliği olarak vermelisiniz. Ya da bir XAML sayfasında, anahtarlı kaynak `x:Key` olarak erişmek istediğiniz herhangi bir öğenin, söz konusu öğede ayarlanmış özniteliği olmalıdır. Bu ve XAML 'in diğer yönleri hakkında daha fazla bilgi için bkz. [xaml genel bakış (WPF)](xaml-overview-wpf.md) veya [XAML sözdizimi ayrıntılı](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Özel sınıflar ve derlemelere eşleme  
 XML ad alanlarını, standart WPF ve xaml iç dizisi xaml ad alanlarının öneklerle nasıl eşlendiğine benzer şekilde, bir `xmlns` önek bildirimi içindeki bir dizi belirteci kullanarak derlemelere eşleyebilirsiniz.  
  
 Sözdizimi aşağıdaki olası adlandırılmış belirteçleri ve aşağıdaki değerleri alır:  
  
 `clr-namespace:`Öğe olarak göstermek için ortak türleri içeren bütünleştirilmiş kod içinde bildirildiği CLR ad alanı.  
  
 `assembly=`Başvurulan CLR ad alanının bazılarını veya tümünü içeren derleme. Bu değer genellikle yalnızca derlemenin adıdır, yol değildir ve uzantıyı içermez (örn. dll veya. exe). Bu derlemenin yolu, eşlemeye çalıştığınız XAML 'yi içeren proje dosyasında bir proje başvurusu olarak oluşturulmalıdır. Sürüm oluşturma ve tanımlayıcı ad imzalamayı `assembly` birleştirmek için, değeri basit dize adı yerine tarafından <xref:System.Reflection.AssemblyName>tanımlanan bir dize olabilir.  
  
 `clr-namespace` Belirteci değerinden ayıran karakterin bir iki nokta üst üste olduğunu unutmayın (:) `assembly` belirteci değerinden ayıran karakter bir eşittir işareti (=) olur. Bu iki belirteç arasında kullanılacak karakter noktalı virgüldür. Ayrıca, bildirimde herhangi bir yere boşluk eklemeyin.  
  
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
  
 Bu özel sınıf daha sonra proje ayarları (gösterilmez) `SDKSampleLibrary`başına bir kitaplığa derlenir.  
  
 Bu özel sınıfa başvurmak için, Ayrıca, Visual Studio 'da Çözüm Gezgini Kullanıcı arabirimini kullanarak genellikle geçerli projeniz için bir başvuru olarak dahil etmeniz gerekir.  
  
 Artık bir sınıf içeren bir kitaplığınız ve proje ayarları 'nda buna bir başvuru olduğuna göre, XAML 'de kök öğenizin bir parçası olarak aşağıdaki önek eşlemesini ekleyebilirsiniz:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Tümünü bir araya koymak için aşağıdaki xaml, kök etiketindeki tipik varsayılan ve x: eşlemeleriyle birlikte özel eşlemeyi de içeren xaml 'dir, ardından bu kullanıcı arabiriminde örnek oluşturmak `ExampleClass` için bir ön ek başvurusu kullanır:  
  
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
 `assembly`başvurulan, `clr-namespace` özel sınıflara başvuran uygulama koduyla aynı derleme içinde tanımlanmışsa atlanabilir. Ya da bu durum için eşdeğer bir sözdizimi, eşittir işaretinden `assembly=`sonra dize belirteci olmadan belirtmektir.  
  
 Özel sınıflar, aynı derlemede tanımlanmışsa bir sayfanın kök öğesi olarak kullanılamaz. Kısmi sınıfların eşlenmesi gerekmez; yalnızca uygulamanızdaki bir sayfanın kısmi sınıfı olmayan sınıfların, XAML 'de öğe olarak başvurmak istiyorsanız eşlenmesi gerekir.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>CLR ad alanlarını bir derlemede XML ad alanları ile eşleme  
 WPF, birden çok CLR ad alanını tek XAML ad alanına eşlemek için XAML işlemcileri tarafından tüketilen bir CLR özniteliği tanımlar. Bu öznitelik <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, derlemeyi üreten kaynak kodundaki derleme düzeyine yerleştirilir. WPF derleme kaynak kodu, <xref:System.Windows> ve <xref:System.Windows.Controls> [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] gibi çeşitli ortak ad alanlarını ad alanına eşlemek için bu özniteliği kullanır.  
  
 İki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> parametre alır: XML/xaml ad alanı adı ve clr ad alanı adı. Birden çok clr ad alanını aynı XML ad alanı ile eşlemek için birden fazla bulunabilir.<xref:System.Windows.Markup.XmlnsDefinitionAttribute> Eşlendikten sonra, bu ad alanlarının üyelerine, isterseniz kısmi sınıf arka plan kod sayfasında uygun `using` deyim sağlanarak tam nitelik olmadan da başvurulabilir. Daha ayrıntılı bilgi için bkz <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>XAML şablonlarından tasarımcı ad alanları ve diğer ön ekler  
 WPF XAML için geliştirme ortamları ve/veya tasarım araçları ile çalışıyorsanız XAML biçimlendirmesinde diğer tanımlı XAML ad alanları/önekleri olduğunu fark edebilirsiniz.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]genellikle önekle `d:`eşlenen bir tasarımcı ad alanı kullanır. WPF için daha yeni proje şablonları, XAML [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 'in ve diğer tasarım ortamlarının değişim desteğini desteklemek üzere bu xaml ad alanını önceden eşlemeye olanak sağlayabilir. Bu tasarım XAML ad alanı, tasarımcıda XAML tabanlı kullanıcı arabirimine gidiş dönüş sırasında tasarım durumunu aktarmak için kullanılır. Ayrıca `d:IsDataSource`, bir Tasarımcıda çalışma zamanı veri kaynaklarını etkinleştiren gibi özellikler için de kullanılır.  
  
 Eşlenmiş olarak gördüğünüz başka bir ön ek `mc:`vardır. `mc:`, biçimlendirme uyumluluğuna yöneliktir ve XAML 'e özgü olmayan bir biçimlendirme uyumluluğu deseninin üzerinde bulunur. Biçimlendirme uyumluluğu özellikleri, bazı bir ölçüde, çerçeveler arasında XAML veya yedekleme uygulamasının diğer sınırları arasında XAML alışverişi yapmak, XAML şema bağlamları arasında çalışmak, tasarımcılar için sınırlı modlar için uyumluluk sağlamak ve bu şekilde devam etmek için kullanılabilir. Biçimlendirme uyumluluğu kavramları ve WPF ile nasıl ilişkilendirildikleri hakkında daha fazla bilgi için bkz [. Biçimlendirme uyumluluğu (MC:) Dil özellikleri](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF ve derleme yükleme  
 WPF için XAML şeması bağlamı WPF uygulama modeliyle tümleştirilir ve bu da CLR tanımlı kavramını <xref:System.AppDomain>kullanır. Aşağıdaki sıra, xaml şema bağlamının, <xref:System.AppDomain> ve diğer faktörlerin WPF kullanımına bağlı olarak, çalışma zamanında veya tasarım zamanında derlemelerin nasıl yükleneceğini ya da türlerin nasıl bulunacağını nasıl yorumlayacağını tanımlar.  
  
1. En son yüklenen derlemeden başlayarak, adının tüm yönlerini karşılayan, önceden yüklenmiş bir derlemeyi arayarak 'deyineleyin.<xref:System.AppDomain>  
  
2. Ad nitelikli ise, tam adı çağırın <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> .  
  
3. Nitelenmiş bir adın kısa ad + ortak anahtar belirteci, biçimlendirmenin yüklendiği derlemeyle eşleşiyorsa, bu derlemeyi döndürün.  
  
4. Çağırmak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa ad + ortak anahtar belirtecini kullanın.  
  
5. Ad nitelenmemiş ise, çağırın <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Gevşek XAML 3. adımı kullanmaz; yüklenen derleme yok.  
  
 WPF için derlenen XAML (XamlBuildTask aracılığıyla oluşturulur), ' den <xref:System.AppDomain> önceden yüklenmiş derlemeleri kullanmaz (adım 1). Ayrıca, ad hiçbir durumda XamlBuildTask çıktısından nitelenmemelidir, bu nedenle 5. adım uygulanmaz.  
  
 Derlenen BAML (PresentationBuildTask aracılığıyla oluşturulur) tüm adımları kullanır, ancak BAML de nitelenmemiş derleme adları içermemelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanlarını anlama](https://go.microsoft.com/fwlink/?LinkId=98069)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
