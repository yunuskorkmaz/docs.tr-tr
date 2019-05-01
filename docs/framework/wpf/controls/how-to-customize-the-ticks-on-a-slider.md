---
title: 'Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 3b32bbedb5f654ce75e90a827eb0c4dba1d4d345
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910695"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="c74b9-102">Nasıl yapılır: Kaydırıcı Üzerinde İşaretleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c74b9-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="c74b9-103">Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> çizgilerinin olan denetim.</span><span class="sxs-lookup"><span data-stu-id="c74b9-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c74b9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c74b9-104">Example</span></span>  
 <span data-ttu-id="c74b9-105"><xref:System.Windows.Controls.Primitives.TickBar> Ayarladığınızda görüntüler <xref:System.Windows.Controls.Slider.TickPlacement%2A> dışında bir değere <xref:System.Windows.Controls.Primitives.TickPlacement.None>, varsayılan değer olan.</span><span class="sxs-lookup"><span data-stu-id="c74b9-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="c74b9-106">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Slider> ile bir <xref:System.Windows.Controls.Primitives.TickBar> işaretleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c74b9-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="c74b9-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> Ve <xref:System.Windows.Controls.Slider.TickFrequency%2A> özelliklerini değer çizgilerinin ve aralarındaki aralığı konumunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c74b9-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="c74b9-108">Taşıdığınızda <xref:System.Windows.Controls.Primitives.Thumb>, araç ipuçlarını görüntüleme değerini <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="c74b9-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="c74b9-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Özelliği, araç ipucunun nerede gerçekleştiği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c74b9-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="c74b9-110"><xref:System.Windows.Controls.Primitives.Thumb> Hareketleri çünkü çizgilerinin konumuna karşılık gelen <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="c74b9-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="c74b9-111">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Slider.Ticks%2A> boyunca değer çizgisi oluşturmak için özellik <xref:System.Windows.Controls.Slider> düzensiz aralıklarla.</span><span class="sxs-lookup"><span data-stu-id="c74b9-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](~/samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c74b9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c74b9-112">See also</span></span>

- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- <span data-ttu-id="c74b9-113">[Nasıl yapılır: Bir özellik değeri için bir kaydırıcı bağlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c74b9-113">[How to: Bind a Slider to a Property Value](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))</span></span>
