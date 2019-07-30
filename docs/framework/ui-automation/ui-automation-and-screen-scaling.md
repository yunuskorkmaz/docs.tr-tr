---
title: UI Otomasyon ve Ekran Ölçeklendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: a59223bfbe9506aa0028933d55b74e24d5595c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629544"
---
# <a name="ui-automation-and-screen-scaling"></a>UI Otomasyon ve Ekran Ölçeklendirme
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]Kullanıcıların ekrandaki öğelerin çoğu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] daha büyük görünmesi için nokta/inç (dpi) ayarı değiştirmesini sağlar. Sürümünde [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]bu özellik uzun süredir kullanılabilir olsa da, önceki sürümlerde ölçeklendirmenin uygulamalar tarafından uygulanması gerekiyordu. ' [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]De Masaüstü Pencere Yöneticisi, kendi ölçeklendirmeyi işlemeyen tüm uygulamalar için varsayılan ölçeklendirmeyi gerçekleştirir. UI Otomasyonu istemci uygulamaları bu özelliği dikkate almalıdır.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista 'da ölçeklendirme  
 Varsayılan DPI ayarı 96 ' dir. Bu, 96 piksellik bir bir veya daha fazla inç genişlik veya yükseklik kaplayacağı anlamına gelir. "İnç" tam ölçüsü, izleyicinin boyutuna ve fiziksel çözünürlüğüne bağlıdır. Örneğin, 12 inç genişliğinde bir monitörde, 1280 piksellik yatay çözünürlükte, 96 piksellik yatay bir çizgi, bir inç 9/10.  
  
 DPI ayarının değiştirilmesi, ekran çözünürlüğünü değiştirme ile aynı değildir. DPI ölçeklendirme sayesinde, ekrandaki fiziksel piksel sayısı aynı kalır. Ancak, ölçekleme [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin boyutuna ve konumuna uygulanır. Bu ölçeklendirme, masaüstü için Masaüstü Pencere Yöneticisi (DWM) ve açıkça ölçeklendirilmemiş olmayan uygulamalar tarafından otomatik olarak gerçekleştirilebilir.  
  
 Aslında, Kullanıcı ölçek faktörünü 120 dpi olarak ayarladığında, ekrandaki dikey veya yatay inç yüzde 25 oranında daha büyük olur. Tüm boyutlar uygun şekilde ölçeklendirilir. Ekranın üst ve sol kenarlarından bir uygulama penceresinin kayması yüzde 25 oranında artar. Uygulama ölçekleme etkinse ve uygulama DPI duyarlı değilse, pencerenin boyutu, içerdiği tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin uzaklıkları ve boyutları ile aynı oranda artar.  
  
> [!NOTE]
>  Varsayılan olarak, Kullanıcı DPI 'yi 120 olarak ayarladığınızda, DWM DPI kullanmayan uygulamalar için ölçeklendirmeyi gerçekleştirmez, ancak DPI, 144 veya üzeri özel bir değere ayarlandığında bunu gerçekleştirir. Ancak, Kullanıcı varsayılan davranışı geçersiz kılabilir.  
  
 Ekran ölçeklendirme, ekran koordinatları ile herhangi bir şekilde ilgilenen uygulamalar için yeni zorluk oluşturur. Ekranda şu anda iki koordinat sistemi var: fiziksel ve mantıksal. Bir noktanın fiziksel koordinatları, kaynağın sol üst kısmından itibaren gerçek uzaklığa göre piksel cinsinden fark edilir. Mantıksal Koordinatlar, piksellerin kendisi ölçeklendiği gibi uzaklıklardır.  
  
 Koordinatları (100, 48) olan bir düğmeye sahip bir iletişim kutusu tasarlayacağınızı varsayın. Bu iletişim kutusu varsayılan 96 DPI 'de görüntülendiğinde, düğme fiziksel koordinatlara (100, 48) yerleştirilir. 120 dpi sürümünde, (125, 60) fiziksel koordinatlarıyla bulunur. Ancak mantıksal koordinatlar herhangi bir DPI ayarında aynıdır: (100, 48).  
  
 Mantıksal Koordinatlar, DPI ayarından bağımsız olarak işletim sisteminin ve uygulamaların davranışını tutarlı hale yaptığından önemlidir. Örneğin, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalde mantıksal koordinatları döndürür. İmleci bir iletişim kutusunda bir öğenin üzerine taşırsanız, DPI ayarından bağımsız olarak aynı koordinatlar döndürülür. (100, 100) adresinde bir Denetim çiziyorsanız, bu mantıksal koordinatlara çizilir ve herhangi bir DPI ayarında aynı göreli konumu kaplayacaktır.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>UI Otomasyonu Istemcilerinde ölçekleme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API mantıksal koordinatları kullanmaz. Aşağıdaki yöntemler ve Özellikler fiziksel koordinatları döndürür ya da bunları parametre olarak alır.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Varsayılan olarak, 96 dpi olmayan bir ortamda çalışan bir UI Otomasyonu istemci uygulaması, bu yöntemler ve özelliklerden doğru sonuçlar elde edemeyecektir. Örneğin, imleç konumu mantıksal koordinatlardaki olduğundan, istemci imlecin altında olan öğeyi almak için bu koordinatları öğesine <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> geçiremez. Ayrıca, uygulama Windows 'u istemci alanının dışına doğru şekilde yerleştiremeyecektir.  
  
 Çözüm iki bölümden oluşur.  
  
1. İlk olarak, istemci uygulamayı DPI ile uyumlu hale getirin. Bunu yapmak için başlatma sırasında [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevi `SetProcessDPIAware` çağırın. Yönetilen kodda, aşağıdaki bildirim bu işlevi kullanılabilir hale getirir.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Bu işlev tüm işlemi DPI 'ye duyarlı hale getirir. Bu, işleme ait olan tüm pencerelerin ölçeklendirilmemiş olması anlamına gelir. [Vurgulayıcı](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)örneğinde, örneğin, vurgulama dikdörtgenini oluşturan dört pencere, mantıksal koordinatları DEĞIL, UI otomasyonundan alınan fiziksel koordinatlara yerleştirilir. Örnek DPI duyarlı değilse, vurgu, masaüstündeki mantıksal koordinatlara çizilir, bu da 96 dpi olmayan bir ortamda yanlış yerleştirme oluşmasına neden olur.  
  
2. İmleç koordinatlarını almak için [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevini `GetPhysicalCursorPos`çağırın. Aşağıdaki örnekte, bu işlevin nasıl bildirilemeyeceğini ve kullanılacağı gösterilmektedir.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Kullanmayın <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Bu özelliğin ölçeklendirilen bir ortamda istemci penceresi dışında davranışı tanımsızdır.  
  
 Uygulamanız DPI kullanmayan uygulamalarla doğrudan işlemler arası iletişim gerçekleştiriyorsa, ve [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `LogicalToPhysicalPoint`işlevlerini `PhysicalToLogicalPoint` kullanarak mantıksal ve fiziksel koordinatlar arasında dönüştürme yapmış olabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Vurgulayıcı örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
