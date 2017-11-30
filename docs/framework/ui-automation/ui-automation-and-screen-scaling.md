---
title: "UI Otomasyon ve Ekran Ölçeklendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 98a2069009d04a2c1ff9127006c2382bf7481e04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-and-screen-scaling"></a>UI Otomasyon ve Ekran Ölçeklendirme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]Kullanıcıların değiştirmesine olanak tanır [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] böylece çoğu ayarı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] daha büyük ekranda öğeleri görünür. Bu özellik uzun kullanılabilir olsa da [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], önceki sürümlerde ölçeklendirme sahip uygulamalar tarafından uygulanacak. İçinde [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], Masaüstü Pencere Yöneticisi kendi ölçeklendirme işlemez tüm uygulamalar için ölçeklendirme varsayılan gerçekleştirir. UI Otomasyonu istemci uygulamalarının bu özellik, dikkate almanız gerekir.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista'da ölçeklendirme  
 Varsayılan [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] bir ayardır 96, 96 piksel genişliği veya yüksekliği bir notional inç kaplar anlamına gelir. Bir "inch" tam ölçü boyutu ve fiziksel çözümleme izleme bağlıdır. Örneğin, bir monitörde 12 inç genişlik, yatay 1280 piksel çözünürlükte 96 piksel yatay çizgi hakkında 9/10 inç genişletir.  
  
 Değiştirme [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı ekran çözünürlüğünü değiştirme ile aynı değil. İle [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ölçeklendirme, fiziksel piksel ekranında sayısı aynı kalır. Ancak, ölçekleme boyutunu ve konumunu uygulanır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri. Bu ölçeklendirme tarafından Masaüstü Pencere Yöneticisi (DWM) değil ölçeklendirilmesi açıkça isteme uygulamalar ve Masaüstü için otomatik olarak gerçekleştirilebilir.  
  
 Etkin olduğunda kullanıcı ayarlar ölçek faktörü için 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], dikey veya yatay inç ekranında 25 oranında daha büyük hale gelir. Tüm boyutlar uygun şekilde ölçeklendirilir. Ekranın üst ve sol kenarlarının Uygulama penceresinden uzaklığını yüzde 25 artırır. Uygulama ölçeklendirme etkinleştirilmişse ve uygulama değil [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aklınızda pencere boyutu artar uzaklıkları ve tüm boyutları birlikte aynı oranda [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri içeriyor.  
  
> [!NOTE]
>  Varsayılan olarak, DWM ölçeklendirme gerçekleştirmez olmayan[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-kullanıcı ayarlar zaman uyumlu uygulamalar [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ile 120 işlemini gerçekleştirir ancak zaman [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] özel bir değer 144 veya üzeri ayarlanır. Ancak, kullanıcı varsayılan davranışı geçersiz kılabilirsiniz.  
  
 Ekran ölçeklendirme ekran koordinatları ile herhangi bir yolla ilgili uygulamalar için yeni zorluklar oluşturur. Ekran şimdi iki koordinat sistemi içerir: fiziksel ve mantıksal. Fiziksel bir noktanın koordinatlarını gerçek uzaklık piksel cinsinden üstten olan kökeni sol. Ölçeklendirilmiş piksel kendilerini durumunda olduğu gibi mantıksal koordinatlar uzaklıkları belirlenir.  
  
 Bir düğmeyi içeren bir iletişim kutusu tasarım (100, 48) koordinatlarda varsayalım. Bu iletişim kutusunu 96 varsayılan olarak görüntülenen zaman [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], fiziksel koordinatlarda düğmesi bulunur (100, 48). 120 adresindeki [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], fiziksel koordinatlarda bulunur (125, 60). Ancak mantıksal koordinatları herhangi aynıdır [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı: (100, 48).  
  
 İşletim sistemi ve uygulamalar davranışını bakılmaksızın tutarlı hale mantıksal koordinatları önemli [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı. Örneğin, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalde mantıksal koordinatları döndürür. Bir öğedeki bir iletişim kutusu üzerinden imleci taşırsanız, aynı koordinatlara bağımsız olarak, döndürülen [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı. Bir denetimine çizin varsa (100, 100), bu mantıksal koordinatları çizilir ve aynı göreli konumda herhangi kaplar [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ayarı.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>UI otomasyonda ölçeklendirme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] Mantıksal koordinatları kullanmaz. Aşağıdaki yöntemleri ve özellikleri fiziksel koordinatları dönün veya parametre olarak alın.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Varsayılan olarak,-96 olmayan bir içinde çalışan bir UI Otomasyonu istemci uygulaması [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ortamı bu yöntemlere ve özelliklere doğru sonuçlar almak mümkün olmayacak. İmleç konumu mantıksal koordinatlarında olduğundan, örneğin, istemci sadece bu koordinatlara geçirilemez <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> altında imleç öğesi elde edilir. Ayrıca, uygulamanın doğru kendi istemci alanının dışında windows yerleştirin mümkün olmaz.  
  
 İki parça halinde çözümüdür.  
  
1.  İlk olarak, istemci uygulaması olun [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-kullanan. Bunu yapmak için arama [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevi `SetProcessDPIAware` başlangıçta. Yönetilen kodda şu bildirimi bu işlev kullanılabilir hale getirir.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Bu işlev tüm işlem yapar [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-kullanan, işleme ait tüm windows ölçeklendirilmemiş olduğu anlamına gelir. İçinde [vurgulama örnek](http://msdn.microsoft.com/en-us/19ba4577-753e-4efd-92cc-c02ee67c1b69), örneği için Vurgu dikdörtgeni dört windows alınan fiziksel koordinatları adresindedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], mantıksal koordinatları. Örnek olsalar [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aklınızda Vurgu mantıksal koordinatlarda yanlış yerleştirme içinde-96 olmayan bir sonuçlanacaktır masaüstünde çizilmesi [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ortamı.  
  
2.  İmleç koordinatları almak için arama [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevi `GetPhysicalCursorPos`. Aşağıdaki örnek, bildirme ve bu işlevi kullanın gösterilmektedir.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Kullanmayın <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. Bu özellik ölçeklendirilmiş bir ortamda windows istemcisi dışında davranışını tanımlanmamıştır.  
  
 Uygulamanız ile olmayan doğrudan işlem içi iletişimi gerçekleştirir, [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-kullanan uygulamalar, sahip dönüştürmeniz kullanarak mantıksal ve fiziksel koordinatları arasında [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] işlevleri `PhysicalToLogicalPoint` ve `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Vurgulama örnek](http://msdn.microsoft.com/en-us/19ba4577-753e-4efd-92cc-c02ee67c1b69)
