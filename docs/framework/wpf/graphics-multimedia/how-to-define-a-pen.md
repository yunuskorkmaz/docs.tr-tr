---
title: "Nasıl yapılır: Kalem Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c173b895f67164152d5930efc6a385bc480aaa81
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-define-a-pen"></a>Nasıl yapılır: Kalem Tanımlama
Bu örnek nasıl kullanıldığını gösterir bir <xref:System.Windows.Media.Pen> bir şekli ana hatlarını belirlemek için. Basit bir oluşturmak için <xref:System.Windows.Media.Pen>, yalnızca belirttiğiniz kendi <xref:System.Windows.Media.Pen.Thickness%2A> ve <xref:System.Windows.Media.Pen.Brush%2A>. Daha karmaşık kalem belirterek oluşturabileceğiniz bir <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, ve <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Pen> tarafından tanımlanan bir şekli ana hatlarını belirlemek için bir <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Anahatları üreten tarafından kalem](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
