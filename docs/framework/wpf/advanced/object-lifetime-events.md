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
ms.openlocfilehash: c0858a0194bc0e9efa60a42d4029bdba9f4f3fef
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458581"
---
# <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları
Bu konuda, oluşturma, kullanma ve yok etme bir nesne ömrü içindeki aşamaları belirten belirli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları açıklanmaktadır.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu başlığı altında, bağımlılık özelliklerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarında var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsaymış olursunuz. Bu konudaki örnekleri izlemek için, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ( [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları nasıl yazacağınız hakkında bilgi sahibi olmanız gerekir.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları  
 Microsoft .NET Framework yönetilen kodundaki tüm nesneler, yaşam, oluşturma, kullanma ve yok etme aşamalarını benzer bir dizi aşamadan geçer. Birçok nesnenin Ayrıca, yok etme aşamasının bir parçası olarak oluşan sonlandırma aşaması vardır. nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneler, daha özel olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe olarak tanımlanan görsel nesneler, ayrıca nesne ömrü yaygın bir aşamaları kümesi de vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama ve uygulama modelleri bu aşamaları bir dizi olay olarak sunar. Yaşam süresi olaylarına göre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört ana nesne türü vardır; Genel, pencere öğeleri, gezinti konakları ve uygulama nesneleri öğeleri. Windows ve gezinti konakları Ayrıca görsel nesnelerin daha büyük gruplandırmasına (öğeler) sahiptir. Bu konu, tüm öğeler için ortak olan ömür olaylarını açıklar ve ardından uygulama tanımları, pencereler veya gezinti konakları için uygulanan daha belirgin olanları tanıtır.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Öğeler için ortak ömür olayları  
 Herhangi bir WPF framework düzeyi öğesi (<xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>türetmede kullanılan nesneler) üç ortak ömür olayına sahiptir: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>ve <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Başlatıldı  
 <xref:System.Windows.FrameworkElement.Initialized> önce oluşturulur ve kabaca, oluşturucusunun çağrısıyla nesnenin başlatılmasına karşılık gelir. Olayı başlatmaya yanıt olarak yapıldığından, nesnenin tüm özelliklerinin ayarlandığı garanti edilir. (Özel durum, Dinamik kaynaklar veya bağlama gibi ifade kullanımlarıdır; bunlar değerlendirilmeyecek ifadeler olur.) Tüm özelliklerin ayarlandığı gereksinimin bir sonucu olarak, İşaretlemede tanımlanan iç içe yerleştirilmiş öğeler tarafından oluşturulan <xref:System.Windows.FrameworkElement.Initialized> sırası, önce öğe ağacındaki en derin öğelerin, sonra da köke doğru olan üst öğeler sırasıyla ortaya çıkar. Bu sıra, üst-alt ilişkileri ve kapsamasının Özellik olmasından ve bu nedenle, özelliği dolduran alt öğeler de tamamen başlatıldığından üst öğe başlatmayı bildiremeyecek.  
  
 <xref:System.Windows.FrameworkElement.Initialized> olayına yanıt olarak işleyiciler yazarken, işleyicinin eklendiği öğe ağacındaki (mantıksal ağaç veya görsel ağaç) tüm diğer öğelerin, özellikle de üst öğe olduğunu göz önünde bulundurmanız gerekir. ög. Üye değişkenleri null olabilir veya veri kaynakları henüz temeldeki bağlama tarafından doldurulmayabilir (ifade düzeyinde bile).  
  
### <a name="loaded"></a>Yüklü  
 <xref:System.Windows.FrameworkElement.Loaded> sonraki bir adımda oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> olayı son işlemeden önce tetiklenir, ancak düzen sistemi, işleme için gereken tüm değerleri hesapladıktan sonra. <xref:System.Windows.FrameworkElement.Loaded>, bir öğenin içinde yer aldığı mantıksal ağacın tamamlanmasını ve HWND ve işleme yüzeyini sağlayan bir sunum kaynağına bağlanmasını gerektirir. Standart veri bağlama (diğer özellikler veya doğrudan tanımlanmış veri kaynakları gibi yerel kaynaklara bağlama) <xref:System.Windows.FrameworkElement.Loaded>önce gerçekleşmeyecektir. Zaman uyumsuz veri bağlama (dış veya dinamik kaynaklar) oluşmuş olabilir, ancak zaman uyumsuz doğası tanımına göre oluşma garantisi garanti edilemez.  
  
 <xref:System.Windows.FrameworkElement.Loaded> olayının oluşturulduğu mekanizma <xref:System.Windows.FrameworkElement.Initialized>farklıdır. <xref:System.Windows.FrameworkElement.Initialized> olay, tamamlanmış bir öğe ağacı tarafından doğrudan koordinasyon olmadan öğesi öğesi tarafından tetiklenir. Buna karşılık, <xref:System.Windows.FrameworkElement.Loaded> olayı tüm öğe ağacının tamamında (özellikle, mantıksal ağaç) eşgüdümlü bir çaba olarak oluşturulur. Ağaçtaki tüm öğeler yüklü olarak kabul edildiği bir durumda olduğunda, <xref:System.Windows.FrameworkElement.Loaded> olay önce kök öğe üzerinde tetiklenir. <xref:System.Windows.FrameworkElement.Loaded> olay, her alt öğe üzerinde büyük ölçüde oluşturulur.  
  
> [!NOTE]
> Bu davranış, yönlendirilmiş bir olay için superficially benzer tünelleme gösterebilir. Ancak, olaydan olaya hiçbir bilgi taşınmaz. Her her öğe <xref:System.Windows.FrameworkElement.Loaded> olayını işleme fırsatına sahiptir ve olay verilerinin işlenmiş olarak işaretlenmesi bu öğenin ötesinde hiçbir etkiye sahip değildir.  
  
### <a name="unloaded"></a>Kaldırıldı  
 <xref:System.Windows.FrameworkElement.Unloaded> en son oluşturulur ve sunu kaynağı ya da kaldırılmakta olan görsel üst öğe tarafından başlatılır. <xref:System.Windows.FrameworkElement.Unloaded> başlatıldığında ve işlenirse, olay kaynağı üst öğesi olan (<xref:System.Windows.FrameworkElement.Parent%2A> özelliği tarafından belirlendiği şekilde) veya mantıksal ya da görsel ağaçlarda yukarı eklenen herhangi bir öğe önceden kaldırılmış olabilir, bu da veri bağlama, kaynak başvuruları ve stiller normal veya son bilinen çalışma zamanı değerine ayarlanamaz.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Ömür olayları uygulama modeli öğeleri  
 Öğeler için ortak ömür olaylarını oluşturmak şu uygulama modeli öğeleridir: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>ve <xref:System.Windows.Controls.Frame>. Bunlar, ortak ömür olaylarını belirli amaçlarına uygun ek olaylarla genişletir. Bunlar aşağıdaki konumlarda ayrıntılı olarak ele alınmıştır:  
  
- <xref:System.Windows.Application>: [uygulama yönetimine genel bakış](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [WPF Windows 'A genel bakış](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>ve <xref:System.Windows.Controls.Frame>: [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
