---
title: DataGridView Denetimi Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742532"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="bae66-102">DataGridView Denetimi Mimarisi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bae66-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="bae66-103"><xref:System.Windows.Forms.DataGridView> denetimi ve ilgili sınıfları tablo verilerini görüntülemek ve görüntülemek için esnek, genişletilebilir bir sistem olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bae66-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="bae66-104">Bu sınıfların hepsi <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanında yer alır ve hepsi "DataGridView" ön ekiyle adlandırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bae66-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="bae66-105">Mimari öğeleri</span><span class="sxs-lookup"><span data-stu-id="bae66-105">Architecture Elements</span></span>  
 <span data-ttu-id="bae66-106">Birincil <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları <xref:System.Windows.Forms.DataGridViewElement>türetilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="bae66-107">Aşağıdaki nesne modelinde <xref:System.Windows.Forms.DataGridViewElement> devralma hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![DataGridViewElement nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="bae66-109"><xref:System.Windows.Forms.DataGridViewElement> sınıfı üst <xref:System.Windows.Forms.DataGridView> denetimine bir başvuru sağlar ve <xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırmadaki değerlerin birleşimini temsil eden bir değer tutan bir <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bae66-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="bae66-110">Aşağıdaki bölümlerde <xref:System.Windows.Forms.DataGridView> yardımcı sınıfları daha ayrıntılı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bae66-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="bae66-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="bae66-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="bae66-112"><xref:System.Windows.Forms.DataGridViewElementStates> Numaralandırma aşağıdaki değerleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bae66-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="bae66-113">Bu sabit listesinin değerleri bit düzeyinde mantıksal işleçlerle birleştirilebilir, bu nedenle <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği bir seferde birden fazla durum ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="bae66-114">Örneğin, <xref:System.Windows.Forms.DataGridViewElement> aynı anda <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>ve <xref:System.Windows.Forms.DataGridViewElementStates.Visible>olabilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="bae66-115">Hücreler ve şeritler</span><span class="sxs-lookup"><span data-stu-id="bae66-115">Cells and Bands</span></span>  
 <span data-ttu-id="bae66-116"><xref:System.Windows.Forms.DataGridView> denetimi iki temel nesne türünü kapsar: hücreler ve bantlar.</span><span class="sxs-lookup"><span data-stu-id="bae66-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="bae66-117">Tüm hücreler <xref:System.Windows.Forms.DataGridViewCell> temel sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="bae66-118">İki tür bant, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewRow>, her ikisi de <xref:System.Windows.Forms.DataGridViewBand> temel sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="bae66-119"><xref:System.Windows.Forms.DataGridView> denetimi çeşitli sınıflarla birlikte çalışır, ancak en sık karşılaşılan <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>ve <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="bae66-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="bae66-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="bae66-120">DataGridViewCell</span></span>  
 <span data-ttu-id="bae66-121">Hücre, <xref:System.Windows.Forms.DataGridView>için temel etkileşim birimidir.</span><span class="sxs-lookup"><span data-stu-id="bae66-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="bae66-122">Görüntü hücrelerde ortalanır ve veri girişi genellikle hücreler aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="bae66-123"><xref:System.Windows.Forms.DataGridViewRow> sınıfının <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> koleksiyonunu kullanarak hücrelere erişebilirsiniz ve <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> koleksiyonunu kullanarak seçili hücrelere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="bae66-124">Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewCell> devralma hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![DataGridViewCell nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="bae66-126"><xref:System.Windows.Forms.DataGridViewCell> türü, tüm hücre türlerinin türeten bir soyut temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="bae66-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="bae66-127"><xref:System.Windows.Forms.DataGridViewCell> ve türetilmiş türleri Windows Forms denetimler değildir ancak bazı konak Windows Forms denetimleri.</span><span class="sxs-lookup"><span data-stu-id="bae66-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="bae66-128">Bir hücre tarafından desteklenen tüm Düzenle işlevleri genellikle barındırılan bir denetim tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="bae66-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="bae66-129"><xref:System.Windows.Forms.DataGridViewCell> nesneler, Windows Forms denetimleriyle aynı şekilde kendi görünüm ve boyama özelliklerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="bae66-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="bae66-130">Bunun yerine, <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCell> nesnelerinin görünüşünün sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="bae66-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="bae66-131"><xref:System.Windows.Forms.DataGridView> denetiminin özellikleri ve olayları ile etkileşime girerek hücrelerin görünümünü ve davranışını önemli ölçüde etkileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="bae66-132"><xref:System.Windows.Forms.DataGridView> denetiminin özelliklerinden daha fazla olan özelleştirmeler için özel gereksinimleriniz varsa, <xref:System.Windows.Forms.DataGridViewCell> veya alt sınıflarından türeyen kendi sınıfınızı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="bae66-133">Aşağıdaki listede <xref:System.Windows.Forms.DataGridViewCell>türetilen sınıflar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bae66-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="bae66-134">Özel hücre türlerinizin</span><span class="sxs-lookup"><span data-stu-id="bae66-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="bae66-135">'In</span><span class="sxs-lookup"><span data-stu-id="bae66-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="bae66-136"><xref:System.Windows.Forms.DataGridView> denetimin ekli veri deposunun şeması, <xref:System.Windows.Forms.DataGridView> denetimin sütunlarında ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="bae66-137"><xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonunu kullanarak <xref:System.Windows.Forms.DataGridView> denetiminin sütunlarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="bae66-138">Seçilen sütunlara <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> koleksiyonunu kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="bae66-139">Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewColumn> devralma hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![DataGridViewColumn nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="bae66-141">Bazı anahtar hücresi türleri karşılık gelen sütun türlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bae66-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="bae66-142">Bunlar <xref:System.Windows.Forms.DataGridViewColumn> temel sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="bae66-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="bae66-143">Aşağıdaki listede <xref:System.Windows.Forms.DataGridViewColumn>türetilen sınıflar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bae66-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="bae66-144">Özel sütun türleriniz</span><span class="sxs-lookup"><span data-stu-id="bae66-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="bae66-145">DataGridView Editing denetimleri</span><span class="sxs-lookup"><span data-stu-id="bae66-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="bae66-146">Gelişmiş Düzenle işlevini destekleyen hücreler genellikle Windows Forms denetiminden türetilen bir barındırılan denetim kullanır.</span><span class="sxs-lookup"><span data-stu-id="bae66-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="bae66-147">Bu denetimler <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimini de uygular.</span><span class="sxs-lookup"><span data-stu-id="bae66-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="bae66-148">Aşağıdaki nesne modelinde bu denetimlerin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![DataGridView Editing Control nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="bae66-150">Aşağıdaki düzen denetimleri <xref:System.Windows.Forms.DataGridView> denetimiyle birlikte sağlanır:</span><span class="sxs-lookup"><span data-stu-id="bae66-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="bae66-151">Kendi düzen denetimlerinizi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri barındırma](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="bae66-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="bae66-152">Aşağıdaki tabloda, hücre türleri, sütun türleri ve düzen denetimleri arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="bae66-153">Hücre türü</span><span class="sxs-lookup"><span data-stu-id="bae66-153">Cell type</span></span>|<span data-ttu-id="bae66-154">Barındırılan denetim</span><span class="sxs-lookup"><span data-stu-id="bae66-154">Hosted control</span></span>|<span data-ttu-id="bae66-155">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="bae66-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="bae66-156">yok</span><span class="sxs-lookup"><span data-stu-id="bae66-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="bae66-157">yok</span><span class="sxs-lookup"><span data-stu-id="bae66-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="bae66-158">yok</span><span class="sxs-lookup"><span data-stu-id="bae66-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="bae66-159">yok</span><span class="sxs-lookup"><span data-stu-id="bae66-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="bae66-160">'A</span><span class="sxs-lookup"><span data-stu-id="bae66-160">DataGridViewRow</span></span>  
 <span data-ttu-id="bae66-161"><xref:System.Windows.Forms.DataGridViewRow> sınıfı, <xref:System.Windows.Forms.DataGridView> denetiminin eklendiği veri deposundaki bir kaydın veri alanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bae66-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="bae66-162"><xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunu kullanarak <xref:System.Windows.Forms.DataGridView> denetiminin satırlarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="bae66-163">Seçili satırlara <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> koleksiyonunu kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bae66-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="bae66-164">Aşağıdaki nesne modelinde bu kullanım gösterilmektedir ve <xref:System.Windows.Forms.DataGridViewRow> devralma hiyerarşisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bae66-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![DataGridViewRow nesne modeli hiyerarşisini gösteren diyagram.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="bae66-166"><xref:System.Windows.Forms.DataGridViewRow> sınıfından kendi türlerinizi türetebilirsiniz, ancak bu genellikle gerekli olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="bae66-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="bae66-167"><xref:System.Windows.Forms.DataGridView> denetiminde, <xref:System.Windows.Forms.DataGridViewRow> nesnelerinin davranışını özelleştirmeye yönelik birkaç satırla ilgili olay ve özellik bulunur.</span><span class="sxs-lookup"><span data-stu-id="bae66-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="bae66-168"><xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliğini etkinleştirirseniz, son satır olarak yeni satır eklemek için özel bir satır görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bae66-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="bae66-169">Bu satır <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonunun bir parçasıdır, ancak ilgilenmeniz gereken özel işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bae66-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="bae66-170">Daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki yeni kayıtlar Için satırı kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bae66-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae66-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bae66-171">See also</span></span>

- [<span data-ttu-id="bae66-172">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bae66-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="bae66-173">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bae66-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bae66-174">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="bae66-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
