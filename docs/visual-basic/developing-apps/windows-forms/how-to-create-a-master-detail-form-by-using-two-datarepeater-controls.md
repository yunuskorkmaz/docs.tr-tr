---
title: "Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana / ayrıntı formu oluşturma"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02f98cce74f99d8a00bc916b38e5c290045926a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="d2d1f-102">Nasıl Yapılır: İki DataRepeater Denetimi Kullanarak Ana Öğe/Ayrıntı Formu Oluşturma (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d2d1f-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="d2d1f-103">İki veya daha fazla kullanarak ilgili verileri görüntüleyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimleri ana/ayrıntı formu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="d2d1f-104">Örneğin, müşterilerin listesini birinde görüntülemek isteyebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ve kullanıcı bir müşteri seçtiğinde, ikinci bir müşterinin siparişleri listesini görüntülemek <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="d2d1f-105">Aynı ana tablo düğümünden paylaşma ayrıntı öğeleri sürükleyerek ilgili verileri görüntüleyebilir **veri kaynakları** penceresi üzerine bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="d2d1f-106">Müşteriler tablosu ile ilişkili bir sipariş tabloda sahip bir veri kaynağı varsa, örneğin, her iki tabloyu ağaç görünümünde üst düzey düğüm şeklinde gördüğünüz **veri kaynakları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="d2d1f-107">Sütunları görebilmeniz için müşteriler düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="d2d1f-108">Listedeki son sütunun Siparişler tablosundaki temsil eden bir Genişletilebilir düğümü olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="d2d1f-109">Bu düğüm, bir müşteri için ilgili siparişleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="d2d1f-110">İçinde iki DataRepeater denetimi ilgili verileri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="d2d1f-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="d2d1f-111">İki <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetimleri **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="d2d1f-112">Denetimleri boyut ve yan yana konumlandırmak için boyutlandırma ve konumu tanıtıcıları sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="d2d1f-113">Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster**.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2d1f-114">Varsa **veri kaynakları** penceresi boşsa, bir veri kaynağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="d2d1f-115">Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="d2d1f-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="d2d1f-116">İçinde **veri kaynakları** penceresi, üst düzey düğüm için ana tablo seçin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="d2d1f-117">Tıklatarak ana tablo bırakma türü için ayrıntıları değiştirin **ayrıntıları** Tablo düğümü aşağı açılan listesinde.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="d2d1f-118">Ana Tablo düğümü ilk öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="d2d1f-119">Ana Tablo düğümünü genişletin ve ilişkili tablo ayrıntı düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="d2d1f-120">Tıklayarak ayrıntıları ayrıntı tablosunu açılan türünü değiştirme **ayrıntıları** Tablo düğümü aşağı açılan listesinde.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="d2d1f-121">Bu tablo düğümü seçin ve ikinci öğe şablonu bölgesi sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d1f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d1f-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="d2d1f-123">DataRepeater denetimine giriş</span><span class="sxs-lookup"><span data-stu-id="d2d1f-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d2d1f-124">Nasıl yapılır: DataRepeater denetiminde veri bağlı</span><span class="sxs-lookup"><span data-stu-id="d2d1f-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d2d1f-125">Nasıl yapılır: görüntü Windows Forms uygulamalarındaki ilgili verileri</span><span class="sxs-lookup"><span data-stu-id="d2d1f-125">How to: Display Related Data in a Windows Forms Application</span></span>](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)  
 [<span data-ttu-id="d2d1f-126">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="d2d1f-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d2d1f-127">DataRepeater denetiminde sorun giderme</span><span class="sxs-lookup"><span data-stu-id="d2d1f-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
