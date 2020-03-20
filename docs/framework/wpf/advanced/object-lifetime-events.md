---
title: Nesne Yaşam Süresi Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141113"
---
# <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları
Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir nesne nin oluşturma, kullanma ve imha yaşam ını gösteren belirli olayları açıklar.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özelliklerine Genel [Bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsayar. Bu konudaki örnekleri takip etmek için, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [(Bkz. XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)ve uygulama yazmayı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bilmeniz gerekir.  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları  
 Microsoft .NET Framework yönetilen koddaki tüm nesneler benzer yaşam, oluşturma, kullanma ve imha aşamalarından geçer. Birçok nesne de imha aşamasının bir parçası olarak ortaya çıkan yaşamın bir sonlandırma aşaması var. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nesneler, özellikle öğe olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan görsel nesneler, nesne yaşamının ortak aşamaları kümesi de var. Programlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve uygulama modelleri bu aşamaları bir dizi olay olarak ortaya çıkarır. Yaşam boyu olaylarla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ilgili olarak dört ana nesne türü vardır; genel olarak öğeler, pencere öğeleri, gezinti ana bilgisayarları ve uygulama nesneleri. Windows ve gezinti ana bilgisayarları da görsel nesnelerin (öğelerin) daha büyük gruplandırma içindedir. Bu konu, tüm öğeler için ortak olan yaşam boyu olayları açıklar ve uygulama tanımları, windows veya gezinti ana bilgisayarlar için geçerli olan daha spesifik olanları tanıtır.  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>Öğeler için Ortak Yaşam Boyu Olaylar  
 Herhangi bir WPF çerçeve düzeyinde öğe (bu <xref:System.Windows.FrameworkElement> nesneler <xref:System.Windows.FrameworkContentElement>ya da) üç <xref:System.Windows.FrameworkElement.Initialized> <xref:System.Windows.FrameworkElement.Loaded>ortak <xref:System.Windows.FrameworkElement.Unloaded>yaşam boyu olaylar vardır: , ve .  
  
### <a name="initialized"></a>Başlatıldı  
 <xref:System.Windows.FrameworkElement.Initialized>önce yükseltilir ve kabaca nesnenin oluşturucuya çağrı ile başlatılmasına karşılık gelir. Olay başlatmaya yanıt olarak gerçekleştiğinden, nesnenin tüm özelliklerinin ayarlandığı garanti edilir. (Bir özel durum dinamik kaynaklar veya bağlama gibi ifade kullanımları; bunlar değerlendirilmemiş ifadeler olacaktır.) Tüm özelliklerin ayarlandığı gereksiniminin <xref:System.Windows.FrameworkElement.Initialized> bir sonucu olarak, biçimlendirmede tanımlanan iç içe geçen öğeler tarafından yükseltilme sırası, önce öğe ağacındaki en derin öğeler, sonra köke doğru ana öğeler sırasına göre ortaya çıkar. Bu sıra, üst-alt ilişkileri ve kapsama özellikleri ve bu nedenle üst özelliği dolduran alt öğeleri de tamamen başharfe kadar başlatma bildiremez olmasıdır.  
  
 <xref:System.Windows.FrameworkElement.Initialized> Olaya yanıt olarak işleyiciler yazarken, işleyicinin bağlı olduğu yerdeki öğe ağacındaki (mantıksal ağaç veya görsel ağaç) diğer tüm öğelerin, özellikle de üst öğelerin oluşturulduğunun garantisi olmadığını göz önünde bulundurmanız gerekir. Üye değişkenler null olabilir veya veri kaynakları henüz temel bağlama (ifade düzeyinde bile) tarafından doldurulmuş olmayabilir.  
  
### <a name="loaded"></a>Yüklü  
 <xref:System.Windows.FrameworkElement.Loaded>sonraki yükseltilir. Olay <xref:System.Windows.FrameworkElement.Loaded> son işleme önce yükseltilir, ancak düzen sistemi işleme için gerekli tüm değerleri hesapladı sonra. <xref:System.Windows.FrameworkElement.Loaded>bir öğenin içerdiği mantıksal ağacın tam olduğunu ve HWND ve işleme yüzeyini sağlayan bir sunu kaynağına bağlanmasını gerektirir. Standart veri bağlama (diğer özellikler veya doğrudan tanımlanmış veri kaynakları gibi yerel <xref:System.Windows.FrameworkElement.Loaded>kaynaklara bağlama) önce oluşmuş olacak. Eşzamanlı veri bağlama (dış veya dinamik kaynaklar) oluşmuş olabilir, ancak onun eşzamanlı doğasının tanımı gereği meydana geldiği garanti edilemez.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Olayın yükseltilme <xref:System.Windows.FrameworkElement.Initialized>mekanizması' ndan farklıdır. Olay <xref:System.Windows.FrameworkElement.Initialized> tamamlanan bir öğe ağacı tarafından doğrudan bir koordinasyon olmadan, eleman tarafından yükseltilir. Buna karşılık, <xref:System.Windows.FrameworkElement.Loaded> olay tüm öğe ağacı (özellikle, mantıksal ağaç) boyunca koordine li bir çaba olarak yükseltilir. Ağaçtaki tüm öğeler yüklenmiş olarak kabul edilen bir <xref:System.Windows.FrameworkElement.Loaded> durumda olduklarında, olay ilk olarak kök öğesi üzerinde yükseltilir. Olay <xref:System.Windows.FrameworkElement.Loaded> daha sonra her alt öğe üzerinde art arda yükseltilir.  
  
> [!NOTE]
> Bu davranış, yönlendirilmiş bir olay için tünel leme yüzeysel benzer olabilir. Ancak, olaydan olaya hiçbir bilgi taşınır. Her öğenin her zaman <xref:System.Windows.FrameworkElement.Loaded> kendi olayını işlemek için fırsat vardır ve işlenir gibi olay verileri işaretleme bu öğenin ötesinde hiçbir etkisi yoktur.  
  
### <a name="unloaded"></a>Kaldırıldı  
 <xref:System.Windows.FrameworkElement.Unloaded>en son yükseltilir ve sunu kaynağı veya kaldırılan görsel üst tarafından başlatılır. Yükseltilip <xref:System.Windows.FrameworkElement.Unloaded> işlendiğinde, olay kaynağı üst öğesi olan öğe <xref:System.Windows.FrameworkElement.Parent%2A> (özellik tarafından belirlendiği gibi) veya mantıksal veya görsel ağaçlardaki herhangi bir öğe yukarı doğru zaten ayarlanmamış olabilir, yani veri bağlama, kaynak başvuruları ve stilleri normal veya bilinen son çalışma zamanı değerine ayarlanmamış olabilir.  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>Yaşam Boyu Olaylar Uygulama Modeli Elemanları  
 Öğeler için ortak yaşam boyu olaylar üzerine bina <xref:System.Windows.Application> <xref:System.Windows.Window>aşağıdaki <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>uygulama <xref:System.Windows.Controls.Frame>modeli öğeleri şunlardır: , , , ve . Bunlar, belirli amaçlarıyla ilgili ek olaylarla ortak yaşam boyu olayları genişletir. Bunlar aşağıdaki konumlarda ayrıntılı olarak ele alınmıştır:  
  
- <xref:System.Windows.Application>: [Uygulama Yönetimi Genel Bakış](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [WPF Windows Genel Bakış](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>ve <xref:System.Windows.Controls.Frame>: [Navigasyona Genel Bakış](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
