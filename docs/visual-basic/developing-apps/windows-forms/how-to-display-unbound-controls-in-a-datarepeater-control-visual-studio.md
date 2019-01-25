---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730795"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="2eed5-102">Nasıl yapılır: (Visual Studio) DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2eed5-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="2eed5-103">Bağlama denetimleri ek olarak, diğer denetimler eklemek isteyebileceğiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>statik etiket veya her öğesine yinelenen görüntü gibi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2eed5-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2eed5-104">Ayrıca en az bir bağlantılı denetim olmalıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> veya hiçbir şey çalışma zamanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2eed5-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="2eed5-105">Bağlanmamış denetimler için bir DataRepeater eklemek için</span><span class="sxs-lookup"><span data-stu-id="2eed5-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="2eed5-106">Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="2eed5-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="2eed5-107">Boyut ve konum tutamaçları boyutuna sürükleyin ve denetimi konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="2eed5-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="2eed5-108">Ayrıca boyutu ve değiştirerek denetimin konumunu **boyutu** ve **konumu** özellikleri Özellikler penceresinde.</span><span class="sxs-lookup"><span data-stu-id="2eed5-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="2eed5-109">En az bir veri bağlama denetimine ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2eed5-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="2eed5-110">Daha fazla bilgi için [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2eed5-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="2eed5-111">Bir denetimi **araç kutusu** öğe şablonu bölgesi üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2eed5-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="2eed5-112">Denetim dikdörtgen iki bölgeleri olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2eed5-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="2eed5-113">İç bölgesi *öğe şablonu*; şablonuna eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim.</span><span class="sxs-lookup"><span data-stu-id="2eed5-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="2eed5-114">Dış bölgedir *Görünüm penceresi*, burada öğeler görüntülenir; bu bölgeye eklenen denetimlerin çalışma zamanında görüntülenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="2eed5-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eed5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eed5-115">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="2eed5-116">DataRepeater Denetimine Giriş</span><span class="sxs-lookup"><span data-stu-id="2eed5-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2eed5-117">DataRepeater Denetiminde Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="2eed5-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2eed5-118">Nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2eed5-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2eed5-119">Nasıl yapılır: (Visual Studio) iki DataRepeater denetimi kullanarak ana/ayrıntı formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="2eed5-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [<span data-ttu-id="2eed5-120">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="2eed5-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
