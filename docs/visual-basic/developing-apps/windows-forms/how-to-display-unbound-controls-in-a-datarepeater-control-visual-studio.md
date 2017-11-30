---
title: "Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="63933-102">Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="63933-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="63933-103">Bağlama denetimleri ek olarak, diğer denetimler için eklemek isteyebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>statik bir etiket veya her öğe üzerinde yinelenen bir görüntü gibi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="63933-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63933-104">De en az bir ilişkili denetim olmalıdır <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> veya hiçbir şey çalışma zamanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="63933-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="63933-105">Bir DataRepeater bağlanmamış denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="63933-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="63933-106">Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="63933-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="63933-107">Boyutlandırma ve konumu tanıtıcıları boyuta sürükleyin ve denetim getirin.</span><span class="sxs-lookup"><span data-stu-id="63933-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="63933-108">Ayrıca boyut ve değiştirerek denetimi Yerleştir **boyutu** ve **konumu** Özellikleri penceresinde özellikler.</span><span class="sxs-lookup"><span data-stu-id="63933-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="63933-109">En az bir veri bağlama denetimine ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="63933-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="63933-110">Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüle](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="63933-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="63933-111">Denetimden sürükleyin **araç** öğesi şablonu bölgesini üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="63933-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="63933-112">Denetim iki dikdörtgen bölgeler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="63933-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="63933-113">İç bölgesi *öğe şablonu*; şablona eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim.</span><span class="sxs-lookup"><span data-stu-id="63933-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="63933-114">Dış bölgedir *görünüm penceresinin*, burada öğeleri görüntülenir; bu bölgeye eklenen denetimlerini çalışma zamanında görüntülenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="63933-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63933-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63933-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="63933-116">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="63933-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="63933-117">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="63933-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="63933-118">Nasıl yapılır: DataRepeater denetiminde veri bağlı</span><span class="sxs-lookup"><span data-stu-id="63933-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="63933-119">Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="63933-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="63933-120">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="63933-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
