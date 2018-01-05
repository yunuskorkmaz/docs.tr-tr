---
title: DataGridView Denetimi Mimarisi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b3e51b87cdd766adcc10aa3f682647b28fbbe4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="f4c64-102">DataGridView Denetimi Mimarisi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f4c64-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="f4c64-103"><xref:System.Windows.Forms.DataGridView> Denetim ve ilişkili sınıfları görüntüleme ve tablo veri düzenlemek için esnek ve Genişletilebilir bir sistem olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4c64-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="f4c64-104">Bu sınıfların tüm bulunan <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ve tüm adlı "DataGridView" öneki.</span><span class="sxs-lookup"><span data-stu-id="f4c64-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="f4c64-105">Mimari öğeleri</span><span class="sxs-lookup"><span data-stu-id="f4c64-105">Architecture Elements</span></span>  
 <span data-ttu-id="f4c64-106">Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları türetilen <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="f4c64-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="f4c64-107">Aşağıdaki nesne modeli gösterilmektedir <xref:System.Windows.Forms.DataGridViewElement> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="f4c64-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="f4c64-108">![DataGridViewElement nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="f4c64-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="f4c64-109">DataGridViewElement nesne modeli</span><span class="sxs-lookup"><span data-stu-id="f4c64-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="f4c64-110"><xref:System.Windows.Forms.DataGridViewElement> Sınıfı, üst bir başvuru sağlar <xref:System.Windows.Forms.DataGridView> denetlemek ve sahip bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> değerlerinden bileşimini temsil eden bir değer tutan özelliği <xref:System.Windows.Forms.DataGridViewElementStates> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f4c64-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="f4c64-111">Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> Yahoo! companion daha ayrıntılı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f4c64-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="f4c64-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="f4c64-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="f4c64-113"><xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:</span><span class="sxs-lookup"><span data-stu-id="f4c64-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="f4c64-114">Bu numaralandırma değerlerinin Bitsel mantıksal işleçlerle birleştirilebilir böylece <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği express birden fazla durum aynı anda.</span><span class="sxs-lookup"><span data-stu-id="f4c64-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="f4c64-115">Örneğin, bir <xref:System.Windows.Forms.DataGridViewElement> aynı anda olabilir <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="f4c64-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="f4c64-116">Hücreleri ve bantları</span><span class="sxs-lookup"><span data-stu-id="f4c64-116">Cells and Bands</span></span>  
 <span data-ttu-id="f4c64-117"><xref:System.Windows.Forms.DataGridView> Denetim nesneleri iki temel tür oluşur: hücreleri ve bantları.</span><span class="sxs-lookup"><span data-stu-id="f4c64-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="f4c64-118">Tüm hücreleri türetin <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4c64-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="f4c64-119">Bantlar, iki tür <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, her ikisi de öğesinden türetilen <xref:System.Windows.Forms.DataGridViewBand> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4c64-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="f4c64-120"><xref:System.Windows.Forms.DataGridView> Denetim birkaç sınıfları ile birlikte çalışır, ancak en yaygın olarak karşılaşılan olan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, ve <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="f4c64-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="f4c64-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="f4c64-121">DataGridViewCell</span></span>  
 <span data-ttu-id="f4c64-122">Hücre etkileşim için temel birimidir <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f4c64-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="f4c64-123">Görüntü hücreleri ortalanır ve veri girişini genellikle hücreleri gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f4c64-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="f4c64-124">Hücreleri kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonu <xref:System.Windows.Forms.DataGridViewRow> sınıfı ve erişebilir seçili hücreleri kullanarak <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonu <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="f4c64-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f4c64-125">Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewCell> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="f4c64-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="f4c64-126">![DataGridViewCell nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="f4c64-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="f4c64-127">DataGridViewCell nesne modeli</span><span class="sxs-lookup"><span data-stu-id="f4c64-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="f4c64-128"><xref:System.Windows.Forms.DataGridViewCell> Türüdür kendisinden türetilen tüm hücre türleri Özet temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="f4c64-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="f4c64-129"><xref:System.Windows.Forms.DataGridViewCell>ve türetilmiş türlerini Windows Forms denetimleri, ancak bazı ana bilgisayar Windows Forms denetimleri olup olmadığı.</span><span class="sxs-lookup"><span data-stu-id="f4c64-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="f4c64-130">Bir hücre tarafından desteklenen herhangi bir düzenleme işlevsellik genellikle barındırılan denetim tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="f4c64-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="f4c64-131"><xref:System.Windows.Forms.DataGridViewCell>Windows Forms denetimleri gibi nesneleri kendi Görünüm ve boyama özellikleri aynı şekilde kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="f4c64-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="f4c64-132">Bunun yerine, <xref:System.Windows.Forms.DataGridView> görünümünü için sorumlu kendi <xref:System.Windows.Forms.DataGridViewCell> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f4c64-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="f4c64-133">İle etkileşim kurarak görünümünü ve davranışını hücrelerin önemli ölçüde etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimin özellikleri ve olayları.</span><span class="sxs-lookup"><span data-stu-id="f4c64-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="f4c64-134">Özellikleri dışında olan özelleştirmeler için özel gereksinimleri olduğunda <xref:System.Windows.Forms.DataGridView> denetim, türetilen kendi sınıfı uygulayabilirsiniz <xref:System.Windows.Forms.DataGridViewCell> ya da alt sınıflarından biri.</span><span class="sxs-lookup"><span data-stu-id="f4c64-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="f4c64-135">Aşağıdaki liste öğesinden türetilmiş sınıfları gösterir <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="f4c64-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="f4c64-136">Özel hücre türleri</span><span class="sxs-lookup"><span data-stu-id="f4c64-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="f4c64-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="f4c64-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="f4c64-138">Şeması <xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposu olarak ifade edilir <xref:System.Windows.Forms.DataGridView> denetimin sütun.</span><span class="sxs-lookup"><span data-stu-id="f4c64-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="f4c64-139">Erişebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin sütunları <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4c64-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="f4c64-140">Seçili sütunları kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4c64-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="f4c64-141">Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewColumn> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="f4c64-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="f4c64-142">![DataGridViewColumn nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="f4c64-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="f4c64-143">DataGridViewColumn nesne modeli</span><span class="sxs-lookup"><span data-stu-id="f4c64-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="f4c64-144">Anahtar hücresi türlerinden bazıları karşılık gelen sütun türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f4c64-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="f4c64-145">Bu türetilmiş <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4c64-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="f4c64-146">Aşağıdaki liste öğesinden türetilmiş sınıfları gösterir <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="f4c64-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="f4c64-147">Özel sütun türleri</span><span class="sxs-lookup"><span data-stu-id="f4c64-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="f4c64-148">DataGridView düzenleme denetimleri</span><span class="sxs-lookup"><span data-stu-id="f4c64-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="f4c64-149">Gelişmiş düzenleme işlevi genellikle destek hücreleri bir Windows Forms denetiminden türetilen barındırılan bir denetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4c64-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="f4c64-150">Ayrıca bu denetimleri uygulayın <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f4c64-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="f4c64-151">Aşağıdaki nesne modeli bu denetimlerinin kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f4c64-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="f4c64-152">![DataGridView denetimi nesne modeli düzenleme](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="f4c64-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="f4c64-153">DataGridView düzenleme denetimi nesne modeli</span><span class="sxs-lookup"><span data-stu-id="f4c64-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="f4c64-154">Aşağıdaki düzenleme denetimleri ile sağlanan <xref:System.Windows.Forms.DataGridView> denetimi:</span><span class="sxs-lookup"><span data-stu-id="f4c64-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="f4c64-155">Kendi düzenleme denetimleri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView hücrelerinde ana bilgisayar denetimleri](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="f4c64-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="f4c64-156">Aşağıdaki tabloda hücre türleri, sütun türleri ve düzenleme denetimleri arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4c64-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="f4c64-157">Hücre türü</span><span class="sxs-lookup"><span data-stu-id="f4c64-157">Cell type</span></span>|<span data-ttu-id="f4c64-158">Barındırılan denetimi</span><span class="sxs-lookup"><span data-stu-id="f4c64-158">Hosted control</span></span>|<span data-ttu-id="f4c64-159">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="f4c64-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="f4c64-160">yok</span><span class="sxs-lookup"><span data-stu-id="f4c64-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="f4c64-161">yok</span><span class="sxs-lookup"><span data-stu-id="f4c64-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="f4c64-162">yok</span><span class="sxs-lookup"><span data-stu-id="f4c64-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="f4c64-163">yok</span><span class="sxs-lookup"><span data-stu-id="f4c64-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="f4c64-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="f4c64-164">DataGridViewRow</span></span>  
 <span data-ttu-id="f4c64-165"><xref:System.Windows.Forms.DataGridViewRow> Sınıfı görüntüler bir kaydın veri alanları verileri depolamak için <xref:System.Windows.Forms.DataGridView> denetim eklenmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f4c64-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="f4c64-166">Erişebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin satırları <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4c64-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="f4c64-167">Seçili satırları kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f4c64-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="f4c64-168">Aşağıdaki nesne modeli bu kullanım gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewRow> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="f4c64-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="f4c64-169">![DataGridViewRow nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="f4c64-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="f4c64-170">DataGridViewRow nesne modeli</span><span class="sxs-lookup"><span data-stu-id="f4c64-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="f4c64-171">Kendi türlerinden türetilemeyeceğini <xref:System.Windows.Forms.DataGridViewRow> bu genellikle gerekmeyecektir rağmen sınıf.</span><span class="sxs-lookup"><span data-stu-id="f4c64-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="f4c64-172"><xref:System.Windows.Forms.DataGridView> Kontrolünde birkaç satır ile ilgili olayları ve özellikleri davranışını özelleştirmek için kendi <xref:System.Windows.Forms.DataGridViewRow> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f4c64-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="f4c64-173">Etkinleştirirseniz, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, yeni satır eklemek için özel bir satır son satır olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="f4c64-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="f4c64-174">Bu satır parçası olan <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu, ancak dikkat etmeniz gereken özel işlevselliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f4c64-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="f4c64-175">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f4c64-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c64-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4c64-176">See Also</span></span>  
 [<span data-ttu-id="f4c64-177">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4c64-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="f4c64-178">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f4c64-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f4c64-179">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4c64-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
