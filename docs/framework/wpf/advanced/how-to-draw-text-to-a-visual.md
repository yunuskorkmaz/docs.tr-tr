---
title: 'Nasıl yapılır: Görsele Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094559"
---
# <a name="how-to-draw-text-to-a-visual"></a>Nasıl yapılır: Görsele Metin Çizme
Aşağıdaki örnek, bir <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> nesnesi kullanarak nasıl metin çizileceğini gösterir. Bir çizim bağlamı, bir <xref:System.Windows.Media.DrawingVisual> nesnesinin <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi çağırarak döndürülür. Çizim bağlamına grafik ve metin çizebilirsiniz.  
  
 Çizim bağlamına metin çizmek için, bir <xref:System.Windows.Media.DrawingContext> nesnesinin <xref:System.Windows.Media.DrawingContext.DrawText%2A> yöntemini kullanın. Çizim bağlamına içerik çizmeyi bitirdiğinizde çizim bağlamını kapatmak ve içeriği kalıcı hale getirmek için <xref:System.Windows.Media.DrawingContext.Close%2A> yöntemini çağırın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Yukarıdaki kod örneğinin ayıklandığı bütün kod örneği için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).
