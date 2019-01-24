---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetiminin görünümünü değiştirme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716641"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="4f353-102">Nasıl yapılır: (Visual Studio) DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="4f353-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="4f353-103">Görünümünü değiştirebilirsiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim özelliklerini ayarlayarak, tasarım zamanında ya da işlem tarafından çalışma zamanında <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay.</span><span class="sxs-lookup"><span data-stu-id="4f353-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="4f353-104">Denetim öğesi şablon bölümü seçili olduğunda tasarım zamanında ayarlama özellikleri yinelenen her biri için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="4f353-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="4f353-105">Görünüm ile ilgili özellikleri <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetiminin kendisinin görünmeyecektir olgunlaştıkça yalnızca şu durumlarda bir kapsayıcının bölümü sola çalışma zamanında (örneğin, <xref:System.Windows.Forms.Control.Padding%2A> özelliği, büyük bir değere ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="4f353-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="4f353-106">Çalışma zamanında, görünüm ilgili özellikler koşullara göre ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4f353-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="4f353-107">Örneğin, bir zamanlama uygulamasında, süresi geçmiş bir öğe olduğunda kullanıcıları uyarmak için bir öğe arka plan rengini değişebilir.</span><span class="sxs-lookup"><span data-stu-id="4f353-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="4f353-108">İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi, bir özelliği bir koşullu deyimde gibi ayarlarsanız `If…Then`, de kullanmanız gerekir bir `Else` koşul karşılanmadığında görünümünü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4f353-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="4f353-109">Tasarım zamanında görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4f353-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="4f353-110">Windows Form Tasarımcısı'nda öğe şablonu (üst) bölgesi seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4f353-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="4f353-111">Özellikler penceresinde, bir özellik seçin ve değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4f353-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="4f353-112">Görünüm etkileyen yaygın özellikler dahil <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, ve <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f353-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="4f353-113">Çalışma zamanında görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4f353-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="4f353-114">Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="4f353-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="4f353-115">İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi özelliklerini ayarlamak için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4f353-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4f353-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f353-116">Example</span></span>  
 <span data-ttu-id="4f353-117">Sık karşılaşılan bazı özelleştirmeler için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi içeren satırları rengini değiştirme ve bir koşula göre bir alanın rengi değiştirme görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="4f353-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="4f353-118">Aşağıdaki örnekte şu özelleştirmeleri yapmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f353-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="4f353-119">Bu örnekte, sahibi olduğunuzu varsayar bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind veritabanındaki ürünleri tabloya bağlı denetim.</span><span class="sxs-lookup"><span data-stu-id="4f353-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="4f353-120">Her iki bu özelleştirmeler için her iki tarafında bir koşul için özellikleri ayarlamak üzere kod sağlamalısınız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f353-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="4f353-121">Siz belirtmezseniz `Else` koşulu, çalışma zamanında beklenmeyen sonuçlar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="4f353-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f353-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f353-122">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [<span data-ttu-id="4f353-123">DataRepeater Denetimine Giriş</span><span class="sxs-lookup"><span data-stu-id="4f353-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="4f353-124">DataRepeater Denetiminde Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="4f353-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="4f353-125">Nasıl yapılır: DataRepeater denetiminde bağlı verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4f353-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="4f353-126">Nasıl yapılır: DataRepeater denetimindeki ilişkisiz denetimleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4f353-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="4f353-127">Nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4f353-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
