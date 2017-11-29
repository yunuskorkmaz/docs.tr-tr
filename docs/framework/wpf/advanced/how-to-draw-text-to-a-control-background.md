---
title: "Nasıl yapılır: çizim metin Denetim &#39; s arka plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Nasıl yapılır: çizim metin Denetim &#39; s arka plan
Bir metin dizesi dönüştürerek doğrudan bir denetim arka plan için metin çizebilirsiniz bir <xref:System.Windows.Media.FormattedText> nesnesini genişletin ve ardından denetimin çizim nesnesi <xref:System.Windows.Media.DrawingContext>. Arka plan nesnelerin çizime türetilmiş için de bu tekniği kullanabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.StackPanel>.  
  
 ![Metin arka planı olarak görüntüleme denetimleri](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Özel metin arka plan denetimleriyle örneği  
  
## <a name="example"></a>Örnek  
 Denetim arka plan çizmek için yeni bir oluşturma <xref:System.Windows.Media.DrawingBrush> nesne ve dönüştürülen metin nesnenin çizin <xref:System.Windows.Media.DrawingContext>. Ardından, yeni Ata <xref:System.Windows.Media.DrawingBrush> denetimin arka plan özelliğine.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.FormattedText> nesne ve arka planını çizin bir <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Button> nesne.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.FormattedText>  
 [Biçimli metin çizme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
