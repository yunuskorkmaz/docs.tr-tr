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
ms.openlocfilehash: 656a5cb38461f71698a312e6382a3a9c29158cc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560292"
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="7e1e4-102">Nasıl yapılır: Görsel Taslak Arama</span><span class="sxs-lookup"><span data-stu-id="7e1e4-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="7e1e4-103">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi bir <xref:System.Windows.Media.Animation.Storyboard> film şeridi animasyon herhangi bir konuma gitmek için.</span><span class="sxs-lookup"><span data-stu-id="7e1e4-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e1e4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e1e4-104">Example</span></span>  
 <span data-ttu-id="7e1e4-105">XAML biçimlendirme örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7e1e4-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="7e1e4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e1e4-106">Example</span></span>  
 <span data-ttu-id="7e1e4-107">Yukarıdaki XAML kodu ile birlikte kullanılan kod aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="7e1e4-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7e1e4-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e1e4-108">See Also</span></span>  
 [<span data-ttu-id="7e1e4-109">Görsel Taslağı Zaman Uyumlu Olarak Arama</span><span class="sxs-lookup"><span data-stu-id="7e1e4-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
