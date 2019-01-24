---
title: 'Nasıl yapılır: Metne Program Aracılığıyla Öğe Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
ms.openlocfilehash: 460524a88427ef5fa822461a7bb985426fefea53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693194"
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a>Nasıl yapılır: Metne Program Aracılığıyla Öğe Ekleme
Aşağıdaki örnek nasıl kullanacağınızı gösterir <xref:System.Windows.Documents.TextPointer> metinde uygulamak için bir aralık belirtmek için nesneleri bir <xref:System.Windows.Documents.Span> öğesi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 Aşağıdaki çizimde, bu örnek nasıl göründüğünü gösterir.  
  
 ![Bir metin aralığı için uygulanan bir Span öğesi](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Akış Belgesine Genel Bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
