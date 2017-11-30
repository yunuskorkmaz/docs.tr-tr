---
title: "Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770003c8879661bfc1ce683f5b6ed84483cf47ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="4db29-102">Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="4db29-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="4db29-103">En yaygın kullanımı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimidir bir veritabanı veya başka bir veri kaynağını ilişkili verileri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="4db29-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="4db29-104">Bağlama denetimleri ek olarak, statik bir etiket veya her öğe üzerinde yinelenen bir görüntü gibi diğer denetimleri eklemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="4db29-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="4db29-105">Daha fazla bilgi için bkz: [nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4db29-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="4db29-106">Ayarlayarak çalışma zamanında bir veri kaynağına bağlayabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> özelliğine `True` ve bir veri kaynağına atama <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4db29-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="4db29-107">Bu durumda, veri kaynağı ile tüm etkileşimi yönetmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="4db29-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="4db29-108">Daha fazla bilgi için bkz: [DataRepeater denetiminde sanal mod](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4db29-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="4db29-109">Veri bağlama DataRepeater oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4db29-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="4db29-110">Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="4db29-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="4db29-111">Boyutlandırma ve konumu tanıtıcıları boyuta sürükleyin ve denetim getirin.</span><span class="sxs-lookup"><span data-stu-id="4db29-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="4db29-112">Denetim iki dikdörtgen bölgeler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4db29-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="4db29-113">Üst bölge *öğe şablonu*; şablona eklenen denetimler yinelenen her öğesinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> çalışma zamanında denetim.</span><span class="sxs-lookup"><span data-stu-id="4db29-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="4db29-114">Alt bölge *görünüm penceresinin*, öğeleri burada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4db29-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="4db29-115">Ayrıca boyut ve denetim veya öğe şablonu değiştirerek Yerleştir **boyutu** ve **konumu** Özellikleri penceresinde özellikler.</span><span class="sxs-lookup"><span data-stu-id="4db29-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="4db29-116">Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster**.</span><span class="sxs-lookup"><span data-stu-id="4db29-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4db29-117">Varsa **veri kaynakları** penceresi boşsa, bir veri kaynağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4db29-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="4db29-118">Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="4db29-118">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="4db29-119">İçinde **veri kaynakları** penceresi, üst düzey düğüm bağlamak istediğiniz verileri içeren bir tablo için seçin.</span><span class="sxs-lookup"><span data-stu-id="4db29-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="4db29-120">Tabloya açılan türünü değiştirme `Details` tıklayarak `Details` Tablo düğümü aşağı açılan listesinde.</span><span class="sxs-lookup"><span data-stu-id="4db29-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="4db29-121">Tablo düğümü seçin ve Madde şablonu bölgesini sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="4db29-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="4db29-122">Hangi tür denetimler için her bir alan görüntülenen belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4db29-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="4db29-123">Daha fazla bilgi için bkz: [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimini ayarlama](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span><span class="sxs-lookup"><span data-stu-id="4db29-123">For more information, see [Set the control to be created when dragging from the Data Sources window](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db29-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4db29-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="4db29-125">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="4db29-125">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4db29-126">Nasıl yapılır: ilişkisiz denetimleri DataRepeater denetiminde görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4db29-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4db29-127">Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="4db29-127">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="4db29-128">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="4db29-128">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4db29-129">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4db29-129">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
