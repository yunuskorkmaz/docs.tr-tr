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
ms.openlocfilehash: 9e93d3cd417d0d075fcebb8327ec51799884f8d6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064835"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
Bu konuda daha fazla varlığı ve sık WPF XAML dosyasının kök etiketi içinde bulunan iki XAML ad uzayı eşlemelerinden amacını açıklar. Ayrıca, kendi kod ve/veya ayrı derlemeler içinde tanımlanan öğeleri kullanmak için benzer eşlemeleri oluşturmak nasıl açıklar.  
  
  
## <a name="what-is-a-xaml-namespace"></a>XAML Namespace nedir?  
 XAML ad alanı bir XML ad alanı kavramının gerçekten bir uzantısıdır. XAML ad alanı belirtme teknikleri ön ekleri aynı biçimlendirme kaynak, birden çok ad başvurmak için bir yol sağlamak için ad uzayı tanımlayıcıları olarak URI'ler kullanarak kuralı XML ad alanı sözdizimini kullanır ve benzeri. XML ad alanı XAML tanımına eklenen birincil XAML ad alanı hem bir kapsam benzersizliğin biçimlendirme kullanımlar için anlamına gelir ve ayrıca nasıl biçimlendirme varlıklar büyük olasılıkla belirli CLR ad tarafından desteklenen ve başvurulan etkiler kavramdır bütünleştirilmiş kodları. Bu ikinci faktör ayrıca XAML şema içeriği kavramı tarafından etkilenir. Ancak WPF XAML ad alanları ile nasıl çalıştığına ilişkin daha fazla amaçları için genellikle XAML ad alanları varsayılan bir XAML ad alanı, XAML dil ad alanı ve, XAML biçimlendirme doğrudan belirli destekleyen CLR tarafından eşleştirilen herhangi başka bir XAML ad açısından düşünebilirsiniz ad alanları ve başvurulan derlemeler.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF ve XAML Namespace bildirimi  
 Ad alanı bildirimi XAML sahip çok sayıda dosya içinde kök etiketi, olduğunu genellikle iki XML ad alanı bildirimi görürsünüz. Genel WPF istemci ilk bildirimi eşler / framework XAML ad alanı varsayılan olarak:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 (Genellikle) için eşleme ayrı XAML ad alanı, ikinci bildirim eşler `x:` önek.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Bu bildirimler arasında ilişki olan `x:` önek eşleştirme XAML dil tanımının bir parçası olan yapı içlerini destekler ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML dil olarak kullanan ve bir sözlüğünü tanımlayan bir uygulaması, XAML için nesne. WPF sözlüğü kullanımları XAML yapı içleri kullanımlarından çok daha yaygın olarak olacağından, WPF sözlük varsayılan olarak eşleştirilir.  
  
 `x:` Ön eki kuralı proje şablonları tarafından izlenen XAML dili yapı içleri desteği için örnek kod ve dil özelliklerinin belgesi içinde [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. XAML ad alanı bile temel WPF uygulamaları için gereklidir, birçok yaygın olarak kullanılan özellikleri tanımlar. Örneğin, kısmi sınıf aracılığıyla bir XAML dosyasını bir arka plan kod birleştirmek için bu sınıf olarak adlandırmalısınız `x:Class` ilgili XAML dosyasının kök öğesindeki özniteliği. Veya, anahtarlı kaynaklar olması gerektiği kadar erişmek istediğiniz XAML sayfası içinde tanımlanmış herhangi bir öğe `x:Key` öznitelik öğe üzerinde söz konusu ayarlayın. Bunlar ve diğer yönleri XAML hakkında daha fazla bilgi için bkz. [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [içinde XAML söz dizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Özel sınıflar ve derlemeleri eşleme  
 Bir dizi belirteçleri kullanarak derlemeleri için XML ad alanları eşleyebilirsiniz bir `xmlns` önek bildirimi, standart WPF ve XAML iç XAML ad alanı ön ekleri nasıl eşleştirildiğini için benzer.  
  
 Aşağıdaki olası adlandırılmış belirteçleri söz dizimini alır ve aşağıdaki değerleri:  
  
 `clr-namespace:` CLR ad alanı öğeleri olarak kullanıma sunmak için genel tür içeren derlemenin içinde bildirilmiş.  
  
 `assembly=` Bazılarını veya tümünü başvurulan içeren derleme [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı. Bu değer genellikle yalnızca yolu değil derlemenin adıdır ve uzantıyı (örneğin, .dll veya .exe) dahil değildir. Bu bütünleştirilmiş kod yolu eşlemek için çalıştığınız XAML içeren proje dosyası içinde bir proje başvurusu olarak oluşturulmalıdır. Sürüm oluşturma ve tanımlayıcı ad imzalama, birleştirmek için `assembly` tarafından tanımlandığı gibi değeri bir dize olabilir <xref:System.Reflection.AssemblyName>, yerine basit bir dize adı.  
  
 Ayıran karakter unutmayın `clr-namespace` ise iki nokta üst üste (:) değerini belirteç ayırıcı karakter `assembly` bir eşittir işareti (=) değerini belirteci. Bu iki belirteç arasında kullanılacak noktalı virgül karakteridir. Ayrıca, herhangi bir boşluğu bildiriminde herhangi bir yere eklemeyin.  
  
### <a name="a-basic-custom-mapping-example"></a>Temel özel eşleme örneği  
 Aşağıdaki kod, örnek özel bir sınıf tanımlar:  
  
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
  
 Bu özel sınıf (gösterilmemiştir) proje ayarlarına göre adlı bir kitaplık içinde sonra derlenmiş `SDKSampleLibrary`.  
  
 Bu özel sınıf başvurmak için genellikle yaptığınız, geçerli proje için bir başvuru olarak dahil etmeniz Visual Studio'da Çözüm Gezgini kullanıcı Arabirimi kullanarak.  
  
 Bir sınıf ve proje ayarlarında buna bir başvuru içeren bir kitaplığınız, XAML, kök öğesi bir parçası olarak aşağıdaki önek eşleştirme ekleyebilirsiniz:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Tümünü bir araya getirmek için tipik varsayılan yanı sıra özel eşleme ve x: eşlemeleri kök etiketi içerir ve ardından önekli başvuru örneklerse XAML verilmiştir `ExampleClass` , kullanıcı arabiriminde:  
  
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
 `assembly` atlanabilir `clr-namespace` başvurulan özel sınıflara başvuran bir uygulama kodu ile aynı bütünleştirilmiş kod içinde tanımlanır. Veya belirtmek için bu durum için bir eşdeğer sözdizimi şöyledir `assembly=`, eşittir işareti izleyen hiçbir dize belirteci.  
  
 Özel sınıflar, aynı derlemede tanımlanan, sayfa kök öğesi olarak kullanılamaz. Kısmi sınıflar eşlenmesi gerekmez; yalnızca uygulama gereksinimlerinize XAML öğeleri olarak bunlara başvurmak istiyorsanız, eşlenmiş bir sayfanın kısmi sınıf olmayan sınıflar.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Bir derlemede XML ad alanları için CLR ad alanlarını eşleme  
 WPF XAML işlemcileri tarafından tek bir XAML ad alanı için birden çok CLR ad alanını eşlemek için kullanılan bir CLR özniteliğinin tanımlar. Bu öznitelik <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, kaynak kodundaki derleme üreten derleme düzeyinde yerleştirilir. WPF derlemenin kaynak kodunu çeşitli ortak ad alanları gibi eşlemek için bu öznitelik kullanan <xref:System.Windows> ve <xref:System.Windows.Controls>, [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanı.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> İki parametre alır: XML/XAML ad alanı adı ve CLR ad alanı adı. Birden fazla <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aynı XML ad alanı için birden çok CLR ad alanını eşlemek için bulunabilir. Eşlenen sonra bu ad üyeleri ayrıca tam nitelenmeden uygun sağlayarak isterseniz başvurulabilir `using` parçalı sınıf gerideki kod sayfasında deyimi. Daha fazla ayrıntı için <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Tasarımcı ad alanları ve diğer ön ekleri XAML şablonları  
 WPF XAML için geliştirme ortamları ve/veya Tasarım araçları ile çalışıyorsanız, tanımlı diğer XAML ad olduğunu fark edebilirsiniz / XAML biçimlendirmesi içinde ekler.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] ön eki genellikle eşlenmiş bir tasarımcı ad alanı kullanan `d:`. WPF için daha yeni proje şablonları, XAML arasında değişim desteklemek için bu XAML ad alanı önceden harita [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] ve diğer tasarım ortamları. Bu tasarım XAML ad alanı arasında gidiş dönüş tasarımcıdaki XAML tabanlı UI tasarım durumunu için kullanılır. Ayrıca özellikleri gibi kullanılır `d:IsDataSource`, çalışma zamanı veri kaynakları bir tasarımcıda etkinleştirin.  
  
 Eşlenen başka bir önek görebileceğiniz `mc:`. `mc:` biçimlendirme uyumluluğu içindir ve mutlaka XAML özgü olmayan bir işaretleme uyumluluğu modeli kullanır. Bir ölçüde, yedekleme uygulamasının, diğer sınırları veya çerçeveleri arasında XAML alışverişi özellikleri kullanılabilir işaretleme uyumluluğu XAML şema bağlamları arasında çalışır, sınırlı modlarında tasarımcıları için uyumluluk sağlamak ve benzeri. Biçimlendirme uyumluluğu kavramları ve WPF birbirleriyle hakkında daha fazla bilgi için bkz. [işaretleme uyumluluğu (mc:) Dil özellikleri](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF ve derleme yükleme  
 WPF için XAML şema içeriği hangi sırayla CLR tanımlı kavramını kullanır WPF uygulaması modelle tümleştirir <xref:System.AppDomain>. Aşağıdaki sırayı nasıl XAML şema içeriği derlemeler yüklemek ya da WPF kullanıma bağlı çalıştırma veya tasarım zamanı türlerini bulmak nasıl yorumlayacağını açıklayan <xref:System.AppDomain> ve diğer etkenlere bağlı.  
  
1.  Yinelemek <xref:System.AppDomain>tüm yönlerini adı ile eşleşen bir zaten yüklü derleme için arama, gelen en son yüklenen derleme başlatılıyor.  
  
2.  Adı nitelenmiş varsa, çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
3.  Kısa ad + tam adı, ortak anahtar belirteci biçimlendirme öğesinden yüklenmiş derleme eşleşiyorsa, bu derleme döndürür.  
  
4.  Çağırmak için kısa ad + ortak anahtar belirteci kullanmanız <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5.  Adı nitelenmemiş ise, çağrı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Adım 3 gevşek XAML kullanmaz; yüklenen gelen derleme yok.  
  
 WPF (XamlBuildTask oluşturulur) için derlenmiş XAML zaten yüklenmiş derlemeleri kullanmayan <xref:System.AppDomain> (1. adım). 5. Adım uygulanamaz Ayrıca, ad hiçbir zaman XamlBuildTask çıktısını nitelenmemiş olmalıdır.  
  
 BAML nitelenmemiş derleme adları da içermemelidir, ancak tüm adımlar, derlenmiş BAML (PresentationBuildTask oluşturulan) kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları anlama](https://go.microsoft.com/fwlink/?LinkId=98069)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
