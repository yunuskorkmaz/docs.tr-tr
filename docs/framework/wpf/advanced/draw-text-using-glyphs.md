---
title: Karakterleri Kullanarak Metin Çizme
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: e2b35eb6df140551d5db7d597826df53e37182fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542532"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="c38c8-102">Karakterleri Kullanarak Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="c38c8-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="c38c8-103">Bu konu alt düzey kullanımı açıklanmaktadır <xref:System.Windows.Documents.Glyphs> metinde görüntülenecek nesne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c38c8-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="c38c8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c38c8-104">Example</span></span>  
 <span data-ttu-id="c38c8-105">Aşağıdaki örnekler özelliklerini tanımlamak nasıl bir <xref:System.Windows.Documents.Glyphs> nesnesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c38c8-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="c38c8-106"><xref:System.Windows.Documents.Glyphs> Nesneyi temsil ediyor çıktısını bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c38c8-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="c38c8-107">Örneklerde, Arial, Courier New ve kez yeni Latin yazı tipleri yerel bilgisayarda C:\WINDOWS\Fonts klasörüne yüklenir varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38c8-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="c38c8-108">Bu örnek, diğer özelliklerini tanımlamak gösterilmiştir <xref:System.Windows.Documents.Glyphs> nesnelerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c38c8-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c38c8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c38c8-109">See Also</span></span>  
 [<span data-ttu-id="c38c8-110">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="c38c8-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
