---
title: Tasarımcıyı DataGridView denetimiyle kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 50e8bddb97c2dfb84cebdbb2ca4d42a6c5743304
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728359"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="6ef44-102">Windows Formları DataGridView Denetimi ile Tasarımcı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6ef44-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6ef44-103">Visual Studio, kod yazmadan birçok Kurulum görevi gerçekleştirmenizi sağlayan `DataGridView` denetimine yönelik tasarımcı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="6ef44-104">Bu görevler, denetimi bir veri kaynağına bağlamayı, verileri göstermek için kullanılan sütunları değiştirmeyi ve denetimin görünümünü ve temel davranışını ayarlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="6ef44-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ef44-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ef44-105">In This Section</span></span>  
 [<span data-ttu-id="6ef44-106">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="6ef44-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-107">Sütunlar koleksiyonunu doldurmak ve değiştirmek için sütun **Ekle** ve **Sütunları Düzenle** iletişim kutularının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="6ef44-108">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="6ef44-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-109">Verilere bağlanmak için denetimin akıllı etiketindeki **veri kaynağı seç** seçeneğinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="6ef44-110">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6ef44-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-111">Sütunları **Düzenle** iletişim kutusunun sütunları yeniden düzenlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="6ef44-112">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Sütununun Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6ef44-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="6ef44-113">Sütun türlerini değiştirmek için **Sütunları Düzenle** iletişim kutusunun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="6ef44-114">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütun Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6ef44-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-115">Kullanıcıların sütunları yeniden düzenlemenizi sağlamak için denetimin akıllı etiketinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="6ef44-116">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="6ef44-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-117">Belirli sütunların kaymasını engellemek için **Sütunları Düzenle** iletişim kutusunun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="6ef44-118">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Gizleme</span><span class="sxs-lookup"><span data-stu-id="6ef44-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-119">**Sütunları Düzenle** iletişim kutusunun belirli sütunları gizlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="6ef44-120">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="6ef44-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-121">Kullanıcıların belirli sütunlardaki değerleri düzenlemesini engellemek için **Sütunları Düzenle** iletişim kutusunun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="6ef44-122">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Satır Eklemeyi ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="6ef44-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-123">Kullanıcıların satır eklemesini ve silmesini engellemek için denetimin akıllı etiketinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="6ef44-124">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6ef44-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="6ef44-125">Denetimde defter benzeri bir görünüm oluşturmak için **CellStyle Builder** iletişim kutusunun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="6ef44-126">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6ef44-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="6ef44-127">Denetimin temel görünümünü ve veri görüntüleme biçimlerini ayarlamak için **CellStyle Builder** iletişim kutusunun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ef44-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6ef44-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="6ef44-129"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ef44-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef44-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ef44-130">See also</span></span>

- [<span data-ttu-id="6ef44-131">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="6ef44-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
