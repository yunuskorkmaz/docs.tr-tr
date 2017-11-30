---
title: "Nasıl Yapılır: DataRepeater Denetiminde Öğe Üstbilgilerini Görüntüleme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da02f9374471a581a58131e26d618f91d7cbb7af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="5f901-102">Nasıl Yapılır: DataRepeater Denetiminde Öğe Üstbilgilerini Görüntüleme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5f901-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="5f901-103">Öğe üstbilgisinde bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim görsel bir gösterge sağlar, bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> seçilir.</span><span class="sxs-lookup"><span data-stu-id="5f901-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="5f901-104">Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (varsayılan), her bir öğe sola öğesi başlığı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="5f901-105">Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, öğesi üstbilgisinde her öğenin üst kısmında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="5f901-106">İlk seçildiğinde, öğesi üstbilgisi tarafından belirtilen renkte görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> özelliği ve beyaz ok simgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f901-107">Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe ilk seçildiğinde seçimi simgesi görünür olmaz.</span><span class="sxs-lookup"><span data-stu-id="5f901-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="5f901-108">Bir alan <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> odaktaki öğeyi üstbilgi değişiklikleri rengini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> arka plan rengi ve siyah ok simgesine yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="5f901-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="5f901-109">Veri değiştirdiyseniz, Kurşun Kalem simgesini öğesi başlığında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="5f901-110">Varsayılan genişlikteki (veya yükseklik zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) öğesi'nin üstbilgi 15 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="5f901-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) of the item header is 15 pixels.</span></span> <span data-ttu-id="5f901-111">Ayarlayarak genişliğini değiştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f901-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f901-112">Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlamak, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="5f901-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="5f901-113">Öğe üstbilgilerini ayarlayarak gizleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="5f901-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="5f901-114">Zaman <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ayarlanır **False**, öğe seçildiğinde yalnızca çevresinde noktalı çizgi göstergesidir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="5f901-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f901-115">İzleme tarafından kendi seçim göstergesini sağlayabilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> içinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olayı <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f901-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5f901-116">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f901-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="5f901-117">Öğe üstbilgilerini görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="5f901-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="5f901-118">Windows Forms Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f901-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f901-119">Denetimin alt bölgeyi seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f901-119">You must select the lower region of the control.</span></span> <span data-ttu-id="5f901-120">Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi Özellikler penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="5f901-121">Özellikler penceresini kullanın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> öğe üstbilgilerini rengini değiştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5f901-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f901-122">Ayarlarsanız <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> için <xref:System.Drawing.Color.White%2A>, öğe ilk seçildiğinde seçimi simgesi görünür olmaz.</span><span class="sxs-lookup"><span data-stu-id="5f901-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="5f901-123">Kullanım <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> öğe üstbilgilerini genişliğini (veya yükseklik) değiştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5f901-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f901-124">Varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> özelliği 11'den küçük bir değere ayarlamak, gösterge simgeleri öğesi üstbilgisinde görüntülenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="5f901-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="5f901-125">Öğe üstbilgilerini gizleme</span><span class="sxs-lookup"><span data-stu-id="5f901-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="5f901-126">Windows Forms Tasarımcısı'nda alt bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="5f901-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f901-127">Denetimin alt bölgeyi seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f901-127">You must select the lower region of the control.</span></span> <span data-ttu-id="5f901-128">Öğesi şablonu bölümüne seçerseniz, farklı bir özellikler kümesi Özellikler penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5f901-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="5f901-129">Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> özelliğine **False**.</span><span class="sxs-lookup"><span data-stu-id="5f901-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="5f901-130">Bir öğe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> olduğundan, tek belirti çevresinde noktalı çizgi seçilir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="5f901-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f901-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f901-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="5f901-132">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="5f901-132">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5f901-133">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="5f901-133">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5f901-134">Nasıl yapılır: DataRepeater denetimi düzenini değiştirme</span><span class="sxs-lookup"><span data-stu-id="5f901-134">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5f901-135">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5f901-135">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
