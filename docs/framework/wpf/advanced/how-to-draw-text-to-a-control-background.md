---
title: 'Nasıl yapılır: Bir denetime metin çizme&#39;s arka plan'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: d580330de5ef3841979fffc61db336064f1643f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740435"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Nasıl yapılır: Bir denetime metin çizme&#39;s arka plan
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
