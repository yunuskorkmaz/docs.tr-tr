---
title: 'Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 9b63675ec21294496117860aa5b58af132c4284a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614524"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> zaman özelliğinin araç ipuçları hızlı bir şekilde görünür: çok az kayıpla veya hiç gecikmeyle — ne zaman bir kullanıcı hareket fare işaretçisi bir araç ipucu doğrudan diğerine.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> özelliği, bir saniye (1000 milisaniye) için ayarlanır ve <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> araç ipuçları her ikisi için iki saniye (2000 milisaniye cinsinden) olarak ayarlanmış <xref:System.Windows.Shapes.Ellipse> denetimleri. Üç nokta simgesini biri için araç ipucunu görüntülemek ve sonra fare işaretçisi için başka bir elips iki saniye içinde üzerine getirip bekletin, araç ipucu ikinci elipsin hemen görüntüler.  
  
 Aşağıdaki senaryolardan birini <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> uygular, araç ipucu ikinci bir elipsin görünmeden önce bir saniye beklemeniz neden olur:  
  
- İkinci düğme iki saniyeden fazla ise taşımak için geçen süre.  
  
- Araç İpucu elips ilk zaman aralığının başlangıcında görünür değilse.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Nasıl Yapılır Konuları](tooltip-how-to-topics.md)
- [Araç İpucuna Genel Bakış](tooltip-overview.md)
