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
ms.openlocfilehash: 4953312f2241d8816411147dd0e43f96d9d706ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611951"
---
# <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları
Bu konu, söz konusu açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşamaları oluşturma, kullanma ve yok etme, bir nesnenin yaşam süresini belirtmek olayları.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md) konu. Bu konudaki örnekleri izlemek için de anlamanız gereken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (bkz [XAML genel bakış (WPF)](xaml-overview-wpf.md)) ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Nesne Yaşam Süresi Olayları  
 Microsoft .NET Framework yönetilen kodu tüm nesnelerin ömrü, oluşturma, kullanma ve yok etme aşamalarında benzer bir dizi aracılığıyla gidin. Çok sayıda nesne de yok etme aşamasının bir parçası ortaya çıkan yaşam sonlandırma aşaması vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneler, daha fazla özel görseli nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tanımlayan öğeler olarak da ortak nesne ömrü aşamalarını kümesine sahiptir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programlama ve uygulama modelleri bir dizi olay Bu aşamalardan ortaya çıkarır. Nesnelerin dört ana türü vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ömür olayları göre; genel, pencere öğeleri, gezinti konakları ve uygulama nesneleri öğeleri. Windows ve gezinti konakları, ayrıca daha büyük görsel nesneler (öğeleri) gruplandırmasını içinde değildir. Bu konu, tüm öğeleri için ortak olan yaşam süresi olayları açıklar ve ardından uygulama tanımları, windows veya gezinti konakları için geçerli daha özel olanları tanıtır.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Öğeleri için ortak bir yaşam süresi olayları  
 Herhangi bir WPF framework düzeyinde öğe (öğesinden türetilen nesneler <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>) üç yaygın ömür olayları vardır: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, ve <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Başlatıldı  
 <xref:System.Windows.FrameworkElement.Initialized> ilk olarak oluşturulur ve kabaca oluşturucusuna bir çağrı tarafından nesnesi için karşılık gelen. Olaya yanıt olarak başlatılması gerektiğinden, nesnenin tüm özelliklerinin ayarlandığını garanti edilir. (İfade kullanımları dinamik kaynaklar veya bağlama gibi bir özel durumdur; bunlar değerlendirilmemiş ifadeleri olacaktır.) Tüm özellikler ayarlanır, bir dizi gereksinim söz konusu kümelerdeki <xref:System.Windows.FrameworkElement.Initialized> biçimlendirme içinde tanımlanan iç içe öğeler tarafından gerçekleştirilen görünür öğe ağacında en derin öğelerin sırasını önce gerçekleşmesi için doğru kök öğeleri ardından üst. Bu, üst-alt ilişkileri ve kapsama özellikleri olduğundan ve bu nedenle özelliği dolduran alt öğeleri de tamamen yeniden başlatılıncaya kadar üst başlatma raporlayamaz sırasıdır.  
  
 Ne zaman yazdığınız işleyicileri yanıt olarak <xref:System.Windows.FrameworkElement.Initialized> olay göz önünde bulundurmanız gerekir işleyici eklendiği geçici öğe ağacında (mantıksal ağaç veya görsel ağacı) içinde tüm diğer öğeleri, özellikle oluşturulmuş olduğunu garanti yoktur üst öğeler. Üye değişkenleri null olabilir veya veri kaynakları henüz (hatta ifade düzeyinde) temel alınan bağlanarak toplanmamış olabilir.  
  
### <a name="loaded"></a>Yüklü  
 <xref:System.Windows.FrameworkElement.Loaded> sonraki oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> Olayı, ancak son işlemeden önce işleme için tüm gerekli değerleri düzen sistemi hesapladıktan sonra oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> bir öğe içinde bulunan mantıksal ağaç tamamlandıktan ve HWND ve işleme yüzeyi sağlar bir sunu kaynağına bağlar kapsar. Standart veri bağlama (diğer özellikler veya doğrudan tanımlanmış veri kaynakları gibi yerel kaynakları bağlama) öncesinde oluşmuş <xref:System.Windows.FrameworkElement.Loaded>. Zaman uyumsuz veri bağlama (dış veya dinamik kaynakları) oluşmuş olabilir, ancak zaman uyumsuz doğası tanımına göre gerçekleşen garanti edilemez.  
  
 Mekanizma <xref:System.Windows.FrameworkElement.Loaded> olayı farklı <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Olaydır öğe tamamlanmış öğe ağacı tarafından doğrudan koordinasyon olmadan bir öğe oluşturulur. Bunun aksine, <xref:System.Windows.FrameworkElement.Loaded> olayı tüm öğe ağacında (özellikle, mantıksal ağacı) boyunca eşgüdümlü bir çaba olarak oluşturulur. Ağacındaki tüm öğeler yüklendi, burada değerlendirilir bir durumda olduğunda <xref:System.Windows.FrameworkElement.Loaded> olayı Kök öğede önce oluşturulur. <xref:System.Windows.FrameworkElement.Loaded> Olay sırayla oluşturulur her bir alt öğesi.  
  
> [!NOTE]
>  Bu davranış, yüzeysel olarak gönderilmiş bir olay için tüneli oluşturmaya benzer olabilir. Ancak, hiçbir bilgi olayı olay taşınır. Her öğe her zaman işleme fırsatına sahip kendi <xref:System.Windows.FrameworkElement.Loaded> olay ve olay verilerini işlenmiş olarak işaretleme, o öğenin ötesinde herhangi bir etkisi vardır.  
  
### <a name="unloaded"></a>Kaldırıldı  
 <xref:System.Windows.FrameworkElement.Unloaded> Son olarak oluşturulur ve sunu kaynağı veya kaldırılmasını visual üst tarafından başlatılır. Zaman <xref:System.Windows.FrameworkElement.Unloaded> oluşturulduğunda ve işlendiğinde, olay kaynağı üst öğeyi (tarafından belirlenen şekilde <xref:System.Windows.FrameworkElement.Parent%2A> özelliği) veya mantıksal veya görsel ağaçlarda yukarı yönlü verilen herhangi bir öğe zaten, yani veri bağlama, kaynak başvurularını ayarlanmamış olabilir , ve stilleri, normal veya son bilinen çalışma zamanı değerine ayarlanamaz.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Yaşam süresi olayları uygulama modeli öğeleri  
 Öğeleri aşağıdaki uygulama model öğeleri için ortak yaşam süresi olayları oluşturma: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.Frame>. Bu ortak ömür olayları, belirli bir amaç için uygun olan diğer olayları ile genişletin. Bunlar aşağıdaki konumlarda ayrıntılı ele alınmıştır:  
  
- <xref:System.Windows.Application>: [Uygulama Yönetimine Genel Bakış](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [WPF Windows genel bakış](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, ve <xref:System.Windows.Controls.Frame>: [Gezintiye genel bakış](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliği Değer Önceliği](dependency-property-value-precedence.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
