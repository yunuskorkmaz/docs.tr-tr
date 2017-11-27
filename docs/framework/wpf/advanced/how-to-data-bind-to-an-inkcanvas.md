---
title: "Nasıl yapılır: InkCanvas'a Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdcd67f972dafa2de7fb74e01b4a3c22dfd848fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Nasıl yapılır: InkCanvas'a Veri Bağlama
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği bir <xref:System.Windows.Controls.InkCanvas> başka bir <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> bir veri kaynağına özelliği.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Aşağıdaki örnekte iki bildirir <xref:System.Windows.Controls.InkCanvas> nesneleri XAML'de ve bunları ve diğer veri kaynakları arasında veri bağlamayı kurar.  İlk <xref:System.Windows.Controls.InkCanvas>adlı `ic`, iki veri kaynağına bağlanır.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> Ve <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri `ic` bağlı <xref:System.Windows.Controls.ListBox> XAML içinde tanımlanan dizilere sırayla bağlı nesneleri.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, Ve <xref:System.Windows.Controls.InkCanvas.Strokes%2A> ikinci özelliklerini <xref:System.Windows.Controls.InkCanvas> bağlı ilk <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
