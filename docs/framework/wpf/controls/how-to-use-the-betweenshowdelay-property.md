---
title: "Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Araç İpucu genel bakış](../../../../docs/framework/wpf/controls/tooltip-overview.md)
