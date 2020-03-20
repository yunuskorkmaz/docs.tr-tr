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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179974"
---
# <a name="ui-automation-and-screen-scaling"></a>UI Otomasyon ve Ekran Ölçeklendirme
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
Windows Vista'dan başlayarak Windows, kullanıcıların ekrandaki çoğu kullanıcı arabirimi (UI) öğesinin daha büyük görünmesi için kullanıcıların inç başına (dpi) ayarnoktalarını değiştirmesini sağlar. Bu özellik uzun windows'da kullanılabilir olmasına rağmen, önceki sürümlerde ölçekleme uygulamalar tarafından uygulanması gerekiyordu. Windows Vista'dan başlayarak, Masaüstü Pencere Yöneticisi kendi ölçekleme işlemez tüm uygulamalar için varsayılan ölçekleme gerçekleştirir. UI Automation istemci uygulamaları bu özelliği dikkate almalıdır.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Windows Vista'da ölçekleme  
 Varsayılan dpi ayarı 96'dır, bu da 96 pikselin bir genişlik veya bir inç yüksekliğikapladığı anlamına gelir. Bir "inç" tam ölçüsü boyutu ve monitörün fiziksel çözünürlüğü bağlıdır. Örneğin, 12 inç genişliğindeki bir monitörde, 1280 piksellik yatay çözünürlükte, 96 piksellik yatay bir çizgi yaklaşık 9/10 inç kadar uzanır.  
  
 DPI ayarını değiştirmek, ekran çözünürlüğünü değiştirmekle aynı şey değildir. DPI ölçekleme ile ekrandaki fiziksel piksel sayısı aynı kalır. Ancak, ölçekleme öğelerin boyutu na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve konumuna uygulanır. Bu ölçeklendirme, masaüstü için masaüstü pencere yöneticisi (DWM) ve açıkça ölçeklendirilmesini açıkça sormayan uygulamalar için otomatik olarak gerçekleştirilebilir.  
  
 Sonuç olarak, kullanıcı ölçek faktörünü 120 dpi'ye ayarladığında, ekrandaki dikey veya yatay inç yüzde 25 daha büyük olur. Tüm boyutlar buna göre ölçeklendirilir. Bir uygulama penceresinin ekranın üst ve sol kenarlarından mahsup yüzdesi yüzde 25 artar. Uygulama ölçekleme etkinleştirilmişse ve uygulama dpi farkında değilse, pencerenin boyutu içerdiği tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerin uzaklıkları ve boyutlarıyla birlikte aynı oranda artar.  
  
> [!NOTE]
> Varsayılan olarak, dwm kullanıcı dpi 120 ayarlar dpi farkında olmayan uygulamalar için ölçekleme gerçekleştirmez, ancak dpi 144 veya daha yüksek özel bir değere ayarlandığında bunu gerçekleştirir. Ancak, kullanıcı varsayılan davranışı geçersiz kılabilir.  
  
 Ekran ölçekleme, ekran koordinatları ile herhangi bir şekilde ilgili uygulamalar için yeni zorluklar oluşturur. Ekran şimdi iki koordinat sistemi içerir: fiziksel ve mantıksal. Bir noktanın fiziksel koordinatları, kaynağın sol üst kısmından piksellerde gerçek ofsettir. Mantıksal koordinatlar, piksellerin kendileri ölçeklendirildiyse, olacakları gibi uzaklıklardır.  
  
 Koordinatlarda düğme olan bir iletişim kutusu tasarladığınızı varsayalım (100, 48). Bu iletişim kutusu varsayılan 96 dpi'de görüntülendiğinde, düğme (100, 48) fiziksel koordinatlarında bulunur. 120 dpi'de fiziksel koordinatlarda yer alır (125, 60). Ama mantıksal koordinatları herhangi bir dpi ayarı aynıdır: (100, 48).  
  
 Mantıksal koordinatlar önemlidir, çünkü işletim sisteminin davranışını ve uygulamaları dpi ayarından bağımsız olarak tutarlı hale getirin. Örneğin, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalde mantıksal koordinatları döndürür. İmleci bir iletişim kutusundaki bir öğenin üzerine taşırsanız, dpi ayarından bağımsız olarak aynı koordinatlar döndürülür. (100, 100) bir denetim çizerseniz, bu mantıksal koordinatlara çizilir ve herhangi bir dpi ayarında aynı göreli konumu işgal eder.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>UI Otomasyon İstemcilerinde Ölçekleme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API mantıksal koordinatları kullanmaz. Aşağıdaki yöntem ve özellikler fiziksel koordinatları döndürer veya parametre olarak alır.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Varsayılan olarak, 96-dpi olmayan bir ortamda çalışan bir Kullanıcı Bira Otomasyonistemci uygulaması bu yöntem ve özelliklerden doğru sonuçlar elde edemeyecektir. Örneğin, imleç konumu mantıksal koordinatlarda olduğundan, imleç altında öğeyi <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> elde etmek için istemci bu koordinatları kolayca geçemez. Buna ek olarak, uygulama doğru istemci alanı dışında pencereleri yerleştirmek mümkün olmayacaktır.  
  
 Çözelti iki bölümden oluşur.  
  
1. İlk olarak, istemci uygulama dpi-farkında olun. Bunu yapmak için başlangıçta Win32 işlevini `SetProcessDPIAware` arayın. Yönetilen kodda, aşağıdaki bildirim bu işlevi kullanılabilir kılar.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Bu işlev, tüm işlemi dpi-farkında yapar, yani işleme ait tüm pencereler ölçeklenmemiş. Vurgulayıcı [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)Örneği'nde, örneğin, vurgu dikdörtgenini oluşturan dört pencere, mantıksal koordinatlarda değil, UI Automation'dan elde edilen fiziksel koordinatlarda yer alır. Örnek dpi farkında olmasaydı, vurgu masaüstündeki mantıksal koordinatlarda çizilir ve bu da 96-dpi olmayan bir ortamda yanlış yerleşimle sonuçlanır.  
  
2. İmleç koordinatlarını almak için Win32 `GetPhysicalCursorPos`işlevini arayın. Aşağıdaki örnek, bu işlevin nasıl bildirilen ve kullanılacağını gösterir.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>Kullanmayın. Bu özelliğin ölçeklenmiş bir ortamda istemci pencerelerdışında davranışı tanımsız.  
  
 Uygulamanız dpi farkında olmayan uygulamalarla doğrudan çapraz işlem iletişimi gerçekleştirse, Win32 işlevlerini `PhysicalToLogicalPoint` kullanarak mantıksal `LogicalToPhysicalPoint`ve fiziksel koordinatlar arasında dönüştürme yapmış olabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Vurgulayıcı Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
