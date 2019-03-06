---
title: 'Nasıl yapılır: Görsel Taslak Arama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
ms.openlocfilehash: 7553550f406cc72603aa9f65e4233a13329223a9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354290"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="e7d00-102">Nasıl yapılır: Görsel Taslak Arama</span><span class="sxs-lookup"><span data-stu-id="e7d00-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="e7d00-103">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi bir <xref:System.Windows.Media.Animation.Storyboard> herhangi bir konumda bir film şeridinde animasyon atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7d00-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7d00-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7d00-104">Example</span></span>  
 <span data-ttu-id="e7d00-105">XAML işaretleme örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7d00-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="e7d00-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7d00-106">Example</span></span>  
 <span data-ttu-id="e7d00-107">XAML kodu yukarıdaki kullanılan kod aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="e7d00-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e7d00-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7d00-108">See also</span></span>
- [<span data-ttu-id="e7d00-109">Görsel Taslağı Zaman Uyumlu Olarak Arama</span><span class="sxs-lookup"><span data-stu-id="e7d00-109">Seek a Storyboard Synchronously</span></span>](how-to-seek-a-storyboard-synchronously.md)
