---
title: DataGridView denetimi için düzenleme modunu belirtin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743769"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="f1775-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="f1775-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f1775-103">Varsayılan olarak, kullanıcılar geçerli <xref:System.Windows.Forms.DataGridView> metin kutusu hücresinin içeriğini yazarak veya F2 tuşuna basarak düzenleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="f1775-104">Bu, aşağıdaki koşulların tümü karşılanıyorsa hücreyi düzenleme moduna geçirir:</span><span class="sxs-lookup"><span data-stu-id="f1775-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="f1775-105">Temel alınan veri kaynağı, düzenlemesini destekler.</span><span class="sxs-lookup"><span data-stu-id="f1775-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="f1775-106"><xref:System.Windows.Forms.DataGridView> denetimi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="f1775-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>değil.</span><span class="sxs-lookup"><span data-stu-id="f1775-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="f1775-108">Hücrenin, satırın, sütunun ve denetimin `ReadOnly` özellikleri `false`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f1775-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="f1775-109">Düzenleme modunda, Kullanıcı hücre değerini değiştirebilir ve değişikliği kaydetmek için ENTER tuşuna basarak hücreyi özgün değerine döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="f1775-110">Bir <xref:System.Windows.Forms.DataGridView> denetimini, bir hücrenin geçerli hücreye dönüşen kısa sürede düzenleme moduna girmesi için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="f1775-111">Bu durumda ENTER ve ESC tuşlarının davranışı değiştirilmez, ancak değer kaydedildikten veya geri döndürüldüğünden hücre düzenleme modunda kalır.</span><span class="sxs-lookup"><span data-stu-id="f1775-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="f1775-112">Ayrıca, denetimin yalnızca kullanıcılar hücreye yazmaları veya Kullanıcı F2 'ye basması durumunda düzenleme moduna girmesi için denetimi de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="f1775-113">Son olarak, <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemini çağırdığınızda hücrelerin düzenleme moduna girmesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="f1775-114">DataGridView denetiminin düzenleme modunu değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f1775-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="f1775-115"><xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğini uygun <xref:System.Windows.Forms.DataGridViewEditMode> sabit listesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f1775-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1775-116">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="f1775-116">Compiling the Code</span></span>  
 <span data-ttu-id="f1775-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f1775-117">This example requires:</span></span>  
  
- <span data-ttu-id="f1775-118">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="f1775-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f1775-119"><xref:System> ve <xref:System.Windows.Forms> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f1775-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1775-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1775-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f1775-121">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="f1775-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
