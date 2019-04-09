---
title: 'Nasıl yapılır: Şekilli Windows Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: 03fcbb97db180e71283810e2daeab9be272b9d5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087261"
---
# <a name="how-to-create-a-shaped-windows-form"></a><span data-ttu-id="8fb61-102">Nasıl yapılır: Şekilli Windows Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8fb61-102">How to: Create a Shaped Windows Form</span></span>
<span data-ttu-id="8fb61-103">Bu örnek ile formu boyutlandırır elips bir şekli bir form sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fb61-103">This example gives a form an elliptical shape that resizes with the form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fb61-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fb61-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8fb61-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8fb61-105">Compiling the Code</span></span>  
 <span data-ttu-id="8fb61-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8fb61-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8fb61-107">Başvurular <xref:System.Windows.Forms> ve <xref:System.Drawing> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="8fb61-107">References to the <xref:System.Windows.Forms> and <xref:System.Drawing> namespaces.</span></span>  
  
 <span data-ttu-id="8fb61-108">Bu örnek için geçersiz kılar <xref:System.Windows.Forms.Control.OnPaint%2A> formun şeklini değiştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fb61-108">This example overrides the <xref:System.Windows.Forms.Control.OnPaint%2A> method to change the shape of the form.</span></span> <span data-ttu-id="8fb61-109">Bu kodu kullanmak için yöntem bildiriminde yanı sıra yöntemi içindeki çizim kodu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="8fb61-109">To use this code, copy the method declaration as well as the drawing code inside the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb61-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb61-110">See also</span></span>

- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [<span data-ttu-id="8fb61-111">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="8fb61-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
