---
title: "Nasıl yapılır: Görsele Metin Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 735a84a034587b1433403a45edc7c2f459340273
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a>Nasıl yapılır: Görsele Metin Çizme
Aşağıdaki örnekte nasıl metne çizileceğini gösterir bir <xref:System.Windows.Media.DrawingVisual> kullanarak bir <xref:System.Windows.Media.DrawingContext> nesnesi. Çizim Bağlamı çağrılarak döndürülür <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi bir <xref:System.Windows.Media.DrawingVisual> nesnesi. Grafikler ve metin çizim bağlamına çizebilirsiniz.  
  
 Metin çizme bağlamına çizmek için kullanma <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemi bir <xref:System.Windows.Media.DrawingContext> nesnesi. Çizim bağlamına çizim içeriği işiniz bittiğinde, çağrı <xref:System.Windows.Media.DrawingContext.Close%2A> çizim bağlamı kapatmak ve içeriği kalıcı hale getirmek için yöntem.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Önceki kod örneğinde ayıklandığı tam kod örnek için bkz [Test kullanarak isabet sınaması örneği isabet](http://go.microsoft.com/fwlink/?LinkID=159994).
