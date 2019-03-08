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
ms.openlocfilehash: 4b2988314afbe501623fd050a989876842f68601
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674542"
---
# <a name="ui-automation-and-screen-scaling"></a>UI Otomasyon ve Ekran Ölçeklendirme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] Kullanıcıların değiştirmesine olanak tanır [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] böylece çoğu ayarı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] daha büyük öğeler ekranda görünür. Bu özelliği uzun kullanılabilir olsa da [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], önceki sürümlerinde ölçeklendirme olduğu uygulamalar tarafından uygulanacak. İçinde [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], kendi ölçekleme işlememesi tüm uygulamalar için ölçeklendirme varsayılan Masaüstü Pencere Yöneticisi gerçekleştirir. UI Otomasyonu istemci uygulamaları bu özelliği dikkate almanız gerekir.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista'da ölçeklendirme  
 Varsayılan [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı olan 96 96 piksel genişliği veya yüksekliği bir kuramsal inç kaplayabilir anlamına gelir. "İnch" tam ölçüsü, boyutu ve fiziksel monitör çözünürlüğü bağlıdır. Örneğin, bir izleyicide 12 inç genişlik, 1280 piksel yatay çözünürlükte 96 piksel yatay çizgi hakkında 9/10 inç genişletir.  
  
 Değiştirme [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı ekran çözünürlüğünü değiştirme ile aynı değil. İle [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ölçeklendirme, fiziksel piksel ekranında sayısı aynı kalır. Ancak, ölçeklendirme boyutunu ve konumunu uygulanan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri. Bu ölçeklendirme tarafından Masaüstü Pencere Yöneticisi'ni (DWM) değil ölçeklendirilmesi açıkça sorma uygulamalar ve Masaüstü için otomatik olarak gerçekleştirilebilir.  
  
 Aslında, ne zaman kullanıcı ayarlar ölçek faktörü için 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], ekranda bir dikey veya yatay inç yüzde 25 oranında daha büyük hale gelir. Tüm boyutlar uygun şekilde ölçeklendirilir. Ekranın üst ve sol kenarlarının bir uygulama penceresinde uzaklığını yüzde 25 oranında artar. Uygulama ölçeklendirme etkinleştirilir ve uygulama değil [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-uyumlu, pencerenin boyutu artar kaydırmalar ve tüm boyutları ile birlikte aynı oranda [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri içeriyor.  
  
> [!NOTE]
>  Varsayılan olarak, ölçeklendirmenin DWM gerçekleştirmez olmayan[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-kullanıcı ayarladığında kullanan uygulamalar [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ile 120 gerçekleştirir ancak zaman [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] bir 144 veya üzerinin özel değere ayarlayın. Ancak, kullanıcı varsayılan davranışı geçersiz kılabilirsiniz.  
  
 Ekran ölçeklendirme ekran koordinatları ile herhangi bir şekilde endişe uygulamalar için yeni zorluklar oluşturur. Ekranı, artık iki koordinat sistemi içerir: fiziksel ve mantıksal. Fiziksel bir noktasının gerçek uzaklık piksel cinsinden üst koordinatları kaynağı kaldı. Ölçeği piksel durumunda olduğu gibi mantıksal uzaklıklarını koordinatları.  
  
 Bir düğme içeren bir iletişim kutusu tasarım koordinatlarda (100, 48) olduğunu varsayalım. Bu iletişim kutusunu 96 varsayılan olarak görüntülenen zaman [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], fiziksel koordinatlarda düğmesi bulunur (100, 48). 120 adresindeki [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], fiziksel koordinatlarda bulunur (125, 60). Ancak aynı anda tüm mantıksal koordinatları olan [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı: (100, 48).  
  
 İşletim sistemi ve uygulama davranışını öğesinden bağımsız olarak tutarlı hale getirdiklerinden mantıksal koordinatları önemli [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı. Örneğin, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalde mantıksal koordinatlarını döndürür. Bir iletişim kutusu içindeki bir öğenin üzerine imleci taşıma ise bağımsız olarak, aynı koordinatlara döndürülür [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı. Bir denetimi çizerseniz (100, 100), bu mantıksal koordinatlarına çizilmiş ve aynı göreli konumda herhangi kaplayacağı [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>UI Otomasyonu istemcilerinde ölçeklendirme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] Mantıksal koordinatları kullanmaz. Aşağıdaki yöntemleri ve özellikleri fiziksel koordinatlarını döndürür veya bunları parametre alır.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Varsayılan olarak,-96 olmayan bir içinde çalışan bir UI otomasyon istemci uygulaması [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ortamı bu yöntemlere ve özelliklere doğru sonuçları elde etmek mümkün olmayacak. İmleç konumu mantıksal koordinatlarında olduğundan, örneğin, istemci yalnızca bu koordinatlarına geçirilemez <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> imlecin altındaki öğeyi edinme. Ayrıca, uygulamanın doğru şekilde windows kendi istemci alanı dışına yerleştirmek mümkün olmayacaktır.  
  
 İki parça halinde çözümüdür.  
  
1.  İlk olarak, istemci uygulaması olun [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-uyumlu. Bunu yapmak için [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevi `SetProcessDPIAware` başlangıçta. Yönetilen kodda aşağıdaki bildirimi bu işlev kullanılabilir hale getirir.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Bu işlev, tüm işlem DPI kullanan, işleme ait tüm windows ölçeklendirilmemiş olduğu anlamına haline getirir. İçinde [vurgulayıcısı ile ilgili örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), vurgulama dikdörtgeni dört windows örneği için UI Otomasyon, mantıksal koordinatları elde fiziksel koordinatları konumunda bulunur. Örnek DPI kullanan değilse, vurgulama 96 DPI ortamında yanlış yerleştirme neden olacağından Masaüstü, mantıksal koordinatlarda çizilmiş.  
  
2.  İmleç koordinatlarını edinmek için çağrı [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevi `GetPhysicalCursorPos`. Aşağıdaki örnek, bildirmek ve bu işlevi kullanmak gösterilmektedir.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Kullanmayın <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Bu özelliğin ölçeklendirilmiş bir ortamda windows istemcisi dışında davranış tanımsızdır.  
  
 Uygulamanız ile olmayan doğrudan işlem içi iletişimi gerçekleştirir, [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-uyumlu uygulamalarla sahip dönüştürmeniz kullanarak mantıksal ve fiziksel koordinatları arasında [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevleri `PhysicalToLogicalPoint` ve `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Vurgulayıcısı ile ilgili örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
