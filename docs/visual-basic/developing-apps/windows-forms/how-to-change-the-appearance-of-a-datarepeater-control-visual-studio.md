---
title: "Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="afa24-102">Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="afa24-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="afa24-103">Görünümünü değiştirme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> özellikleri ayarlayarak tasarım zamanında veya işleme tarafından çalışma zamanında denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay.</span><span class="sxs-lookup"><span data-stu-id="afa24-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="afa24-104">Denetim öğesi şablon bölümünü seçildiğinde tasarım zamanında ayarlama özellikleri yinelenen her biri için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="afa24-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="afa24-105">Görünüm ilgili özelliklerini <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimin kendisini görünmeyecektir sınamayla eksikse bir kapsayıcı kısmını değişmeden çalışma zamanında (örneğin, <xref:System.Windows.Forms.Control.Padding%2A> özelliği, büyük bir değere ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="afa24-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="afa24-106">Çalışma zamanında, görünüm ilgili özellikler koşullara göre ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="afa24-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="afa24-107">Örneğin, bir zamanlama uygulamasında öğeyi vadesi geçmiş olduğunda kullanıcıları uyarmak için bir öğe arka plan rengini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afa24-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="afa24-108">İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> bir özelliği bir koşullu ifade gibi ayarlarsanız olay işleyicisi `If…Then`, ayrıca kullanmanız gerekir bir `Else` koşulu karşılanmadı ne zaman görünümünü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="afa24-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="afa24-109">Tasarım zamanında görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="afa24-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="afa24-110">Windows Forms Tasarımcısı'nda öğesi şablonu (üst) bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="afa24-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="afa24-111">Özellikleri penceresinde bir özellik seçin ve değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="afa24-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="afa24-112">Görünüm etkileyen ortak özellikler dahil <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, ve <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="afa24-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="afa24-113">Çalışma zamanında görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="afa24-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="afa24-114">Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="afa24-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="afa24-115">İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi özelliklerini ayarlamak için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="afa24-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="afa24-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="afa24-116">Example</span></span>  
 <span data-ttu-id="afa24-117">Bazı yaygın özelleştirmeler için <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim dahil renkleri değişen ve bir koşula göre bir alan rengi değiştirme satırları görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="afa24-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="afa24-118">Aşağıdaki örnek, bu özelleştirmeler gerçekleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="afa24-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="afa24-119">Bu örnek, sahibi olduğunuzu varsayar. bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind veritabanı Ürünler tablosuna bağlı denetimi.</span><span class="sxs-lookup"><span data-stu-id="afa24-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="afa24-120">Her iki bu özelleştirmeler için iki tarafı da koşul özelliklerini ayarlamak için kodu sağlamalısınız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="afa24-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="afa24-121">Belirtmezseniz, `Else` koşul, çalışma zamanında beklenmeyen sonuçlar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="afa24-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa24-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afa24-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="afa24-123">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="afa24-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="afa24-124">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="afa24-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="afa24-125">Nasıl yapılır: DataRepeater denetiminde veri bağlı</span><span class="sxs-lookup"><span data-stu-id="afa24-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="afa24-126">Nasıl yapılır: ilişkisiz denetimleri DataRepeater denetiminde görüntüleme</span><span class="sxs-lookup"><span data-stu-id="afa24-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="afa24-127">Nasıl yapılır: DataRepeater denetiminde öğe üstbilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="afa24-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
