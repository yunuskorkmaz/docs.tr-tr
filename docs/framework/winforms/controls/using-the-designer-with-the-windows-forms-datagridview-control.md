---
title: "Windows Formları DataGridView Denetimi ile Tasarımcı Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b29904954a593607a7872c0b59265bbf241dce98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="8b70b-102">Windows Formları DataGridView Denetimi ile Tasarımcı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="8b70b-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8b70b-103">Visual Studio için tasarımcı desteği sağlar `DataGridView` denetimi, kod yazmadan birçok kurulum görevleri gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b70b-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="8b70b-104">Bu görevler verileri görüntülemek için kullanılan denetim sütunları değiştirmek, bir veri kaynağına bağlama ve denetiminin temel davranış ve görünümünü ayarlama içerir.</span><span class="sxs-lookup"><span data-stu-id="8b70b-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b70b-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b70b-105">In This Section</span></span>  
 [<span data-ttu-id="8b70b-106">Nasıl yapılır: ekleme ve kaldırma sütunları Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-107">Nasıl kullanılacağını açıklar **Sütun Ekle** ve **Edit Columns** doldurmak ve sütunları koleksiyonunu Değiştir iletişim kutuları.</span><span class="sxs-lookup"><span data-stu-id="8b70b-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="8b70b-108">Nasıl yapılır: veri bağlama Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-109">Nasıl kullanılacağını açıklar **veri kaynağı Seç** veri bağlanmak için denetimin akıllı etiket seçeneği.</span><span class="sxs-lookup"><span data-stu-id="8b70b-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="8b70b-110">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetimi sütunların sırasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="8b70b-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-111">Nasıl kullanılacağını açıklar **Edit Columns** sütunları yeniden sıralamak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="8b70b-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="8b70b-112">Nasıl yapılır: Tasarımcı kullanarak Windows Formları DataGridView sütununun türünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="8b70b-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="8b70b-113">Nasıl kullanılacağını açıklar **Edit Columns** sütun türleri değiştirme iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="8b70b-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="8b70b-114">Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetiminde sütun yeniden sıralamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8b70b-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-115">Denetimin akıllı etiket sütunları yeniden sıralamak kullanıcıların sağlamak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b70b-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="8b70b-116">Nasıl yapılır: sütunları dondurma Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-117">Nasıl kullanılacağını açıklar **Edit Columns** belirli sütunlardaki kaymasını engellemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="8b70b-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="8b70b-118">Nasıl yapılır: Gizle sütunları Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-119">Nasıl kullanılacağını açıklar **Edit Columns** belirli sütunları gizlemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="8b70b-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="8b70b-120">Nasıl yapılır: yapma sütunları salt okunur Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-121">Nasıl kullanılacağını açıklar **Edit Columns** iletişim kutusunu kullanıcıların düzenlemesini önlemek için belirli sütunlardaki değerleri.</span><span class="sxs-lookup"><span data-stu-id="8b70b-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="8b70b-122">Nasıl yapılır: satır ekleme ve engelleme silme Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b70b-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-123">Denetimin akıllı etiket eklemek veya satırları silme kullanıcıların önlemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b70b-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="8b70b-124">Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="8b70b-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="8b70b-125">Nasıl kullanılacağını açıklar **CellStyle Oluşturucu** denetiminde defter benzeri bir görünüm oluşturmak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="8b70b-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="8b70b-126">Nasıl yapılır: varsayılan hücre stilleri ve veri biçimleri DataGridView Tasarımcı kullanarak Windows Formları denetimi için ayarlama</span><span class="sxs-lookup"><span data-stu-id="8b70b-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="8b70b-127">Nasıl kullanılacağını açıklar **CellStyle Oluşturucu** temel görünümü ve veri görüntü ayarlama için iletişim kutusu için Denetim biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="8b70b-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8b70b-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8b70b-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8b70b-129">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8b70b-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b70b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b70b-130">See Also</span></span>  
 [<span data-ttu-id="8b70b-131">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="8b70b-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
