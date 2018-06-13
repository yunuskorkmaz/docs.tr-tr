---
title: 'Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544433"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="3a129-102">Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a129-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="3a129-103">Sistem kaynakları, geliştiriciler Sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olacak kaynaklar olarak sistem ölçümleri sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="3a129-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="3a129-104"><xref:System.Windows.SystemFonts> Sistem yazı tipi değerlerini ve değerlere bağlanan sistem yazı tipi kaynakları içeren bir sınıf — Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a129-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="3a129-105">Sistem yazı tipi ölçümleri statik veya dinamik kaynaklar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a129-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="3a129-106">Uygulama çalışırken otomatik olarak güncelleştirmek için yazı tipi ölçüsünün istiyorsanız, dinamik kaynak kullanın çalışır; Aksi halde statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a129-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a129-107">Dinamik kaynaklarınız anahtar sözcüğü *anahtar* özellik adı eklenir.</span><span class="sxs-lookup"><span data-stu-id="3a129-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="3a129-108">Aşağıdaki örnek, erişim ve stil veya bir düğmeyi özelleştirmek için sistem yazı tipi dinamik kaynaklarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a129-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="3a129-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek oluşturur atayan bir düğme stili <xref:System.Windows.SystemFonts> değerleri bir düğme.</span><span class="sxs-lookup"><span data-stu-id="3a129-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a129-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a129-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="3a129-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a129-111">See Also</span></span>  
 [<span data-ttu-id="3a129-112">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="3a129-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="3a129-113">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a129-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="3a129-114">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a129-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
