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
ms.openlocfilehash: 02a6736fe54be4683044f648e9d5ed5e8a3d95dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları
Bu konuda, belirli açıklanmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşamaları bir nesne oluşturma, kullanma ve yok etme ömründeki olaylar.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) konu. Bu konudaki örnekleri takip etmek için ayrıca anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (bkz [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)) ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları  
 Microsoft .NET Framework yönetilen kodda tüm nesnelerin ömrü, oluşturma, kullanma ve yok etme aşamaları benzer bir dizi ile gidin. Birçok nesne ayrıca yok etme aşamasının bir parçası oluşan yaşam sonlandırma aşaması vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri, daha fazla özel görsel nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan öğeler olarak da, ortak nesne ömrü aşamaları kümesine sahiptir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programlama ve uygulama modelleri Bu aşamalar olayları bir dizi olarak ortaya çıkarır. Nesnelerin dört ana türü vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ömür olayları göre; genel, pencere öğeleri, gezinti konakları ve uygulama nesneleri öğe. Windows ve gezinti konakları da görsel nesneler (öğeleri) daha büyük gruplandırma içindeki bulunur. Bu konuda, tüm öğeleri için ortak olan ömür olaylarını açıklar ve uygulama tanımları, windows veya gezinti konakları uygulamak daha belirli olanları tanıtır.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Öğeleri için ortak ömür olayları  
 Herhangi bir WPF çerçeve düzeyi öğesi (ya da türetilen nesneler <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>) üç ortak ömür olayına sahiptir: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, ve <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Başlatıldı  
 <xref:System.Windows.FrameworkElement.Initialized> ilk olarak oluşturulur ve kabaca kendi oluşturucusunu çağırarak nesnenin için karşılık gelir. Yanıt başlatma olarak olay gerçekleştiğinde olduğundan, nesnenin tüm özelliklerinin ayarlanır sağlanır. (Bir özel durum dinamik kaynaklar veya bağlama gibi ifade kullanımlar; bunlar değerlendirilmeyecek ifadeler olacaklardır.) Tüm özelliklerin ayarlanması, gereksinim dizisini gruplarındaki bir sonucu olarak <xref:System.Windows.FrameworkElement.Initialized> biçimlendirmede tanımlanan iç içe geçmiş öğe tarafından gerçekleştirilen görünür öğe ağacındaki derin öğelerin sırasını önce gerçekleşmesi için öğeleri köke doğru üst. Bu, üst-alt ilişkileri ve kapsama özellikleri olduğundan ve bu nedenle özelliği dolduran alt öğeleri de tamamen başlatılıncaya kadar üst başlatma raporlayamaz sırasıdır.  
  
 Ne zaman yazdığınız işleyicileri yanıt olarak <xref:System.Windows.FrameworkElement.Initialized> olay düşünmeniz gerekir işleyici eklendiği geçici öğe ağacındaki (mantıksal ağaç veya görsel ağaç) tüm diğer öğeler, özellikle oluşturulduğunu garantisi yoktur üst öğeler. Üye değişkenleri null olabilir veya veri kaynaklarının henüz temeldeki bağlama (ifade düzeyinde bile) tarafından toplanmamış olabilir.  
  
### <a name="loaded"></a>Yüklü  
 <xref:System.Windows.FrameworkElement.Loaded> sonraki tetiklenir. <xref:System.Windows.FrameworkElement.Loaded> Olayı son işlemeden önce ama düzen sistemi işleme için gereken tüm değerleri hesapladıktan sonra oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> bir öğe içinde yer alan mantıksal ağacının tamamlandıktan ve HWND ve işleme yüzeyi sağlayan bir sunu kaynağına bağlar kapsar. Standart veri bağlama (diğer özellikler veya doğrudan tanımlanmış veri kaynakları gibi yerel kaynakları bağlama) öncesinde oluşmuş <xref:System.Windows.FrameworkElement.Loaded>. Zaman uyumsuz veri bağlama (dış veya dinamik kaynaklardan) oluşmuş olabilir, ancak zaman uyumsuz doğası tanımına göre oluşmuş garanti edilemez.  
  
 Mekanizma <xref:System.Windows.FrameworkElement.Loaded> olayı farklı <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Olaydır öğe tamamlanmış bir öğe ağacı tarafından doğrudan koordinasyon olmadan öğe oluşturulur. Bunun aksine, <xref:System.Windows.FrameworkElement.Loaded> olayı tüm öğe ağacı (özellikle, mantıksal ağacının) boyunca güdümlü bir çaba olarak oluşturulur. Tüm öğeleri ağacında yüklenen, bunlar burada değerlendirilir bir durumda olduğunda <xref:System.Windows.FrameworkElement.Loaded> olayı ilk kök öğe üzerinde oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> Sonra olayı sırayla her alt öğesi.  
  
> [!NOTE]
>  Bu davranış, yüzeysel olarak yönlendirilmiş bir olay için tünel oluşturmaya benzer olabilir. Ancak, hiçbir bilgi olay Olay taşınır. Her öğe her zaman işleme fırsatına sahip kendi <xref:System.Windows.FrameworkElement.Loaded> olay ve olay verileri işlenmiş olarak işaretlemenin o öğenin ötesinde herhangi bir etkisi vardır.  
  
### <a name="unloaded"></a>Kaldırıldı  
 <xref:System.Windows.FrameworkElement.Unloaded> Son olarak oluşturulur ve sunu kaynağı veya kaldırılmakta olan görsel üstü tarafından başlatılır. Zaman <xref:System.Windows.FrameworkElement.Unloaded> oluşturulduğunda ve işlendiğinde, olay kaynağı üst öğeyi (tarafından belirlenen <xref:System.Windows.FrameworkElement.Parent%2A> özelliği) veya mantıksal veya görsel ağaçları içinde yukarı doğru verilen herhangi bir öğe zaten, yani veri bağlama, kaynak başvuruları ayarlanmamış olabilir , ve stiller normal veya son bilinen çalışma zamanı değerlerine ayarlanamaz.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Ömür olayları uygulama modeli öğeleri  
 Öğeleri aşağıdaki uygulama modeli öğeleri için ortak ömür olayları oluşturma: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.Frame>. Bu, kendi belirli amaçları ile ilgili ek olaylar ile ortak ömür olaylarını genişletir. Bunlar aşağıdaki konumlarda ayrıntılı ele alınmıştır:  
  
-   <xref:System.Windows.Application>: [Uygulama yönetimine genel bakış](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [WPF Windows genel bakış](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.Frame>: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık Özelliği Değer Önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
