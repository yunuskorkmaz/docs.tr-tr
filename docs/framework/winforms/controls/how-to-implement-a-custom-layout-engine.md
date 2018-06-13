---
title: 'Nasıl yapılır: Özel Yerleşim Altyapısı Uygulama'
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
ms.openlocfilehash: 0444f0d03a36adf833c04167c6d7a3c302ab15dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531303"
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="a1068-102">Nasıl yapılır: Özel Yerleşim Altyapısı Uygulama</span><span class="sxs-lookup"><span data-stu-id="a1068-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="a1068-103">Aşağıdaki kod örneği, bir basit akış düzeni gerçekleştiren özel yerleşim altyapısı oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a1068-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="a1068-104">Adlı bir panel denetimi uygulayan `DemoFlowPanel`, hangi geçersiz kılmaları <xref:System.Windows.Forms.Control.LayoutEngine%2A> örneği sağlamak için özellik `DemoFlowLayout` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a1068-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1068-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1068-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a1068-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1068-106">See Also</span></span>  
 <xref:System.Windows.Forms.Layout.LayoutEngine>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
