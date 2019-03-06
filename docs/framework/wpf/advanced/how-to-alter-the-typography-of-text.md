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
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="a9e41-102">Nasıl yapılır: Metnin Tipografisini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a9e41-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="a9e41-103">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.TextElement.Typography%2A> özniteliği kullanarak <xref:System.Windows.Documents.Paragraph> örnek öğesi olarak.</span><span class="sxs-lookup"><span data-stu-id="a9e41-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e41-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9e41-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="a9e41-105">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9e41-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="a9e41-106">![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="a9e41-106">![Screenshot: Text with altered typography](./media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="a9e41-107">Buna karşılık, varsayılan tipografik özellikleri ile benzer bir örnek nasıl işlediğini aşağıdaki şekilde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a9e41-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="a9e41-108">![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="a9e41-108">![Screenshot: Text with altered typography](./media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e41-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9e41-109">Example</span></span>  
 <span data-ttu-id="a9e41-110">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğini program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="a9e41-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e41-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e41-111">See also</span></span>
- [<span data-ttu-id="a9e41-112">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9e41-112">Flow Document Overview</span></span>](flow-document-overview.md)
