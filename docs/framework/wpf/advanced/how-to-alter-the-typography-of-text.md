---
title: 'Nasıl yapılır: Metnin Tipografisini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: eeed93f62802a942915511db060c0e6c029579e0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365793"
---
# <a name="how-to-alter-the-typography-of-text"></a>Nasıl yapılır: Metnin Tipografisini Değiştirme
Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.TextElement.Typography%2A> özniteliği kullanarak <xref:System.Windows.Documents.Paragraph> örnek öğesi olarak.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog.png "TextElement_Typog")  
  
 Buna karşılık, varsayılan tipografik özellikleri ile benzer bir örnek nasıl işlediğini aşağıdaki şekilde gösterilmektedir.  
  
 ![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğini program aracılığıyla.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Akış Belgesine Genel Bakış](flow-document-overview.md)
