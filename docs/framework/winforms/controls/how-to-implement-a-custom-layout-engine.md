---
title: 'Nasıl yapılır: Özel yerleşim altyapısı uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
ms.openlocfilehash: 2b5bdab243039014b42d2f57f4037833f2137d67
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702639"
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="e4209-102">Nasıl yapılır: Özel yerleşim altyapısı uygulama</span><span class="sxs-lookup"><span data-stu-id="e4209-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="e4209-103">Aşağıdaki kod örneği, bir basit bir akış düzeni gerçekleştiren özel yerleşim altyapısı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4209-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="e4209-104">Adlı bir panel denetimi uygular `DemoFlowPanel`, hangi geçersiz kılmaları <xref:System.Windows.Forms.Control.LayoutEngine%2A> bir örneğini sağlamak için özellik `DemoFlowLayout` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4209-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4209-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4209-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e4209-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4209-106">See also</span></span>
- <xref:System.Windows.Forms.Layout.LayoutEngine>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
