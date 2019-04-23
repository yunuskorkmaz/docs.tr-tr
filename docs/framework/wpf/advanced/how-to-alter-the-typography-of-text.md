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
ms.openlocfilehash: 4c027424632f8671ba8d7cae1c899ef3a53edc26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078869"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="5cce5-102">Nasıl yapılır: Metnin Tipografisini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5cce5-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="5cce5-103">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.TextElement.Typography%2A> özniteliği kullanarak <xref:System.Windows.Documents.Paragraph> örnek öğesi olarak.</span><span class="sxs-lookup"><span data-stu-id="5cce5-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cce5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cce5-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="5cce5-105">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cce5-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="5cce5-106">![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="5cce5-106">![Screenshot: Text with altered typography](./media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="5cce5-107">Buna karşılık, varsayılan tipografik özellikleri ile benzer bir örnek nasıl işlediğini aşağıdaki şekilde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cce5-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="5cce5-108">![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="5cce5-108">![Screenshot: Text with altered typography](./media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cce5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cce5-109">Example</span></span>  
 <span data-ttu-id="5cce5-110">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğini program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="5cce5-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="5cce5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cce5-111">See also</span></span>

- [<span data-ttu-id="5cce5-112">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5cce5-112">Flow Document Overview</span></span>](flow-document-overview.md)
