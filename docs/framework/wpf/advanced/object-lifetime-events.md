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
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933497"
---
# <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları
Bu konu, bir nesne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturma, kullanma ve yok etme ömründe aşamaları belirten belirli olayları açıklar.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarda mevcut bağımlılık özelliklerinin bir tüketicisinin perspektifinden bağımlılık özelliklerini anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) konusunu okuduğunuzu varsaymış olursunuz. Bu konudaki örnekleri izlemek için, ayrıca ( [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [xaml 'ye Genel Bakış (WPF)](xaml-overview-wpf.md)) anlamanız ve uygulamaların nasıl yazılacağını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bilmeniz gerekir.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları  
 Microsoft .NET Framework yönetilen kodundaki tüm nesneler, yaşam, oluşturma, kullanma ve yok etme aşamalarını benzer bir dizi aşamadan geçer. Birçok nesnenin Ayrıca, yok etme aşamasının bir parçası olarak oluşan sonlandırma aşaması vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nesneler, daha özel olarak öğe olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan görsel nesneler, ayrıca nesne ömrü yaygın bir aşamaları kümesi de vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programlama ve uygulama modelleri bu aşamaları bir dizi olay olarak sunar. ' De [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yaşam süresi olaylarına göre dört ana nesne türü vardır; genel, pencere öğeleri, gezinti konakları ve uygulama nesneleri. Windows ve gezinti konakları Ayrıca görsel nesnelerin daha büyük gruplandırmasına (öğeler) sahiptir. Bu konu, tüm öğeler için ortak olan ömür olaylarını açıklar ve ardından uygulama tanımları, pencereler veya gezinti konakları için uygulanan daha belirgin olanları tanıtır.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Öğeler için ortak ömür olayları  
 Herhangi bir WPF framework düzeyi öğesi <xref:System.Windows.FrameworkElement> (ya <xref:System.Windows.FrameworkContentElement>da öğesinden türetilen nesneler) üç ortak ömür olayına sahiptir: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>ve <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Başlatıldı  
 <xref:System.Windows.FrameworkElement.Initialized>İlk olarak oluşturulur ve kabaca, oluşturucusunun çağrısıyla nesnenin başlatılmasına karşılık gelir. Olayı başlatmaya yanıt olarak yapıldığından, nesnenin tüm özelliklerinin ayarlandığı garanti edilir. (Özel durum, Dinamik kaynaklar veya bağlama gibi ifade kullanımlarıdır; bunlar değerlendirilmeyecek ifadeler olur.) Tüm özelliklerin ayarlandığı gereksinimin bir sonucu olarak, İşaretlemede tanımlanan iç içe geçmiş öğeler <xref:System.Windows.FrameworkElement.Initialized> tarafından oluşturulan sırası, önce öğe ağacındaki en derin öğelerin, sonra da köke doğru olan üst öğeler sırasıyla ortaya çıkar. Bu sıra, üst-alt ilişkileri ve kapsamasının Özellik olmasından ve bu nedenle, özelliği dolduran alt öğeler de tamamen başlatıldığından üst öğe başlatmayı bildiremeyecek.  
  
 <xref:System.Windows.FrameworkElement.Initialized> Etkinliğe yanıt olarak işleyiciler yazarken, işleyicinin eklendiği öğe ağacındaki (mantıksal ağaç veya görsel ağaç) tüm diğer öğelerin, özellikle de bir şekilde oluşturulduğunu göz önünde bulundurmanız gerekir. üst öğeler. Üye değişkenleri null olabilir veya veri kaynakları henüz temeldeki bağlama tarafından doldurulmayabilir (ifade düzeyinde bile).  
  
### <a name="loaded"></a>Yüklü  
 <xref:System.Windows.FrameworkElement.Loaded>bir sonraki adımda oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> Olay, son işlemeden önce tetiklenir, ancak düzen sistemi, işleme için gerekli tüm değerleri hesapladıktan sonra. <xref:System.Windows.FrameworkElement.Loaded>bir öğenin içinde yer aldığı mantıksal ağacın tamamlanmasını ve HWND ve işleme yüzeyini sağlayan bir sunum kaynağına bağlanmasını gerektirir. Standart veri bağlama (diğer özellikler veya doğrudan tanımlanmış veri kaynakları gibi yerel kaynaklara bağlama) öncesinde <xref:System.Windows.FrameworkElement.Loaded>gerçekleşmeyecektir. Zaman uyumsuz veri bağlama (dış veya dinamik kaynaklar) oluşmuş olabilir, ancak zaman uyumsuz doğası tanımına göre oluşma garantisi garanti edilemez.  
  
 <xref:System.Windows.FrameworkElement.Loaded> Olayın oluşturulduğu mekanizma, öğesinden <xref:System.Windows.FrameworkElement.Initialized>farklı. <xref:System.Windows.FrameworkElement.Initialized> Olay, tamamlanmış bir öğe ağacı tarafından doğrudan koordinasyon olmadan öğesi öğe tarafından tetiklenir. Buna karşılık <xref:System.Windows.FrameworkElement.Loaded> olay, tüm öğe ağacının (özellikle de mantıksal ağaç) tamamında eşgüdümlü bir çaba olarak oluşturulur. Ağaçtaki tüm öğeler yüklendikleri bir durumda olduğunda, <xref:System.Windows.FrameworkElement.Loaded> olay ilk olarak kök öğe üzerinde tetiklenir. Daha <xref:System.Windows.FrameworkElement.Loaded> sonra olay her alt öğe üzerinde yoğun şekilde oluşturulur.  
  
> [!NOTE]
> Bu davranış, yönlendirilmiş bir olay için superficially benzer tünelleme gösterebilir. Ancak, olaydan olaya hiçbir bilgi taşınmaz. Her bir öğe her zaman <xref:System.Windows.FrameworkElement.Loaded> olayını işleme fırsatına sahiptir ve olay verilerinin işlenmiş olarak işaretlenmesi o öğenin ötesinde hiçbir etkiye sahip değildir.  
  
### <a name="unloaded"></a>Kaldırıldı  
 <xref:System.Windows.FrameworkElement.Unloaded>en son oluşturulur ve sunu kaynağı ya da kaldırılmakta olan görsel üst öğe tarafından başlatılır. Ne <xref:System.Windows.FrameworkElement.Unloaded> zaman oluşturulur ve işlenirse, olay kaynağı üst öğesi olan (özellik tarafından <xref:System.Windows.FrameworkElement.Parent%2A> belirlendiği şekilde) veya mantıksal ya da görsel ağaçlarda yukarı eklenen herhangi bir öğe önceden kaldırılmış olabilir, bu da veri bağlama, kaynak başvuruları anlamına gelir ve stilleri, normal veya son bilinen çalışma zamanı değerine ayarlanamaz.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Ömür olayları uygulama modeli öğeleri  
 Öğeleri için ortak ömür olayları oluşturmak aşağıdaki uygulama modeli öğeleridir: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.Frame>. Bunlar, ortak ömür olaylarını belirli amaçlarına uygun ek olaylarla genişletir. Bunlar aşağıdaki konumlarda ayrıntılı olarak ele alınmıştır:  
  
- <xref:System.Windows.Application>: [Uygulama yönetimine genel bakış](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [WPF Windows 'A genel bakış](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>ve :<xref:System.Windows.Controls.Frame> [Gezintiye genel bakış](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
