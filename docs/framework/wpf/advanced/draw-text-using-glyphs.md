---
title: Karakterleri Kullanarak Metin Çizme
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 155f0b756b43ad8cfd0ddde63a5e86854f5f1624
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363013"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="acb59-102">Karakterleri Kullanarak Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="acb59-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="acb59-103">Bu konuda alt düzey kullanmayı açıklar <xref:System.Windows.Documents.Glyphs> metni görüntülemek için nesne [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb59-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb59-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="acb59-104">Example</span></span>  
 <span data-ttu-id="acb59-105">Aşağıdaki örnekler özelliklerini tanımlamak nasıl bir <xref:System.Windows.Documents.Glyphs> nesnesine [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb59-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="acb59-106"><xref:System.Windows.Documents.Glyphs> Nesnesini çıktısını gösteren bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb59-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="acb59-107">Örneklerde Arial Courier yeni ve Times yeni Roman yazı tiplerinin C:\WINDOWS\Fonts klasörüne yerel bilgisayarda yüklü olan varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="acb59-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="acb59-108">Bu örnek, diğer özelliklerini tanımlamak gösterilmektedir <xref:System.Windows.Documents.Glyphs> nesneler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb59-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="acb59-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb59-109">See also</span></span>
- [<span data-ttu-id="acb59-110">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="acb59-110">Typography in WPF</span></span>](typography-in-wpf.md)
