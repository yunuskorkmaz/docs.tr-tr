---
title: DataGridView Denetimi Mimarisi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: c57f7d22219c0cda91dad174be4e225808a9949d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494931"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="21195-102">DataGridView Denetimi Mimarisi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="21195-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="21195-103"><xref:System.Windows.Forms.DataGridView> Denetimi ve ilişkili sınıflarının görüntüleme ve düzenleme sekmeli veri için esnek, Genişletilebilir bir sistem için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="21195-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="21195-104">Bu sınıfların tümü bulunur <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı ve tüm adlandırılmış "DataGridView" ön ekine sahip.</span><span class="sxs-lookup"><span data-stu-id="21195-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="21195-105">Mimari öğeler</span><span class="sxs-lookup"><span data-stu-id="21195-105">Architecture Elements</span></span>  
 <span data-ttu-id="21195-106">Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıflar türetilen <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="21195-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="21195-107">Aşağıdaki nesne modelini göstermektedir <xref:System.Windows.Forms.DataGridViewElement> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="21195-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="21195-108">![DataGridViewElement nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="21195-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="21195-109">DataGridViewElement nesne modeli</span><span class="sxs-lookup"><span data-stu-id="21195-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="21195-110"><xref:System.Windows.Forms.DataGridViewElement> Sınıfı üst öğeye bir başvuru sağlar <xref:System.Windows.Forms.DataGridView> denetlemek ve sahip bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> değerlerinden bir birleşimini gösteren bir değer tutuyor özelliği <xref:System.Windows.Forms.DataGridViewElementStates> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="21195-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="21195-111">Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> Yahoo! companion daha ayrıntılı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="21195-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="21195-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="21195-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="21195-113"><xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:</span><span class="sxs-lookup"><span data-stu-id="21195-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="21195-114">Bu numaralandırma değerlerinin bit düzeyinde mantıksal işleçler ile birleştirilebilir böylece <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği express birden fazla durum tek seferde.</span><span class="sxs-lookup"><span data-stu-id="21195-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="21195-115">Örneğin, bir <xref:System.Windows.Forms.DataGridViewElement> aynı anda olabilir <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="21195-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="21195-116">Hücreleri ve bantları</span><span class="sxs-lookup"><span data-stu-id="21195-116">Cells and Bands</span></span>  
 <span data-ttu-id="21195-117"><xref:System.Windows.Forms.DataGridView> Denetimi içeren iki temel nesne türleri: hücreleri ve bantları.</span><span class="sxs-lookup"><span data-stu-id="21195-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="21195-118">Tüm hücrelerini türetir <xref:System.Windows.Forms.DataGridViewCell> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21195-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="21195-119">Bant, iki tür <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, hem türetilen <xref:System.Windows.Forms.DataGridViewBand> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21195-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="21195-120"><xref:System.Windows.Forms.DataGridView> Denetimi birkaç sınıflarla birlikte çalışır, ancak en sık karşılaşılan olan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, ve <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="21195-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="21195-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="21195-121">DataGridViewCell</span></span>  
 <span data-ttu-id="21195-122">Hücre etkileşimi için temel birimdir <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="21195-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="21195-123">Görüntü hücreleri ortalanır ve veri girişini çoğunlukla hücreleri gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21195-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="21195-124">Hücreleri kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonunu <xref:System.Windows.Forms.DataGridViewRow> sınıfı ve seçili hücreleri kullanarak erişebilirsiniz <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonunu <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="21195-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="21195-125">Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewCell> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="21195-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="21195-126">![DataGridViewCell nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="21195-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="21195-127">DataGridViewCell nesne modeli</span><span class="sxs-lookup"><span data-stu-id="21195-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="21195-128"><xref:System.Windows.Forms.DataGridViewCell> Tüm hücre türleri türettiğiniz soyut temel sınıf türüdür.</span><span class="sxs-lookup"><span data-stu-id="21195-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="21195-129"><xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş türlerini Windows Forms denetimleri, ancak bazı ana bilgisayar Windows Forms denetimleri değildir.</span><span class="sxs-lookup"><span data-stu-id="21195-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="21195-130">Bir hücreyi tarafından desteklenen herhangi bir düzenleme işlevi genellikle barındırılan bir denetim tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="21195-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="21195-131"><xref:System.Windows.Forms.DataGridViewCell> Windows Forms denetimleri gibi nesneleri kendi Görünüm ve bir boyama özellikleri aynı şekilde kontrol.</span><span class="sxs-lookup"><span data-stu-id="21195-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="21195-132">Bunun yerine, <xref:System.Windows.Forms.DataGridView> görünümünü için sorumlu kendi <xref:System.Windows.Forms.DataGridViewCell> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="21195-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="21195-133">İle etkileşim kurarak görünümünü ve davranışını hücre önemli ölçüde etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimin özellikleri ve olayları.</span><span class="sxs-lookup"><span data-stu-id="21195-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="21195-134">Sunulan özelliklerin ötesine olan özelleştirmeleri özel gereksinimleriniz varsa <xref:System.Windows.Forms.DataGridView> denetimi, türetilen kendi sınıfınızı uygulayabilirsiniz <xref:System.Windows.Forms.DataGridViewCell> veya onun alt sınıflarından birini.</span><span class="sxs-lookup"><span data-stu-id="21195-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="21195-135">Aşağıdaki liste öğelerinden türetilen sınıfları gösterir <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="21195-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
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
  
-   <span data-ttu-id="21195-136">Özel hücre türlerinizi</span><span class="sxs-lookup"><span data-stu-id="21195-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="21195-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="21195-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="21195-138">Şemasını <xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposu olarak ifade edilir <xref:System.Windows.Forms.DataGridView> denetimin sütunları.</span><span class="sxs-lookup"><span data-stu-id="21195-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="21195-139">Erişebildiğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetimin sütunları <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21195-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="21195-140">Seçili sütunları kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21195-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="21195-141">Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewColumn> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="21195-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="21195-142">![DataGridViewColumn nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="21195-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="21195-143">DataGridViewColumn nesne modeli</span><span class="sxs-lookup"><span data-stu-id="21195-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="21195-144">Bazı anahtar hücresi türlerine karşılık gelen sütun türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="21195-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="21195-145">Bu türetilmiş <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21195-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="21195-146">Aşağıdaki liste öğelerinden türetilen sınıfları gösterir <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="21195-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="21195-147">Özel sütun türleri</span><span class="sxs-lookup"><span data-stu-id="21195-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="21195-148">DataGridView denetimi düzenleme</span><span class="sxs-lookup"><span data-stu-id="21195-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="21195-149">Gelişmiş düzenleme işlevi genellikle destekleyen hücreleri bir Windows Forms denetiminden türetilen bir denetimden kullanın.</span><span class="sxs-lookup"><span data-stu-id="21195-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="21195-150">Bu denetimler Ayrıca uygulama <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21195-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="21195-151">Aşağıdaki nesne modeli, bu denetimleri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21195-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="21195-152">![DataGridView denetimi nesne modeli düzenleme](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="21195-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="21195-153">DataGridView düzenleme denetimi nesne modeli</span><span class="sxs-lookup"><span data-stu-id="21195-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="21195-154">Aşağıdaki düzenleme denetimleri ile sağlanan <xref:System.Windows.Forms.DataGridView> denetimi:</span><span class="sxs-lookup"><span data-stu-id="21195-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="21195-155">Kendi düzenleme denetimler oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="21195-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="21195-156">Aşağıdaki tabloda, düzenleme denetimleri hücre türleri ve sütun türleri arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="21195-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="21195-157">Hücresi türü</span><span class="sxs-lookup"><span data-stu-id="21195-157">Cell type</span></span>|<span data-ttu-id="21195-158">Barındırılan denetim</span><span class="sxs-lookup"><span data-stu-id="21195-158">Hosted control</span></span>|<span data-ttu-id="21195-159">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="21195-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="21195-160">yok</span><span class="sxs-lookup"><span data-stu-id="21195-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="21195-161">yok</span><span class="sxs-lookup"><span data-stu-id="21195-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="21195-162">yok</span><span class="sxs-lookup"><span data-stu-id="21195-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="21195-163">yok</span><span class="sxs-lookup"><span data-stu-id="21195-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="21195-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="21195-164">DataGridViewRow</span></span>  
 <span data-ttu-id="21195-165"><xref:System.Windows.Forms.DataGridViewRow> Sınıfı görüntüler bir kaydın veri alanları verileri depolamak istediğiniz <xref:System.Windows.Forms.DataGridView> denetimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="21195-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="21195-166">Erişebildiğiniz <xref:System.Windows.Forms.DataGridView> kullanarak denetiminin satırları <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21195-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="21195-167">Seçili satırları kullanarak erişebileceğiniz <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21195-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="21195-168">Aşağıdaki nesne modeli bu kullanımı gösterir ve gösterir <xref:System.Windows.Forms.DataGridViewRow> Devralma Hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="21195-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="21195-169">![DataGridViewRow nesne modeli](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="21195-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="21195-170">DataGridViewRow nesne modeli</span><span class="sxs-lookup"><span data-stu-id="21195-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="21195-171">Kendi türlerinden türetebilirsiniz <xref:System.Windows.Forms.DataGridViewRow> sınıfı, ancak bu genellikle gerekli olmaz.</span><span class="sxs-lookup"><span data-stu-id="21195-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="21195-172"><xref:System.Windows.Forms.DataGridView> Denetim sahip birkaç satır ile ilgili olayları ve özelliklerini davranışını özelleştirmek için kendi <xref:System.Windows.Forms.DataGridViewRow> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="21195-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="21195-173">Etkinleştirirseniz <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, yeni satır eklemek için özel bir satır son satırı görünür.</span><span class="sxs-lookup"><span data-stu-id="21195-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="21195-174">Bu satırı parçasıdır <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu, ancak ilgilenmenizi gerektiren özel işlevler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="21195-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="21195-175">Daha fazla bilgi için [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="21195-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21195-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21195-176">See also</span></span>
- [<span data-ttu-id="21195-177">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="21195-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="21195-178">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="21195-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="21195-179">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="21195-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
