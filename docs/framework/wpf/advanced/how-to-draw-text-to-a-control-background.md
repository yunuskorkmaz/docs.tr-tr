---
title: 'Nasıl yapılır: Denetimin Arka Planına Metin Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 9be4eb92021a62baaf6b43198587616d00cc265e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259260"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Nasıl yapılır: Denetimin Arka Planına Metin Çizme
Bir metin dizesindeki dönüştürerek doğrudan bir denetimin arka planına metin çizebilirsiniz bir <xref:System.Windows.Media.FormattedText> nesnesi ve ardından nesne denetimin çizim <xref:System.Windows.Media.DrawingContext>. Nesne arka plan çizimi türetilen için de bu tekniği kullanabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>.  
  
 ![Metin arka planı olarak görüntüleme denetimleri](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Özel metin arka plan denetimleriyle örneği  
  
## <a name="example"></a>Örnek  
 Bir denetimin arka planına çizmek için yeni bir oluşturma <xref:System.Windows.Media.DrawingBrush> nesne ve nesnenin Dönüştürülen metin çizme <xref:System.Windows.Media.DrawingContext>. Ardından, yeni Ata <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliği için.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.FormattedText> nesne ve arka planına çizin bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesne.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.FormattedText>
- [Biçimlendirilmiş Metin Çizme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
