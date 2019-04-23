---
title: 'Nasıl yapılır: Alt Öğeleri Konumlandırmak için Tuvalin Ekli Özelliklerini Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 347c8502bd4c5fafcde7a142327f85bfb75b9954
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159633"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>Nasıl yapılır: Alt Öğeleri Konumlandırmak için Tuvalin Ekli Özelliklerini Kullanma
Bu örnekte, ekli özelliklerini kullanma işlemi gösterilmektedir <xref:System.Windows.Controls.Canvas> alt öğeleri konumlandırmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dört ekler <xref:System.Windows.Controls.Button> öğeleri bir üst öğenin alt öğeleri olarak <xref:System.Windows.Controls.Canvas>. Her öğe tarafından temsil edilen bir <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, ve <xref:System.Windows.Controls.Canvas.Top%2A>.
Her <xref:System.Windows.Controls.Button> üst konumlandırılmış <xref:System.Windows.Controls.Canvas> ve atanan özellik değerine göre.  
  
 [!code-cpp[CanvasAttachedProperties#1](~/samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [Panellere Genel Bakış](panels-overview.md)
- [Nasıl Yapılır Konuları](canvas-how-to-topics.md)
- [Ekli Özelliklere Genel Bakış](../advanced/attached-properties-overview.md)
