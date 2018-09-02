---
title: 'Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 045a2f540a37cdea84d2bf2f3ed1e74e122bdbb5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388312"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="7fc0a-102">Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7fc0a-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="7fc0a-103">Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> çizgilerinin olan denetim.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc0a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fc0a-104">Example</span></span>  
 <span data-ttu-id="7fc0a-105"><xref:System.Windows.Controls.Primitives.TickBar> Ayarladığınızda görüntüler <xref:System.Windows.Controls.Slider.TickPlacement%2A> dışında bir değere <xref:System.Windows.Controls.Primitives.TickPlacement.None>, varsayılan değer olan.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="7fc0a-106">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> ile bir <xref:System.Windows.Controls.Primitives.TickBar> işaretleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="7fc0a-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> Ve <xref:System.Windows.Controls.Slider.TickFrequency%2A> özelliklerini değer çizgilerinin ve aralarındaki aralığı konumunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="7fc0a-108">Taşıdığınızda <xref:System.Windows.Controls.Primitives.Thumb>, araç ipuçlarını görüntüleme değerini <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="7fc0a-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Özelliği, araç ipucunun nerede gerçekleştiği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="7fc0a-110"><xref:System.Windows.Controls.Primitives.Thumb> Hareketleri çünkü çizgilerinin konumuna karşılık gelen <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="7fc0a-111">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Slider.Ticks%2A> boyunca değer çizgisi oluşturmak için özellik <xref:System.Windows.Controls.Slider> düzensiz aralıklarla.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7fc0a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7fc0a-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="7fc0a-113">Kaydırıcı ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="7fc0a-113">Slider How-to Topics</span></span>](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
