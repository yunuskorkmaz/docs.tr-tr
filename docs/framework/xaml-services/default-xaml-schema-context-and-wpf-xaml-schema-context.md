---
title: "Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: ccb89b67b222c11695131a1aa8423b89df1c9a70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Varsayılan XAML Şema İçeriği ve WPF XAML Şema İçeriği
XAML şema içeriği belirli bir XAML sözlük kullanan XAML üretim davranışı nasıl türü eşlemesi çözümler, derlemeler nasıl yüklenir, nasıl belirli okuyucu ve yazıcı dahil olmak üzere, yazma nesnesi ile nasıl etkileşim kurduğu niteleyen kavramsal bir varlıktır ayarları yorumlanır. Bu konu, .NET Framework XAML hizmetlerinde ve CLR türü sistemi temelinde ilişkili varsayılan XAML şema içeriği özelliklerini açıklar. Bu konu ayrıca WPF için kullanılan XAML şema içeriği açıklar.  
  
## <a name="default-xaml-schema-context"></a>Varsayılan XAML şema içeriği  
 .NET framework XAML hizmetlerinde hem uygular ve varsayılan XAML şema içeriği kullanır. Varsayılan XAML şema içeriği davranışı her zaman API'si, tam olarak görünür değil <xref:System.Xaml.XamlSchemaContext> sınıfı. Bununla birlikte, çoğu durumda varsayılan XAML şema içeriği etkileyen XAML tür sistemi üyeleri gibi ortak API'si aracılığıyla observable davranıştır <xref:System.Xaml.XamlMember> veya <xref:System.Xaml.XamlType>, ya da XAML okuyucuları ve kullanmakta olduğunuz XAML yazıcılarının açık API'ler aracılığıyla Varsayılan XAML şema içeriği.  
  
 Oluşturabileceğiniz bir <xref:System.Xaml.XamlSchemaContext> varsayılan davranışı çağırarak yalıtır <xref:System.Xaml.XamlSchemaContext> Oluşturucusu. Bu varsayılan XAML şema içeriği açıkça oluşturur. XAML okuyucu ya da XAML yazan açıkça yararlanabilir mi API'lerini kullanarak başlatmak, aynı varsayılan XAML şema içeriği örtülü olarak oluşturulan bir <xref:System.Xaml.XamlSchemaContext> giriş parametresi.  
  
 Varsayılan XAML şema içeriği CLR yansıma türü eşleme davranışını için kullanır. Bu tanımlama CLR inceleniyor içerir <xref:System.Type>ve ilgili <xref:System.Reflection.PropertyInfo> veya <xref:System.Reflection.MethodInfo>. Ayrıca, CLR attribution türleri veya üyeleri XAML türü veya CLR türü yedekleme kullanan XAML üye bilgi için ayrıntıları doldurun için kullanılır. Varsayılan XAML şema içeriği türü sistem uzantısı teknikleri gibi gerektirmez `Invoker` gerekli bilgileri CLR türü sistemde kullanılabilen olduğundan desen.  
  
 Mantığı yüklenirken derleme için varsayılan XAML şema içeriği çoğunlukla XAML ad eşleştirmelerinde sağlanan derleme değerleri kullanır. Ayrıca, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> iç türleri yükleme gibi senaryolar için yüklemek için bir derleme ipucu.  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML şema içeriği  
 WPF uygulaması varsayılan olmayan XAML şema bağlamı uygulama tarafından sunulan özellikler türlerini ilginç bir çizimi sağladığından WPF XAML şema içeriği bu konuda açıklanan. Ayrıca, XAML şema içeriği kavramı çok WPF XAML adresleri WPF belgelerinde ele alınmamıştır; XAML şema içeriği etkinleştiren davranışı yalnızca varsayılan XAML şema içeriği nasıl çalıştığı ile ilgili bir tartışma bütünleştirdiyseniz tam olarak anlaşılabilir olabilir. WPF XAML şema içeriği aşağıdaki davranışı uygular.  
  
 **Arama geçersiz kılar:** WPF XAML için birkaç içerik modelleri sahip olmadan işlev XAML İçerik özellikleri olduğu <xref:System.Windows.Markup.ContentPropertyAttribute> öznitelikli. <xref:System.Xaml.XamlType.LookupContentProperty%2A>WPF için bu davranışı geçersiz kılmalarını.  
  
 **WPF ifadeler için erteleme:** WPF çalışma zamanı bağlam kullanılabilir hale gelene kadar bir değer erteleneceği birkaç ifade sınıfları özellikleri. Ayrıca, şablonu genişletme üzerinde erteleme teknikleri kullanır bir çalışma zamanı davranıştır.  
  
 **Sistem arama iyileştirmelerini yazın:** WPF devral yüzlerce WPF tanımlı sınıflar için temel sınıf üyesi tanımları dahil olmak üzere bir kapsamlı XAML dağarcığı ve nesne modeli vardır. Ayrıca, WPF kendisini birkaç derlemeler arasında yayılır. WPF arama tabloları ve başka teknikler kullanarak kendi Arama türünde en iyi duruma getirir. Varsayılan XAML şema içeriği ve tür CLR tabanlı arama performans artışı sağlar. Burada türleri arama tablosunda yok durumlarda davranış varsayılan XAML şema içeriği benzer XAML şema içeriği teknikler kullanır.  
  
 **Uzantı XamlType ve XamlMember:** WPF özelliği kavramlarını bağımlılık özellikleri ile genişletir ve olay kavramları yönlendirilmiş olayları. Bu kavramları daha fazla görünürlük XAML işlemleri için vermek için WPF genişletir <xref:System.Xaml.XamlType> ve <xref:System.Xaml.XamlMember>ve rapor bağımlılık özelliği ve olay özelliklerini yönlendirilen iç özellikleri ekler.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>WPF XAML şema içeriği erişme  
 WPF tabanlı XAML teknikleri kullanıyorsanız <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> veya <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, WPF XAML şema içeriği bu XAML okuyucu ve XAML yazan uygulamaları kullanılıyor.  
  
 WPF XAML şema içeriği ile diğer XAML okuyucu veya başlatamadı. XAML yazan uygulamaları kullanıyorsanız, çalışan bir WPF XAML şema bağlamından almak mümkün olabilir <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Daha sonra bu değeri kullanın diğer API için başlatma olarak kullanabilirsiniz bir <xref:System.Xaml.XamlSchemaContext>. Örneğin, çağırabilirsiniz <xref:System.Xaml.XamlXmlReader.%23ctor%2A> başlatma ve WPF XAML şema içeriği geçişi için. Veya WPF XAML şema içeriği XAML tür sistem işlemleri için kullanabilirsiniz. Bu yapı başlatılması içerebilir bir <xref:System.Xaml.XamlType> veya <xref:System.Xaml.XamlMember>, veya çağırma <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 WPF XAML belirli yönlerini saf bir XAML düğüm akış perspektiften erişirse, WPF framework özelliklerden bazıları henüz işlem değil olduğunu unutmayın. Örneğin, WPF şablonları denetimleri için henüz uygulanmaz. Bu nedenle tam görsel ağaç ile doldurulmuş olabilir, çalışma zamanında bir özellik erişirseniz, yalnızca bir şablon başvuruda bulunan bir özellik değeri görebilirsiniz. WPF biçimlendirme uzantıları için sağlanan hizmet bağlamı aynı zamanda bir çalışma zamanı olmayan durumdan sağladıysanız doğru olmayabilir ve özel durumları bir nesne grafiğinin yazmaya çalışırken neden olabilir.  
  
