---
title: 'Nasıl yapılır: Kalem Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
ms.openlocfilehash: 1d69a40604dbf2f7a73c17279ae946faeb6c634a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965405"
---
# <a name="how-to-define-a-pen"></a><span data-ttu-id="65c0e-102">Nasıl yapılır: Kalem Tanımlama</span><span class="sxs-lookup"><span data-stu-id="65c0e-102">How to: Define a Pen</span></span>
<span data-ttu-id="65c0e-103">Bu örnek nasıl kullanıldığını gösterir bir <xref:System.Windows.Media.Pen> anahat bir şekli.</span><span class="sxs-lookup"><span data-stu-id="65c0e-103">This example shows how use a <xref:System.Windows.Media.Pen> to outline a shape.</span></span> <span data-ttu-id="65c0e-104">Basit bir oluşturmak için <xref:System.Windows.Media.Pen>, yalnızca belirttiğiniz, <xref:System.Windows.Media.Pen.Thickness%2A> ve <xref:System.Windows.Media.Pen.Brush%2A>.</span><span class="sxs-lookup"><span data-stu-id="65c0e-104">To create a simple <xref:System.Windows.Media.Pen>, you need only specify its <xref:System.Windows.Media.Pen.Thickness%2A> and <xref:System.Windows.Media.Pen.Brush%2A>.</span></span> <span data-ttu-id="65c0e-105">Daha karmaşık kalem belirterek oluşturabileceğiniz bir <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, ve <xref:System.Windows.Media.Pen.EndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="65c0e-105">You can create more complex pen's by specifying a <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, and <xref:System.Windows.Media.Pen.EndLineCap%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65c0e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="65c0e-106">Example</span></span>  
 <span data-ttu-id="65c0e-107">Aşağıdaki örnekte bir <xref:System.Windows.Media.Pen> tarafından tanımlanan şekil anahat bir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="65c0e-107">The following example uses a <xref:System.Windows.Media.Pen> to outline a shape defined by a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 <span data-ttu-id="65c0e-108">![Anahatları üreten bir kalem](./media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span><span class="sxs-lookup"><span data-stu-id="65c0e-108">![Outlines produces by a Pen](./media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span></span>  
<span data-ttu-id="65c0e-109">GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="65c0e-109">A GeometryDrawing</span></span>
