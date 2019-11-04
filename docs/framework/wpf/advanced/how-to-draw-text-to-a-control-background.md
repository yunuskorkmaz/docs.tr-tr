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
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424384"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Nasıl yapılır: Denetimin Arka Planına Metin Çizme
Bir metin dizesini <xref:System.Windows.Media.FormattedText> nesnesine dönüştürerek ve sonra denetimin <xref:System.Windows.Media.DrawingContext>nesneyi çizerek bir denetimin arka planına doğrudan metin çizebilirsiniz. Bu tekniği, <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>gibi <xref:System.Windows.Controls.Panel>türetilen nesnelerin arka planına çizim için de kullanabilirsiniz.  
  
 ![Metin arka plan olarak görüntülenen denetimlerin ekran görüntüsü.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
Özel metin arka planlarına sahip denetimler örneği  
  
## <a name="example"></a>Örnek  
 Bir denetimin arka planına çizim yapmak için, yeni bir <xref:System.Windows.Media.DrawingBrush> nesnesi oluşturun ve dönüştürülen metni nesnenin <xref:System.Windows.Media.DrawingContext>çizin. Ardından, yeni <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliğine atayın.  
  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Media.FormattedText> nesnesinin nasıl oluşturulduğunu ve bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesnesinin arka planına nasıl çizileceğini gösterir.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.FormattedText>
- [Biçimlendirilmiş Metin Çizme](drawing-formatted-text.md)