## <a name="xaml-and-assembly-loading"></a>XAML ve derleme yükleme  
 XAML ve .NET Framework XAML Hizmetleri için yükleme derleme tümleştirir CLR tanımlı kavramıyla <xref:System.AppDomain>. Derlemeleri yükleme veya türlerini çalıştırma veya tasarım zamanı kullanılmasına göre bulmak nasıl bir XAML şema içeriği yorumlar <xref:System.AppDomain> ve diğer etkenlere bağlı. Mantığı XAML gevşek XAML için XAML okuyucu olmasına bağlı olarak biraz daha farklı, uygun bir DLL tarafından içine derlenmiş XAML `XamlBuildTask`, veya BAML WPF tarafından 's üretilen `PresentationBuildTask`.  
  
 WPF XAML şema bağlamının sırayla kullanan WPF uygulaması modelle tümleştirir <xref:System.AppDomain> WPF uygulaması ayrıntıları diğer etkenlere yanı sıra.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>XAML okuyucu giriş (gevşek XAML)  
  
1.  XAML şema içeriği dolaşır <xref:System.AppDomain> adı tüm yönlerini eşleşen bir önceden yüklenen derleme için arayan uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o bütünleştirilmiş kod çözümlemesi için kullanılır.  
  
2.  CLR üzerinde aşağıdaki teknikler birini alarak Aksi halde, <xref:System.Reflection.Assembly> API, bir derlemeyi yüklemek için kullanılır:  
  
    -   Adı eşlemede nitelikleri karşılıyorsa, çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
    -   Önceki adım başarısız olursa, kısa bir ad (ve ortak anahtar belirteci varsa) kullanmak çağırmak için <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Eşlemede nitelenmemiş ise, çağrı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask`için kullanılan [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] ve [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
 Aracılığıyla bütünleştirilmiş koduna başvuruyor Not `XamlBuildTask` her zaman tam olur.  
  
1.  Çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
2.  Önceki adım başarısız olursa, kısa bir ad (ve ortak anahtar belirteci varsa) kullanmak çağırmak için <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Derleme yükleme BAML için için iki yön vardır: bir bileşen olarak BAML içeren ilk derlemesi yüklenirken ve BAML üretim tarafından başvurulan tüm türlerinin türü destekleyen derlemeleri yükleme.  
  
##### <a name="assembly-load-for-initial-markup"></a>Derleme yükleme ilk biçimlendirme için:  
 Derleme biçimlendirmeden yüklemek için her zaman nitelenmemiş başvurudur.  
  
1.  WPF XAML şema içeriği dolaşır <xref:System.AppDomain> adı tüm yönlerini eşleşen bir önceden yüklenen derleme için arayan WPF uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o bütünleştirilmiş kod çözümlemesi için kullanılır.  
  
2.  Önceki adım başarısız olursa, kısa bir ad (ve ortak anahtar belirteci varsa) kullanmak çağırmak için <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Derleme başvurularını BAML türlerine göre:  
 Derleme başvurularını BAML üretimde kullanılan türleri için her zaman bir derleme görevi çıkış olarak tam olarak nitelenmiş.  
  
1.  WPF XAML şema içeriği dolaşır <xref:System.AppDomain> adı tüm yönlerini eşleşen bir önceden yüklenen derleme için arayan WPF uygulamasının en son başlatma derleme yüklendi. Bir eşleşme bulunursa, o bütünleştirilmiş kod çözümlemesi için kullanılır.  
  
2.  Aksi takdirde, aşağıdaki teknikler biri bir derlemeyi yüklemek için kullanılır:  
  
    -   Çağrı <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> tam adı.  
  
    -   Bir kısa ad + BAML yüklenmesinden derleme eşleşen ortak anahtar belirteci birleşimi, bu derleme kullanın.  
  
    -   Çağırmak için kısa ad + ortak anahtar belirteci kullanın <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML düğüm akış yapılarını ve kavramlarını anlama](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
