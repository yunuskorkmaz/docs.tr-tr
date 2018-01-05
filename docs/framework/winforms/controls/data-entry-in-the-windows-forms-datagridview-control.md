---
title: "Windows Forms DataGridView Denetimindeki Veri Girişi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399520738c53e149e7a5539a62a5d4599e26a8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1d899-102">Windows Forms DataGridView Denetimindeki Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="1d899-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1d899-103">`DataGridView` Denetimi nasıl kullanıcılar ekleme veya denetiminde verileri değiştirme değiştirmek olanak sağlayan birçok özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d899-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="1d899-104">Örneğin, veri girişi daha verimli yeni satırlar için varsayılan değerleri sağlayarak ve hata oluştuğunda kullanıcıların uyarı tarafından yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d899-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d899-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1d899-105">In This Section</span></span>  
 [<span data-ttu-id="1d899-106">Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="1d899-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1d899-107">Hücre düzenleme kullanıcıların başlangıç biçiminin nasıl değiştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1d899-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="1d899-108">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="1d899-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="1d899-109">Veri girişi zaman kazanmak yeni kayıtlar için satır önceden doldurmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d899-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="1d899-110">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="1d899-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1d899-111">Gizlemeden, görünümünü özelleştirme ve nasıl için ilgili bilgiler dahil olmak üzere ayrıntılı yeni kayıtlar için satır açıklar <xref:System.Windows.Forms.DataGridView.Rows%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1d899-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="1d899-112">İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="1d899-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1d899-113">Veri girişini biçimlendirme hataları önlemek için kullanıcı girişi doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d899-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="1d899-114">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="1d899-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="1d899-115">Kullanıcı yeni bir değer tamamlama girişiminde bulunduğunda, veri kaynağından kaynaklanan veri girişi sırasında oluşan hataları nasıl ele alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d899-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1d899-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1d899-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="1d899-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="1d899-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="1d899-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.EditMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1d899-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="1d899-119">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.</span><span class="sxs-lookup"><span data-stu-id="1d899-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="1d899-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.DataError> olay.</span><span class="sxs-lookup"><span data-stu-id="1d899-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="1d899-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.CellValidating> olay.</span><span class="sxs-lookup"><span data-stu-id="1d899-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d899-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1d899-122">Related Sections</span></span>  
 [<span data-ttu-id="1d899-123">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1d899-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1d899-124">El ile veya bir dış veri kaynağından veri denetimiyle doldurmak nasıl açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d899-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d899-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d899-125">See Also</span></span>  
 [<span data-ttu-id="1d899-126">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="1d899-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="1d899-127">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="1d899-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
