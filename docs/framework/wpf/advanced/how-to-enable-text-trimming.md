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
ms.openlocfilehash: 97bc88b298500892fcc7d26e61f8052a05d9e593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543546"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="b192c-102">Nasıl yapılır: Metin Kırpmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b192c-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="b192c-103">Örnek Kullanım ve kullanılabilir değerlerinin etkileri gösterir <xref:System.Windows.TextTrimming> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b192c-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b192c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b192c-104">Example</span></span>  
 <span data-ttu-id="b192c-105">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Controls.TextBlock> öğeyle <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="b192c-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="b192c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b192c-106">Example</span></span>  
 <span data-ttu-id="b192c-107">Karşılık gelen ayarlama <xref:System.Windows.TextTrimming> özelliğinin kodda aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b192c-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="b192c-108">Metin kırpma için şu anda üç seçenek vardır: **CharacterEllipsis**, **WordEllipsis**, ve **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="b192c-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="b192c-109">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **CharacterEllipsis**, metin kırpılır ve kırpma kenarına en yakın karakterinde üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="b192c-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="b192c-110">Bu ayar daha yakından kırpma sınıra uyacak şekilde metin olarak kırpmaya ancak kısmen kırpılmadan sözcükleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b192c-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="b192c-111">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="b192c-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="b192c-112">![Örnek: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="b192c-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="b192c-113">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **WordEllipsis**, metin kırpılır ve kırpma kenarına en yakın ilk tam sözcüğü sonundaki üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="b192c-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="b192c-114">Bu ayar, kısmen bölünen sözcükleri göstermeyecektir ancak metin kırpma kenara olabildiğince yakın değil olarak kırpmaya **CharacterEllipsis** ayarı.</span><span class="sxs-lookup"><span data-stu-id="b192c-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="b192c-115">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="b192c-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="b192c-116">![Örnek: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="b192c-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="b192c-117">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **hiçbiri**, metin kırpma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b192c-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="b192c-118">Bu durumda, metin yalnızca ana metin kapsayıcının sınırına kırpılır.</span><span class="sxs-lookup"><span data-stu-id="b192c-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="b192c-119">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="b192c-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="b192c-120">![Örnek: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="b192c-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
