---
title: 'Nasıl yapılır: Mürekkep Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
ms.openlocfilehash: 31f5d0ffb6f0fdcdaef13bc44653f8c7938ac7f3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378816"
---
# <a name="how-to-rotate-ink"></a><span data-ttu-id="08e7d-102">Nasıl yapılır: Mürekkep Döndürme</span><span class="sxs-lookup"><span data-stu-id="08e7d-102">How to: Rotate Ink</span></span>
## <a name="example"></a><span data-ttu-id="08e7d-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="08e7d-103">Example</span></span>  
 <span data-ttu-id="08e7d-104">Aşağıdaki örnek mürekkebi kopyalar bir <xref:System.Windows.Controls.InkCanvas> için bir <xref:System.Windows.Controls.Canvas> içeren bir <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="08e7d-104">The following example copies the ink from an <xref:System.Windows.Controls.InkCanvas> to a <xref:System.Windows.Controls.Canvas> that contains an <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="08e7d-105">Mürekkep uygulama kopyalar, 90 derece saat yönünde de mürekkep döndürür.</span><span class="sxs-lookup"><span data-stu-id="08e7d-105">When the application copies the ink, it also rotates the ink 90 degrees clockwise.</span></span>  
  
 [!code-xaml[HowToRotateInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="08e7d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="08e7d-106">Example</span></span>  
 <span data-ttu-id="08e7d-107">Aşağıdaki örnek, bir özel <xref:System.Windows.Documents.Adorner> , döndürür vuruşları üzerinde bir <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="08e7d-107">The following example is a custom <xref:System.Windows.Documents.Adorner> that rotates the strokes on an <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[AdornerForStrokes#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 <span data-ttu-id="08e7d-108">Aşağıdaki örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlayan dosyası bir <xref:System.Windows.Controls.InkPresenter> ve mürekkep ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="08e7d-108">The following example is a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that defines an <xref:System.Windows.Controls.InkPresenter> and populates it with ink.</span></span> <span data-ttu-id="08e7d-109">`Window_Loaded` Olay işleyicisi ekler özel donatıcı <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="08e7d-109">The `Window_Loaded` event handler adds the custom adorner to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-xaml[AdornerForStrokes#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
