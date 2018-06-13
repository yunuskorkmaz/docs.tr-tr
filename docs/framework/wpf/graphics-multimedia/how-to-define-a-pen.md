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
ms.openlocfilehash: 7c5be5eff06df55e465f3e34646ba1c34e8b7e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559870"
---
# <a name="how-to-define-a-pen"></a>Nasıl yapılır: Kalem Tanımlama
Bu örnek nasıl kullanıldığını gösterir bir <xref:System.Windows.Media.Pen> bir şekli ana hatlarını belirlemek için. Basit bir oluşturmak için <xref:System.Windows.Media.Pen>, yalnızca belirttiğiniz kendi <xref:System.Windows.Media.Pen.Thickness%2A> ve <xref:System.Windows.Media.Pen.Brush%2A>. Daha karmaşık kalem belirterek oluşturabileceğiniz bir <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, ve <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Pen> tarafından tanımlanan bir şekli ana hatlarını belirlemek için bir <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Anahatları üreten tarafından kalem](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
