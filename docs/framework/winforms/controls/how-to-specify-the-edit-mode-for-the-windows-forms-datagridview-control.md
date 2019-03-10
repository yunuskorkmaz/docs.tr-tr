---
title: 'Nasıl yapılır: İçin Windows Forms DataGridView denetiminin düzenleme modunu belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 00c5bb85eb1b238371e58a631d90b69a41c49140
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725318"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="62f4c-102">Nasıl yapılır: İçin Windows Forms DataGridView denetiminin düzenleme modunu belirtme</span><span class="sxs-lookup"><span data-stu-id="62f4c-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="62f4c-103">Varsayılan olarak, kullanıcılar geçerli içeriğini düzenleyebilir <xref:System.Windows.Forms.DataGridView> yazmak ya da F2 tuşuna basarak metin kutusu hücre.</span><span class="sxs-lookup"><span data-stu-id="62f4c-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="62f4c-104">Tüm aşağıdaki koşullardan biri karşılanırsa bu hücre düzenleme moduna girer:</span><span class="sxs-lookup"><span data-stu-id="62f4c-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="62f4c-105">Temel alınan veri kaynağına düzenlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="62f4c-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="62f4c-106"><xref:System.Windows.Forms.DataGridView> Denetimi etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="62f4c-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="62f4c-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri değil <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="62f4c-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="62f4c-108">`ReadOnly` Hücre, satır, sütun ve denetim özellikleri olan tüm kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="62f4c-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="62f4c-109">Kullanıcı düzenleme modunda hücre değerini değiştirin ve değişikliği veya özgün değerine hücreye dönmek için ESC kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="62f4c-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="62f4c-110">Yapılandırabileceğiniz bir <xref:System.Windows.Forms.DataGridView> böylece geçerli hücreyi duruma geldiğinde bir hücre düzenleme moduna girer.</span><span class="sxs-lookup"><span data-stu-id="62f4c-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="62f4c-111">Bu durumda ENTER ve ESC anahtarları davranışını değiştirilmez, ancak değeri kaydedilmiş veya geri sonra hücre düzenleme modunda kalır.</span><span class="sxs-lookup"><span data-stu-id="62f4c-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="62f4c-112">Yalnızca kullanıcılar hücre veya yalnızca, kullanıcılar F2 tuşuna yazarken hücre düzenleme moduna girin. böylece, denetimi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62f4c-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="62f4c-113">Son olarak, çağırdığınızda dışında düzenleme moduna geçmesini hücreleri engelleyebilir miyim <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62f4c-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="62f4c-114">DataGridView denetiminin düzenleme modunu değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="62f4c-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="62f4c-115">Ayarlama <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğini uygun <xref:System.Windows.Forms.DataGridViewEditMode> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="62f4c-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62f4c-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="62f4c-116">Compiling the Code</span></span>  
 <span data-ttu-id="62f4c-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="62f4c-117">This example requires:</span></span>  
  
-   <span data-ttu-id="62f4c-118">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="62f4c-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="62f4c-119">Başvurular <xref:System> ve <xref:System.Windows.Forms> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="62f4c-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f4c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f4c-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="62f4c-121">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="62f4c-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
