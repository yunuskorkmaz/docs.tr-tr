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
ms.workload: dotnet
ms.openlocfilehash: 7c8c4f558386edd8da213f8a8af75b6a4c6a98b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="75caa-102">Nasıl yapılır: InkCanvas'a Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="75caa-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="75caa-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="75caa-103">Example</span></span>  
 <span data-ttu-id="75caa-104">Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği bir <xref:System.Windows.Controls.InkCanvas> başka bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="75caa-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="75caa-105">Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> bir veri kaynağına özelliği.</span><span class="sxs-lookup"><span data-stu-id="75caa-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="75caa-106">Aşağıdaki örnekte iki bildirir <xref:System.Windows.Controls.InkCanvas> nesneleri XAML'de ve bunları ve diğer veri kaynakları arasında veri bağlamayı kurar.</span><span class="sxs-lookup"><span data-stu-id="75caa-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="75caa-107">İlk <xref:System.Windows.Controls.InkCanvas>adlı `ic`, iki veri kaynağına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="75caa-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="75caa-108"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A> Ve <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri `ic` bağlı <xref:System.Windows.Controls.ListBox> XAML içinde tanımlanan dizilere sırayla bağlı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="75caa-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="75caa-109"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, Ve <xref:System.Windows.Controls.InkCanvas.Strokes%2A> ikinci özelliklerini <xref:System.Windows.Controls.InkCanvas> bağlı ilk <xref:System.Windows.Controls.InkCanvas>, `ic`.</span><span class="sxs-lookup"><span data-stu-id="75caa-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
