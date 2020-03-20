---
title: XAML İsim Alanları ve Ad Alanı Eşleme
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
ms.openlocfilehash: 9b01643e8f8d77073595253580ebea60fabfd23b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186240"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
Bu konu ayrıca, bir WPF XAML dosyasının kök etiketinde sıklıkla bulunan iki XAML ad alanı eşlemesinin varlığını ve amacını açıklar. Ayrıca, kendi kodunuzda ve/veya ayrı derlemeler içinde tanımlanan öğeleri kullanmak için benzer eşlemelerin nasıl üretilebildiğini de açıklar.  

## <a name="what-is-a-xaml-namespace"></a>XAML Ad Alanı nedir?  
 XAML ad alanı gerçekten bir XML ad alanı kavramının bir uzantısıdır. Bir XAML ad alanı belirtme teknikleri XML ad alanı sözdizimini, uri'leri ad alanı tanımlayıcıları olarak kullanma kuralına, aynı biçimlendirme kaynağından birden çok ad alanına başvurmak için bir araç sağlamak için önekleri kullanma kuralına ve benzeri ne bürünmeye dayanır. XML ad alanının XAML tanımına eklenen birincil kavram, XAML ad alanının hem biçimlendirme kullanımları için bir benzersizlik kapsamını ima etmesi hem de biçimlendirme varlıklarının belirli CLR ad alanları tarafından potansiyel olarak nasıl desteklenenve başvurulan Derleme. Bu ikinci düşünce de bir XAML şema bağlamı kavramı etkilenir. Ancak WPF'nin XAML ad alanlarıyla nasıl çalıştığı nasıI çalışırsa, genellikle XAML ad boşluklarını varsayılan XAML ad alanı, XAML dil ad alanı ve XAML biçimlendirmeniz tarafından doğrudan belirli destek CLR'inizle eşlenen diğer XAML ad alanları açısından düşünebilirsiniz ad alanları ve başvurulan derlemeler.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF ve XAML İsim Alanı Bildirimleri  
 Birçok XAML dosyasının kök etiketindeki ad alanı bildirimleri içinde, genellikle iki XML ad alanı bildirimi olduğunu görürsünüz. İlk bildirim, genel WPF istemcisini / çerçeve XAML ad alanını varsayılan olarak eşler:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 İkinci bildirim, önek için (genellikle) `x:` eşleme, ayrı bir XAML ad alanı eşler.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Bu bildirimler arasındaki ilişki, `x:` önek eşlemenin XAML dil tanımının bir parçası olan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içselleri desteklemesi ve XAML'yi bir dil olarak kullanan ve XAML için nesnelerinin sözcük dağarcığını tanımlayan bir uygulama olmasıdır. WPF kelime nin kullanımları XAML içsel kullanımlarından çok daha yaygın olacağından, WPF sözcük dağarcığı varsayılan olarak eşlenir.  
  
 XAML dili içsel desteğinin eşlenmesi için `x:` önek kuralını proje şablonları, örnek kod ve bu SDK'daki dil özelliklerinin belgelenmesi takip eder. XAML ad alanı, temel WPF uygulamaları için bile gerekli olan yaygın olarak kullanılan birçok özelliği tanımlar. Örneğin, bir XAML dosyasının arkasında herhangi bir kod alabilmek için, bu `x:Class` sınıfı ilgili XAML dosyasının kök öğesindeki öznitelik olarak adlandırmanız gerekir. Veya, anahtarlı kaynak `x:Key` olarak erişmek istediğiniz bir XAML sayfasında tanımlandığı gibi herhangi bir öğe, söz konusu öğeüzerinde öznitelik ayarlanmalıdır. XAML'nin bu ve diğer yönleri hakkında daha fazla bilgi için bkz: [XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [XAML Sözdizimi Ayrıntılı](xaml-syntax-in-detail.md)olarak.  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>Özel Sınıflar ve Derlemeler için Haritalama  
 XML ad alanlarını, standart WPF ve XAML `xmlns` içsel seves XAML ad alanlarının öneklerle eşlenmiş olması gibi bir önek bildirimi içinde bir dizi belirteç kullanarak derlemelerle eşleyebilirsiniz.  
  
 Sözdizimi aşağıdaki olası adlandırılmış belirteçleri ve aşağıdaki değerleri alır:  
  
 `clr-namespace:`Derleme içinde, öğeler olarak ortaya çıkarmak için ortak türleri içeren clr ad alanı bildirilir.  
  
 `assembly=`Başvurulan CLR ad alanının bazılarını veya tümlerini içeren derleme. Bu değer genellikle yalnızca derlemenin adıdır, yol değil ve uzantıyı içermez (.dll veya .exe gibi). Bu derlemeye giden yol, eşlemeye çalıştığınız XAML'yi içeren proje dosyasında proje başvurusu olarak oluşturulmalıdır. Sürüm ve güçlü ad imzalamayı birleştirmek için, `assembly` değer basit dize <xref:System.Reflection.AssemblyName>adı yerine tanımlandığı şekilde bir dize olabilir.  
  
 `clr-namespace` Belirteci değerinden ayıran karakterin bir iki nokta üst üste (:) `assembly` belirteci değerinden ayıran karakter eşittir işareti (=) ise. Bu iki belirteç arasında kullanılacak karakter bir yarı nokta noktadır. Ayrıca, bildirimde herhangi bir yerde herhangi bir beyaz boşluk içermez.  
  
### <a name="a-basic-custom-mapping-example"></a>Temel Özel Eşleme Örneği  
 Aşağıdaki kod örnek özel bir sınıf tanımlar:  
  
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
  
 Bu özel sınıf daha sonra proje ayarları (gösterilmez) olarak adlandırılır `SDKSampleLibrary`bir kitaplık, içine derlenir.  
  
 Bu özel sınıfa başvurmak için, visual Studio'da Çözüm Gezgini Kullanıcı Arabirimi'ni kullanarak yapacağınız geçerli projeniz için bir başvuru olarak da eklemeniz gerekir.  
  
 Artık bir sınıf içeren bir kitaplığınız ve proje ayarlarında buna bir başvurunuz olduğuna göre, XAML'deki kök öğenizin bir parçası olarak aşağıdaki önek eşlemenini ekleyebilirsiniz:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Hepsini bir araya getirmek için, aşağıdaki tipik varsayılan ve x ile birlikte özel eşleme içeren XAML: kök etiketieşlemeler, sonra bu Kullanıcı Arabirimi instantiate `ExampleClass` için önceden belirlenmiş bir başvuru kullanır:  
  
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
  
### <a name="mapping-to-current-assemblies"></a>Geçerli Derlemelere Eşleme  
 `assembly``clr-namespace` başvurulan özel sınıflara başvuran uygulama koduyla aynı derleme içinde tanımlanıyorsa atlanabilir. Veya, bu servis talebi için eşdeğer `assembly=`bir sözdizimi, eşitler işaretini izleyen dize belirteçolmadan belirtmektir.  
  
 Özel sınıflar, aynı derlemede tanımlanmışsa, sayfanın kök öğesi olarak kullanılamaz. Kısmi sınıfların eşlenemeihtiyacı yoktur; yalnızca uygulamanızdaki bir sayfanın kısmi sınıfı olmayan sınıfların XAML'deki öğeler olarak başvurmayı planlıyorsanız eşlenmeleri gerekir.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>CLR Ad Alanlarını Derlemedeki XML İsim Boşluklarıyla Eşleme  
 WPF, birden çok CLR ad alanını tek bir XAML ad alanıyla eşlemek için XAML işlemciler tarafından tüketilen bir CLR özniteliği tanımlar. Bu öznitelik, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, derleme üreten kaynak kodunda montaj düzeyine yerleştirilir. WPF derleme kaynak kodu, <xref:System.Windows> <xref:System.Windows.Controls> `http://schemas.microsoft.com/winfx/2006/xaml/presentation` ad alanı gibi çeşitli ortak ad alanlarını eşlemek için bu özniteliği kullanır.  
  
 İki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> parametre alır: XML/XAML ad alanı adı ve CLR ad alanı adı. Birden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> fazla CLR ad alanını aynı XML ad alanıyla eşlemek için birden fazla var olabilir. Eşlendikten sonra, bu ad alanlarının üyeleri, kısmi sınıf kod arkası `using` sayfasında uygun ifadeyi sağlayarak istenirse tam nitelik olmadan da başvurulabilir. Daha fazla bilgi <xref:System.Windows.Markup.XmlnsDefinitionAttribute>için bkz.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>XAML Şablonlarından Tasarımcı Ad Alanları ve Diğer Önekleri  
 WPF XAML için geliştirme ortamları ve/veya tasarım araçlarıyla çalışıyorsanız, XAML biçimlendirmesinde başka tanımlanmış XAML ad alanları / önekleri olduğunu fark edebilirsiniz.  
  
 Visual Studio için WPF Designer genellikle önek `d:`eşlenen bir tasarımcı ad alanı kullanır. WPF için daha yeni proje şablonları, Visual Studio için WPF Designer ve diğer tasarım ortamları arasında XAML'nin değiş tokuşünü desteklemek için bu XAML ad alanını önceden eşleyebilir. Bu tasarım XAML ad alanı, tasarımcıda XAML tabanlı Kullanıcı Arabirimi'ni yuvarlarken tasarım durumunu sürdürmek için kullanılır. Ayrıca, bir tasarımcıda `d:IsDataSource`çalışma zamanı veri kaynaklarını etkinleştiren özellikler için de kullanılır.  
  
 Eşlenen görebilirsiniz başka bir `mc:`önek. `mc:`biçimlendirme uyumluluğu içindir ve xaml'ye özgü olmayan bir biçimlendirme uyumluluk deseni dir. Bir dereceye kadar, biçimlendirme uyumluluk özellikleri çerçeveler arasında xaml değişimi veya uygulama destek diğer sınırları arasında, XAML şema bağlamları arasında çalışmak, tasarımcılar sınırlı modları için uyumluluk sağlamak ve benzeri için kullanılabilir. Biçimlendirme uyumluluk kavramları ve WPF ile nasıl ilişkili oldukları hakkında daha fazla bilgi için [bkz. Dil Özellikleri](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF ve Montaj Yükleme  
 WPF için XAML şeması, WPF uygulama modeliyle bütünleşir ve bu da CLR <xref:System.AppDomain>tarafından tanımlanan . Aşağıdaki sıra, XAML şema bağlamının WPF kullanımı <xref:System.AppDomain> ve diğer etkenlere bağlı olarak derlemeleri nasıl yükleyeceklerini veya çalışma zamanında veya tasarım zamanında türleri nasıl bulabileceğinizi açıklar.  
  
1. <xref:System.AppDomain>En son yüklenen derlemeden başlayarak, adın tüm yönleriyle eşleşen zaten yüklü bir derleme yi arayarak,  
  
2. Ad nitelikliyse, nitelikli <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> adı arayın.  
  
3. Nitelikli bir ismin kısa adı + ortak anahtar belirteci biçimlendirmenin yüklendiği derlemeyle eşleşiyorsa, bu derlemeyi döndürün.  
  
4. Aramak <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>için kısa ad + ortak anahtar belirteci kullanın.  
  
5. Ad niteliksizse, <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>çağırın.  
  
 Gevşek XAML Adım 3 kullanmaz; montajdan yüklenmiş bir yük yoktur.  
  
 WPF için derlenmiş XAML (XamlBuildTask üzerinden oluşturulan) (Adım <xref:System.AppDomain> 1) zaten yüklenmiş derlemeleri kullanmaz. Ayrıca, ad XamlBuildTask çıktısından asla niteliksiz olmamalıdır, bu nedenle Adım 5 geçerli değildir.  
  
 Derlenmiş BAML (PresentationBuildTask aracılığıyla oluşturulan) tüm adımları kullanır, ancak BAML de niteliksiz montaj adları içermemelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML İsim Alanlarını Anlama](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
