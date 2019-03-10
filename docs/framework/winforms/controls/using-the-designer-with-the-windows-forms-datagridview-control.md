---
title: Windows Formları DataGridView Denetimi ile Tasarımcı Kullanımı
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 460dfa7a0bad4e3421ee32695cd57d8072a3cb0d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721950"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="b3fe5-102">Windows Formları DataGridView Denetimi ile Tasarımcı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b3fe5-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b3fe5-103">Visual Studio için tasarımcı desteği sağlar `DataGridView` denetimi, kod yazmaya gerek kalmadan birçok kurulum görevleri gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="b3fe5-104">Bu görevler, verileri görüntülemek için kullanılan denetim sütunlarını değiştirme, bir veri kaynağına bağlama ve temel denetimin davranışını ve görünümünü ayarlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3fe5-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3fe5-105">In This Section</span></span>  
 [<span data-ttu-id="b3fe5-106">Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma</span><span class="sxs-lookup"><span data-stu-id="b3fe5-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-107">Nasıl kullanılacağını açıklar **Sütun Ekle** ve **sütunları Düzenle** iletişim kutularını doldurun ve sütun koleksiyonundaki değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="b3fe5-108">Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="b3fe5-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-109">Nasıl kullanılacağını açıklar **veri kaynağı Seç** verilere bağlanmak için akıllı etiket denetimin seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="b3fe5-110">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunların sırasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b3fe5-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-111">Nasıl kullanılacağını açıklar **sütunları Düzenle** sütunları yeniden sıralamak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="b3fe5-112">Nasıl yapılır: Tasarımcı kullanarak Windows Formları DataGridView sütununun türünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="b3fe5-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="b3fe5-113">Nasıl kullanılacağını açıklar **sütunları Düzenle** sütun türlerini değiştirmek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="b3fe5-114">Nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütun yeniden sıralamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b3fe5-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-115">Sütunları yeniden sıralamak kullanıcıları etkinleştirmek için akıllı etiket denetimin kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="b3fe5-116">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları dondurma</span><span class="sxs-lookup"><span data-stu-id="b3fe5-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-117">Nasıl kullanılacağını açıklar **sütunları Düzenle** kaymasını belirli sütunları engellemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="b3fe5-118">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="b3fe5-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-119">Nasıl kullanılacağını açıklar **sütunları Düzenle** belirli sütunları gizlemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="b3fe5-120">Nasıl yapılır: Salt okunur Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunları olun</span><span class="sxs-lookup"><span data-stu-id="b3fe5-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-121">Nasıl kullanılacağını açıklar **sütunları Düzenle** iletişim kutusu, kullanıcıların düzenlemesini önlemek için belirli sütunlardaki değerleri.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="b3fe5-122">Nasıl yapılır: Satır eklemeyi ve tasarımcı kullanarak Windows Forms DataGridView denetiminde Silmeyi engelle</span><span class="sxs-lookup"><span data-stu-id="b3fe5-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-123">Denetimin akıllı etiket ekleme veya silme satırları kullanıcıların önlemek için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="b3fe5-124">Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="b3fe5-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="b3fe5-125">Nasıl kullanılacağını açıklar **CellStyle Oluşturucu** denetiminde defter benzeri bir görünüm oluşturmak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="b3fe5-126">Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için varsayılan hücre stilleri ve veri biçimleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="b3fe5-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="b3fe5-127">Nasıl kullanılacağını açıklar **CellStyle Oluşturucu** temel görünümünü ve veri görüntü ayarlamak için iletişim kutusu için denetimin biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3fe5-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b3fe5-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b3fe5-129">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fe5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3fe5-130">See also</span></span>
- [<span data-ttu-id="b3fe5-131">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="b3fe5-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
