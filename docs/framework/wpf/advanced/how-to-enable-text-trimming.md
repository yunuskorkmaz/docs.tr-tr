---
title: "Nasıl yapılır: Metin Kırpmayı Etkinleştirme"
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
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdaafa62815c75d8ab364a18d909d867f90052c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="9a991-102">Nasıl yapılır: Metin Kırpmayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9a991-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="9a991-103">Örnek Kullanım ve kullanılabilir değerlerinin etkileri gösterir <xref:System.Windows.TextTrimming> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="9a991-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a991-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a991-104">Example</span></span>  
 <span data-ttu-id="9a991-105">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Controls.TextBlock> öğeyle <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="9a991-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="9a991-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a991-106">Example</span></span>  
 <span data-ttu-id="9a991-107">Karşılık gelen ayarlama <xref:System.Windows.TextTrimming> özelliğinin kodda aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a991-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="9a991-108">Metin kırpma için şu anda üç seçenek vardır: **CharacterEllipsis**, **WordEllipsis**, ve **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="9a991-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="9a991-109">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **CharacterEllipsis**, metin kırpılır ve kırpma kenarına en yakın karakterinde üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="9a991-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="9a991-110">Bu ayar daha yakından kırpma sınıra uyacak şekilde metin olarak kırpmaya ancak kısmen kırpılmadan sözcükleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a991-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="9a991-111">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="9a991-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="9a991-112">![Örnek: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="9a991-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="9a991-113">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **WordEllipsis**, metin kırpılır ve kırpma kenarına en yakın ilk tam sözcüğü sonundaki üç nokta ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="9a991-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="9a991-114">Bu ayar, kısmen bölünen sözcükleri göstermeyecektir ancak metin kırpma kenara olabildiğince yakın değil olarak kırpmaya **CharacterEllipsis** ayarı.</span><span class="sxs-lookup"><span data-stu-id="9a991-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="9a991-115">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="9a991-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="9a991-116">![Örnek: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="9a991-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="9a991-117">Zaman <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> ayarlanır **hiçbiri**, metin kırpma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9a991-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="9a991-118">Bu durumda, metin yalnızca ana metin kapsayıcının sınırına kırpılır.</span><span class="sxs-lookup"><span data-stu-id="9a991-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="9a991-119">Bu ayarda etkisini aşağıdaki şekilde gösterilmiştir bir <xref:System.Windows.Controls.TextBlock> yukarıda tanımlanan benzer.</span><span class="sxs-lookup"><span data-stu-id="9a991-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="9a991-120">![Örnek: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="9a991-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
