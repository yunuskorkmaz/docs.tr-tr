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
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963845"
---
# <a name="how-to-draw-text-to-a-visual"></a>Nasıl yapılır: Görsele Metin Çizme
Aşağıdaki örnek, bir <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> nesnesi kullanılarak nasıl metin çizileceğini gösterir. Bir çizim bağlamı, bir <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> <xref:System.Windows.Media.DrawingVisual> nesnenin yöntemi çağırarak döndürülür. Çizim bağlamına grafik ve metin çizebilirsiniz.  
  
 Çizim bağlamına metin çizmek için, bir <xref:System.Windows.Media.DrawingContext.DrawText%2A> <xref:System.Windows.Media.DrawingContext> nesnenin yöntemini kullanın. Çizim bağlamına içerik çizmeyi bitirdiğinizde, çizim bağlamını kapatmak ve içeriği kalıcı hale <xref:System.Windows.Media.DrawingContext.Close%2A> getirmek için yöntemini çağırın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Yukarıdaki kod örneğinin ayıklandığı bütün kod örneği için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159994).
