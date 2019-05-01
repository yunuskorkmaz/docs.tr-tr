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
# <a name="how-to-define-a-pen"></a>Nasıl yapılır: Kalem Tanımlama
Bu örnek nasıl kullanıldığını gösterir bir <xref:System.Windows.Media.Pen> anahat bir şekli. Basit bir oluşturmak için <xref:System.Windows.Media.Pen>, yalnızca belirttiğiniz, <xref:System.Windows.Media.Pen.Thickness%2A> ve <xref:System.Windows.Media.Pen.Brush%2A>. Daha karmaşık kalem belirterek oluşturabileceğiniz bir <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, ve <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Pen> tarafından tanımlanan şekil anahat bir <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Anahatları üreten bir kalem](./media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
