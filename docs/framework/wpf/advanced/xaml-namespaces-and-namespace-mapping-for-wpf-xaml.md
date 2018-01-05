---
title: "WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f152f8cdf459f920d723df66756af680b4bcea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>WPF XAML için XAML Ad Alanları ve Ad Alanı Eşlemesi
Bu konuda daha fazla varlığını ve sık bir WPF XAML dosyasının kök etiketinde bulunan iki XAML ad uzayı eşlemesinin amacını açıklanmaktadır. Ayrıca, benzer eşlemeleri kullanan kendi kodunuzda ve/veya ayrı derlemeler içinde tanımlanan öğeler için üretmek nasıl açıklanır.  
  
  
## <a name="what-is-a-xaml-namespace"></a>XAML Namespace nedir?  
 XAML ad uzayı gerçekten bir XML ad alanı kavramını uzantısıdır. XAML ad uzayı belirtmenin teknikleri XML ad alanı söz dizimi, birden çok ad alanını aynı biçimlendirme kaynağından başvurmak için bir yol sağlamak için önekleri kullanarak ad alanı tanımlayıcıları olarak URI'ler kullanmanın kuralı kullanır ve benzeri. XML ad alanı XAML tanımına eklenen birincil XAML ad uzayı benzersizlik hem bir bir kapsam biçimlendirme kullanımlar için anlamına gelir ve ayrıca nasıl biçimlendirme varlıklarının olası belirli CLR ad alanları tarafından yedeklenir ve başvurulan etkilediğini kavramdır derlemeler. İkinci değerlendirme ayrıca XAML şema içeriği kavramı tarafından etkilenir. Ancak WPF XAML ad uzayları ile nasıl çalıştığı amacıyla, genellikle XAML ad uzayları varsayılan XAML ad uzayı, XAML dili ad alanı ve, XAML biçimlendirme doğrudan belirli destekleyen CLR tarafından eşleştirilen herhangi başka XAML ad uzayları açısından düşünebilirsiniz ad alanları ve başvurulan derlemeler.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF ve XAML Namespace bildirimleri  
 Ad alanı bildirimlerinde çoğu XAML dosyasının kök etiketinde, olduğunu genellikle iki XML ad alanı bildirimi görürsünüz. İlk bildirim genel WPF istemci eşlemeleri / framework XAML ad uzayı varsayılan olarak:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 İkinci bildirim (genellikle) için eşleme ayrı XAML ad alanı, eşler `x:` öneki.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Bu bildirimler arasındaki ilişki olduğu `x:` önek eşleştirme destekler XAML dili tanımının bir parçası olan iç bilgileri ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML dil olarak kullanan ve bir sözlüğünü tanımlayan bir uygulaması, XAML için nesneleri. WPF sözlüğü kullanımları XAML yapı kullanımlarından çok daha yaygın olduğundan, WPF sözlüğü varsayılan olarak eşlenir.  
  
 `x:` Öneki kuralı proje şablonları tarafından izlenen XAML dili yapı desteği için örnek kod ve dil özelliklerinin belgesi içinde [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. XAML ad uzayı bile temel WPF uygulamaları için gerekli olan birçok yaygın olarak kullanılan özellikleri tanımlar. Örneği için bir parçalı sınıf aracılığıyla XAML dosyasına tüm arka plan kodu katılmak için bu sınıf olarak adı olmalıdır `x:Class` ilgili XAML dosyasının kök öğesinin özniteliği. Veya, anahtarlı kaynaklar olması gerektiği kadar erişmek istediğiniz XAML sayfası içinde tanımlanan herhangi bir öğe `x:Key` özniteliğini öğede söz konusu ayarlayın. Bunlar ve diğer yönlerini XAML hakkında daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Özel sınıfları ve derlemeleri eşleme  
 XML ad alanları içindeki belirteç dizisini kullanarak derlemeler eşleyebilirsiniz bir `xmlns` önek bildirimi, standart WPF ve XAML yapı içi XAML ad uzayları ön eklerin nasıl eşlendiğini için benzer.  
  
 Aşağıdaki olası adlandırılmış belirteçleri sözdizimi alır ve aşağıdaki değerleri:  
  
 `clr-namespace:`Öğeler olarak sunmak için ortak türleri içeren bütünleştirilmiş kodun içinde CLR ad alanı bildirimi.  
  
 `assembly=`Bazılarını veya tümünü başvurulan içeren bütünleştirilmiş kodun [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı. Bu değer genellikle yolu değil derleme adı ve uzantısı (örneğin, .dll veya .exe) içermez. Bu derleme yolu eşlemeye çalıştığınız XAML içeren proje dosyası proje başvuru olarak oluşturulmalıdır. Sürüm oluşturma ve güçlü ad imzalama, birleştirmek için `assembly` tarafından tanımlanan değeri bir dize olabilir <xref:System.Reflection.AssemblyName>, basit bir dize adı yerine.  
  
 Ayıran karakter unutmayın `clr-namespace` ancak iki nokta üst üste (:) değerinden belirteci ayıran karakter `assembly` bir eşittir işareti (=) değerinden belirteci. Bu iki belirteç arasında kullanmak için noktalı virgül karakteridir. Ayrıca, tüm boşluk bildiriminde herhangi bir yere içermez.  
  
### <a name="a-basic-custom-mapping-example"></a>Temel özel eşleme örneği  
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
  
 Bu özel bir sınıf sonra proje ayarı (gösterilmez) başına adlı bir kitaplık içinde derlenmiş `SDKSampleLibrary`.  
  
 Bu özel bir sınıf başvurmak için genellikle yaptığınız, geçerli projeniz için bir başvuru olarak dahil etmeniz Visual Studio'da Çözüm Gezgini UI kullanarak.  
  
 Bir sınıf ve proje ayarlarında bir başvuru içeren bir kitaplık sahip olduğunuza göre XAML, kök öğesinde bir parçası olarak aşağıdaki öneki eşlemesini ekleyebilirsiniz:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Hepsini bir araya getirin için tipik varsayılan birlikte özel eşleme ve x: eşlemeleri kök etiketinde içerir ve ardından örneği oluşturmak için önekli başvuru kullanan XAML aşağıdadır `ExampleClass` , kullanıcı arabiriminde:  
  
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
 `assembly`atlanabilir `clr-namespace` başvurulan özel sınıflara başvuran uygulama kodu aynı bütünleştirilmiş içinde tanımlanan. Veya belirtmek için bu durum için eşdeğer bir sözdizimi şöyledir `assembly=`, eşittir işaretinden dize belirteci olmadan.  
  
 Özel sınıflar aynı bütünleştirilmiş kodda tanımlanmış ise sayfanın kök öğesi olarak kullanılamaz. Kısmi sınıflar eşlenmesi gerekmez; yalnızca, uygulama bunları XAML öğeleri olarak başvurmak istiyorsanız eşlenmesi gerekir sayfasının parçalı sınıf olmayan sınıflar.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Derleme XML ad alanları için CLR ad alanlarını eşleme  
 WPF XAML işlemcileri tarafından tek bir XAML ad alanı için birden çok CLR ad alanını eşlemek için kullanılan bir CLR özniteliği tanımlar. Bu öznitelik <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, derleme üreten kaynak kodu derleme düzeyinde yerleştirilir. WPF bütünleştirilmiş kaynak kodu çeşitli ortak ad alanları gibi eşlemek için bu öznitelik kullanır <xref:System.Windows> ve <xref:System.Windows.Controls>, [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanı.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> İki parametre alır: XML/XAML ad alanı adı ve CLR ad alanı adı. Birden fazla <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aynı XML ad alanı için birden çok CLR ad alanını eşlemek için bulunabilir. Eşlenen sonra bu ad alanları üyeleri de tam nitelemesiz uygun sağlayarak isterseniz başvurulabilir `using` parçalı sınıf arka plan kod sayfası deyiminde. Daha fazla ayrıntı için bkz: <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Tasarımcı ad alanları ve XAML şablonlarından diğer önekler  
 WPF XAML için geliştirme ortamları ve/veya Tasarım araçları ile çalışıyorsanız, diğer tanımlı XAML ad uzayları olduğunu fark edebilirsiniz / önekleri içinde XAML biçimlendirme.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]genellikle önekine eşlenen Tasarımcı bir ad alanı kullanır `d:`. WPF için daha yeni proje şablonları arasında XAML değişim desteklemek için bu XAML ad uzayı önceden eşleme [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] ve diğer tasarım ortamları. Bu tasarım XAML ad uzayı arasında gidiş dönüş XAML tabanlı UI Tasarımcısı'nda gelirken tasarım durumunu aktarmak için kullanılır. Ayrıca özellikleri gibi kullanılır `d:IsDataSource`, çalışma zamanı veri kaynakları bir Tasarımcısı'nda etkinleştirin.  
  
 Eşlenen başka bir önek görebilirsiniz `mc:`. `mc:`biçimlendirme uyumluluğu içindir ve mutlaka XAML özgü olmayan bir biçimlendirme uyumluluğu modeli kullanır. Bazı ölçüde özellikleri XAML çerçeveler arasında ya da diğer sınırları yedekleme uygulamasının, exchange için kullanılan biçimlendirme uyumluluğu XAML şema bağlamları arasında iş, sınırlı modlarında tasarımcıları için uyumluluk sağlamak ve benzeri. Biçimlendirme uyumluluğu kavramları ve WPF ile ilişkili nasıl oldukları hakkında daha fazla bilgi için bkz: [Uyumluluk Biçimlendirme (mc:) Dil özellikleri](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF ve derleme yükleme  
 WPF XAML şema bağlamının sırayla CLR tanımlı kavramı kullanan WPF uygulaması modelle tümleştirir <xref:System.AppDomain>. XAML şema içeriği nasıl derlemelerini yüklemek veya WPF kullanım dayanarak çalıştırma veya tasarım zamanı türlerini bulmak yorumlaması aşağıdaki sırayı açıklar <xref:System.AppDomain> ve diğer etkenlere bağlı.  
  
1.  Yinelemek <xref:System.AppDomain>adı tüm yönlerini eşleşen bir önceden yüklenen derleme için arayan, gelen en son yüklenen derleme başlatılıyor.  
  
2.  Ad niteliği onaylanırsa, çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
3.  Kısa ad + tam adı, ortak anahtar belirteci işaretleme yüklenmesinden derleme eşleşiyorsa bu derleme döndür.  
  
4.  Çağırmak için kısa ad + ortak anahtar belirteci kullanın <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5.  Nitelenmemiş ise, çağrı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Gevşek XAML adım 3 kullanmaz; yüklenen yeri derlemesi bulunmuyor.  
  
 Derlenmiş XAML (XamlBuildTask oluşturulan) WPF için daha önce yüklenmiş derlemelerden kullanmaz <xref:System.AppDomain> (adım 1). Adım 5 uygulanamaz Ayrıca, ad hiçbir zaman XamlBuildTask çıktısını nitelenmemiş olmalıdır.  
  
 BAML ayrıca nitelenmemiş derleme adları içermemelidir karşın tüm adımları derlenmiş BAML (PresentationBuildTask oluşturulan) kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanlarını anlama](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
