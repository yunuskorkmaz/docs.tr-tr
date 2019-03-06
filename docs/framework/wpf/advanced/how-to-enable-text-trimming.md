---
title: 'Nasıl yapılır: Metin Kırpmayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 367e1f46524d8135d8269a2e2159dfe7c2468c45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354472"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="03a4f-102">Nasıl yapılır: Metin Kırpmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="03a4f-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="03a4f-103">Bu örnek kullanımını ve kullanılabilir değerleri etkilerini gösterir <xref:System.Windows.TextTrimming> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="03a4f-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a4f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a4f-104">Example</span></span>  
 <span data-ttu-id="03a4f-105">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Controls.TextBlock> öğeyle <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="03a4f-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="03a4f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a4f-106">Example</span></span>  
 <span data-ttu-id="03a4f-107">Buna karşılık gelen ayarı <xref:System.Windows.TextTrimming> kod özelliğinde aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="03a4f-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="03a4f-108">Metin kırpma için şu anda üç seçenek vardır: **CharacterEllipsis**, **WordEllipsis**, ve **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="03a4f-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="03a4f-109">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **CharacterEllipsis**, metin kırpılır ve kırpma kenarına en yakın karakterde üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="03a4f-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="03a4f-110">Bu ayar daha yakından kırpmayı sınıra uyacak şekilde metin olarak kırpmaya ancak sözcükler kesilecek kısmen neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="03a4f-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="03a4f-111">Aşağıdaki şekil, bu ayarda etkisini gösterir. bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="03a4f-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="03a4f-112">![Örnek: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="03a4f-112">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="03a4f-113">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **WordEllipsis**, metin kırpılır ve kırpma kenarına en yakın ilk tam sözcük sonuna üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="03a4f-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="03a4f-114">Bu ayar, kısmen bölünen sözcükleri göstermez ancak yakın kesme kenara metin değil olarak kırpmaya **CharacterEllipsis** ayarı.</span><span class="sxs-lookup"><span data-stu-id="03a4f-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="03a4f-115">Aşağıdaki şekil, bu ayarda etkisini gösterir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="03a4f-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="03a4f-116">![Örnek: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="03a4f-116">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="03a4f-117">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **hiçbiri**, hiçbir metin kırpmayı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="03a4f-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="03a4f-118">Bu durumda, metin yalnızca metin kapsayıcının üst sınıra kırpılır.</span><span class="sxs-lookup"><span data-stu-id="03a4f-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="03a4f-119">Aşağıdaki şekil, bu ayarda etkisini gösterir. bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="03a4f-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="03a4f-120">![Örnek: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="03a4f-120">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
