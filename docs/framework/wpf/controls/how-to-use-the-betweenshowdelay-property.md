---
title: 'Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552720"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> araç ipuçları hızlı bir şekilde görünmesini sağlayacak şekilde zaman özelliğinin — çok az kayıpla veya hiç gecikmeyle — zaman kullanıcı hareket fare işaretçisini bir araç ipucu doğrudan diğerine.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> özelliği bir saniye (1000 milisaniye cinsinden) ayarlamak ve <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> hem araç ipuçları için iki saniye (2000 milisaniye) olarak ayarlanmış <xref:System.Windows.Shapes.Ellipse> kontrol eder. Üç nokta birinin araç ipucunu görüntüleyebilirsiniz ve ardından fare işaretçisini başka bir elips iki saniye içinde üzerinde getirip bekletin, ikinci elipsin araç ipucuna hemen görüntüler.  
  
 Aşağıdaki senaryolardan biri, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> uygular, araç ipucu görünmeden önce bir saniye bekleyin ikinci elipsin neden olur:  
  
-   İkinci düğme iki saniyeden fazla ise taşımak için geçen süre.  
  
-   Araç İpucu ilk elipsin zaman aralığının başlangıcında görünür değilse.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [Araç İpucuna Genel Bakış](../../../../docs/framework/wpf/controls/tooltip-overview.md)
