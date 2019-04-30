---
title: "Nasıl yapılır: InkCanvas'a Veri Bağlama"
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 5d3fc0ed7b6176d7bc68bf20af42c311b5563908
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776473"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Nasıl yapılır: InkCanvas'a Veri Bağlama
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği bir <xref:System.Windows.Controls.InkCanvas> diğerine <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> bir veri kaynağına özelliği.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Aşağıdaki örnek iki bildirir <xref:System.Windows.Controls.InkCanvas> nesneleri XAML ve bunları ve diğer veri kaynakları arasında veri bağlama oluşturur.  İlk <xref:System.Windows.Controls.InkCanvas>adlı `ic`, iki veri kaynaklarına bağlanır.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> Ve <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri `ic` bağlı <xref:System.Windows.Controls.ListBox> sırayla XAML içinde tanımlanan dizileri bağlı olan nesneleri.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, Ve <xref:System.Windows.Controls.InkCanvas.Strokes%2A> ikinci özelliklerini <xref:System.Windows.Controls.InkCanvas> bağlı ilk <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
