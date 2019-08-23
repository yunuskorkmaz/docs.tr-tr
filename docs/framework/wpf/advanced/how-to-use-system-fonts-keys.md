---
title: 'Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918381"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="4fb83-102">Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="4fb83-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="4fb83-103">Sistem kaynakları, geliştiricilerin sistem ayarlarıyla tutarlı görseller oluşturmalarına yardımcı olmak için çeşitli sistem ölçümlerini kaynak olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4fb83-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="4fb83-104"><xref:System.Windows.SystemFonts>, hem sistem yazı tipi değerlerini hem de değerleri bağlayan sistem yazı tipi kaynaklarını içeren bir sınıftır — Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> ve. <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A></span><span class="sxs-lookup"><span data-stu-id="4fb83-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="4fb83-105">Sistem yazı tipi ölçümleri, statik veya dinamik kaynaklar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fb83-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="4fb83-106">Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak kullanın; Aksi halde statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="4fb83-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fb83-107">Dinamik kaynaklarda, özellik adının sonuna anahtar sözcük *anahtarı* eklenir.</span><span class="sxs-lookup"><span data-stu-id="4fb83-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="4fb83-108">Aşağıdaki örnek, bir düğmeye stil eklemek veya özelleştirmek için sistem yazı tipi dinamik kaynaklarının nasıl erişebileceğini ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fb83-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="4fb83-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, bir düğmeye değerler atayan <xref:System.Windows.SystemFonts> bir düğme stili oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4fb83-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fb83-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fb83-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="4fb83-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb83-111">See also</span></span>

- [<span data-ttu-id="4fb83-112">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="4fb83-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="4fb83-113">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="4fb83-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="4fb83-114">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="4fb83-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
