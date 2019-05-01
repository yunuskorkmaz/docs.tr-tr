---
title: 'Nasıl yapılır: Sistem Yazı Tiplerini Numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001604"
---
# <a name="how-to-enumerate-system-fonts"></a><span data-ttu-id="47bc9-102">Nasıl yapılır: Sistem Yazı Tiplerini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="47bc9-102">How to: Enumerate System Fonts</span></span>
## <a name="example"></a><span data-ttu-id="47bc9-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="47bc9-103">Example</span></span>  
 <span data-ttu-id="47bc9-104">Aşağıdaki örnek, sistem yazı tipi koleksiyonu yazı tiplerini numaralandırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-104">The following example shows how to enumerate the fonts in the system font collection.</span></span> <span data-ttu-id="47bc9-105">Yazı tipi ailesinin adı her <xref:System.Windows.Media.FontFamily> içinde <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> bir birleşik giriş kutusu için bir öğe olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="47bc9-105">The font family name of each <xref:System.Windows.Media.FontFamily> within <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> is added as an item to a combo box.</span></span>  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 <span data-ttu-id="47bc9-106">Birden çok sürümünü aynı yazı tipi ailesi aynı dizinde bulunuyorsa [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tipi numaralandırma yazı en son sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="47bc9-106">If multiple versions of the same font family reside in the same directory, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font enumeration returns the most recent version of the font.</span></span> <span data-ttu-id="47bc9-107">Sürüm bilgilerini çözümleme sağlamıyorsa, en son zaman damgasına sahip yazı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="47bc9-107">If the version information does not provide resolution, the font with latest timestamp is returned.</span></span> <span data-ttu-id="47bc9-108">Zaman damgası bilgi eşdeğer ise, alfabetik olarak sıralandığı ilk yazı tipi dosyasını döndürülür.</span><span class="sxs-lookup"><span data-stu-id="47bc9-108">If the timestamp information is equivalent, the font file that is first in alphabetical order is returned.</span></span>
