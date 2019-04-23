---
title: Windows Forms DataGridView Denetimindeki Veri Girişi
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
ms.openlocfilehash: 3ebfcaaf22ca632e5784dc1f01a351583e78e865
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090712"
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7c91-102">Windows Forms DataGridView Denetimindeki Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="c7c91-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7c91-103">`DataGridView` Denetimi nasıl kullanıcıları ekleyin veya denetiminde verileri değiştirme değiştirme olanak veren çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="c7c91-104">Örneğin, veri girişini daha verimli yeni satırlar için varsayılan değerleri sağlayarak ve hatalar ortaya çıktığında kullanıcıları uyarı tarafından yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7c91-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7c91-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c7c91-105">In This Section</span></span>  
 [<span data-ttu-id="c7c91-106">Nasıl yapılır: İçin Windows Forms DataGridView denetiminin düzenleme modunu belirtme</span><span class="sxs-lookup"><span data-stu-id="c7c91-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c7c91-107">Hücre düzenleme kullanıcıların başlangıç şeklini değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="c7c91-108">Nasıl yapılır: Windows Forms DataGridView denetiminde yeni satırlar için varsayılan değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="c7c91-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="c7c91-109">Veri girişi zaman kazanmak yeni kayıtlar için satır önceden açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="c7c91-110">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7c91-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c7c91-111">Ayrıntılı bilgiler gizleyerek, görünümünü özelleştirme ve onu ilişkisini dahil olmak üzere, yeni kayıtlar için satır açıklar <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c7c91-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="c7c91-112">İzlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="c7c91-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c7c91-113">Veri girişi biçimlendirme hataları önlemek için kullanıcı girişini doğrulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="c7c91-114">İzlenecek yol: Windows Forms DataGridView denetimine veri girişi sırasında oluşan hataları ele alma</span><span class="sxs-lookup"><span data-stu-id="c7c91-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="c7c91-115">Kullanıcı yeni bir değer kaydetmeye çalıştığında, veri kaynağından kaynaklanan veri girişi sırasında oluşan hataları nasıl ele alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7c91-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c7c91-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c7c91-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c7c91-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c7c91-118">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.EditMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7c91-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="c7c91-119">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.</span><span class="sxs-lookup"><span data-stu-id="c7c91-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="c7c91-120">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.DataError> olay.</span><span class="sxs-lookup"><span data-stu-id="c7c91-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="c7c91-121">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.CellValidating> olay.</span><span class="sxs-lookup"><span data-stu-id="c7c91-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7c91-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c7c91-122">Related Sections</span></span>  
 [<span data-ttu-id="c7c91-123">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7c91-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c7c91-124">El ile veya bir dış veri kaynağından denetimi veriyle doldurmak nasıl açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7c91-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c91-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7c91-125">See also</span></span>

- [<span data-ttu-id="c7c91-126">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c7c91-126">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="c7c91-127">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="c7c91-127">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
