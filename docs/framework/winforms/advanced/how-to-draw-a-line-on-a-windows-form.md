---
title: "Nasıl yapılır: Bir Windows Formunda Çizgi Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 78ad7d455f1de4b7077288d9575ea4907c3f218d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="a4f51-102">Nasıl yapılır: Bir Windows Formunda Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="a4f51-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="a4f51-103">Bu örnek, bir form üzerinde bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="a4f51-103">This example draws a line on a form.</span></span> <span data-ttu-id="a4f51-104">Genellikle, bir form üzerinde çizerken formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve çizim gerçekleştirin ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs>, bu örnekte gösterildiği gibi</span><span class="sxs-lookup"><span data-stu-id="a4f51-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f51-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4f51-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4f51-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a4f51-106">Compiling the Code</span></span>  
 <span data-ttu-id="a4f51-107">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a4f51-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a4f51-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a4f51-108">Robust Programming</span></span>  
 <span data-ttu-id="a4f51-109">Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> sistem kaynakları gibi kullanabilecek tüm nesneler üzerinde <xref:System.Drawing.Pen> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a4f51-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f51-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f51-110">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="a4f51-111">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="a4f51-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="a4f51-112">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="a4f51-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="a4f51-113">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a4f51-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
