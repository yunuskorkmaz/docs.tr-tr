---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70bf241865eef3366444e1b4dc20c19adaff983e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="68bb2-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="68bb2-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="68bb2-103">Varsayılan olarak, kullanıcılar geçerli içeriğini düzenleyebilir <xref:System.Windows.Forms.DataGridView> metin kutusu hücresinin içine yazarak veya F2 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68bb2-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="68bb2-104">Aşağıdaki koşulların tümü yerine getirilirse bu hücre düzenleme moduna girer:</span><span class="sxs-lookup"><span data-stu-id="68bb2-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="68bb2-105">Veri kaynağındaki düzenlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="68bb2-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="68bb2-106"><xref:System.Windows.Forms.DataGridView> Denetim etkin.</span><span class="sxs-lookup"><span data-stu-id="68bb2-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="68bb2-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri değil <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="68bb2-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="68bb2-108">`ReadOnly` Hücre, satır, sütun ve denetim özellikleridir tüm kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="68bb2-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="68bb2-109">Düzenleme modunda kullanıcı hücrenin değerini değiştirin ve değişikliği veya özgün değeri hücreye geri dönmek için ESC yürütmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68bb2-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="68bb2-110">Yapılandırabileceğiniz bir <xref:System.Windows.Forms.DataGridView> geçerli hücreyi hale hemen bir hücre düzenleme moduna girer. böylece denetim.</span><span class="sxs-lookup"><span data-stu-id="68bb2-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="68bb2-111">ENTER ve ESC anahtarları davranışını bu durumda değiştirilmez, ancak değeri yürütülmeli veya geri sonra hücre düzenleme modunda kalır.</span><span class="sxs-lookup"><span data-stu-id="68bb2-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="68bb2-112">Böylece yalnızca kullanıcı hücrenin veya yalnızca kullanıcıların F2 basın yazarken hücre düzenleme moduna denetimi de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68bb2-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="68bb2-113">Son olarak, çağırdığınızda dışında düzenleme moduna geçmesini hücreleri engel olabilirsiniz <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="68bb2-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="68bb2-114">DataGridView denetiminin düzenleme modunu değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="68bb2-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="68bb2-115">Ayarlama <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğine uygun <xref:System.Windows.Forms.DataGridViewEditMode> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="68bb2-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68bb2-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="68bb2-116">Compiling the Code</span></span>  
 <span data-ttu-id="68bb2-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="68bb2-117">This example requires:</span></span>  
  
-   <span data-ttu-id="68bb2-118">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="68bb2-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="68bb2-119">Başvurular <xref:System> ve <xref:System.Windows.Forms> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="68bb2-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68bb2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68bb2-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="68bb2-121">Veri girişi Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="68bb2-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
