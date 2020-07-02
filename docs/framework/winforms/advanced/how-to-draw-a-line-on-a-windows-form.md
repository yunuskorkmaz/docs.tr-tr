---
title: 'Nasıl yapılır: Bir Windows Formunda Çizgi Çizme'
description: Paint olayını işleyerek form üzerinde bir çizgi çizmenizi ve sonra da PaintEventArgs 'un Graphics özelliğini kullanarak çizimi gerçekleştirmeyi öğrenin.
ms.date: 03/30/2017
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621632"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="58a39-103">Nasıl yapılır: Bir Windows Formunda Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="58a39-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="58a39-104">Bu örnek, bir form üzerinde bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="58a39-104">This example draws a line on a form.</span></span> <span data-ttu-id="58a39-105">Genellikle, bir form üzerinde çizim yaptığınızda formun <xref:System.Windows.Forms.Control.Paint> olayını işler ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs> Bu örnekte gösterildiği gibi, öğesinin özelliğini kullanarak çizimi gerçekleştirirsiniz</span><span class="sxs-lookup"><span data-stu-id="58a39-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a39-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="58a39-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58a39-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="58a39-107">Compiling the Code</span></span>  
 <span data-ttu-id="58a39-108">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> `e` olay işleyicisinin bir parametresi olan gerektirir <xref:System.Windows.Forms.Control.Paint> .</span><span class="sxs-lookup"><span data-stu-id="58a39-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="58a39-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="58a39-109">Robust Programming</span></span>  
 <span data-ttu-id="58a39-110"><xref:System.IDisposable.Dispose%2A>Nesneler gibi sistem kaynaklarını kullanan tüm nesneleri her zaman çağırmanız gerekir <xref:System.Drawing.Pen> .</span><span class="sxs-lookup"><span data-stu-id="58a39-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a39-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58a39-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="58a39-112">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="58a39-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="58a39-113">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="58a39-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="58a39-114">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="58a39-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
