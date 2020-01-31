---
title: Tasarımcı kullanarak DataGridView Denetimindeki sütunların sırasını değiştirme
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: be4f67ca6530b74fc90cb50a10463b2378edb933
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743150"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="1fb70-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1fb70-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="1fb70-103">Bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimini bir veri kaynağına bağladığınızda, otomatik olarak oluşturulan sütunların görüntüleme sırası veri kaynağı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1fb70-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="1fb70-104">Bu sıra tercih ettiğiniz değilse, Tasarımcıyı kullanarak sütunların sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb70-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="1fb70-105">Ayrıca denetime ilişkisiz sütunlar eklemek ve görüntüleme sıralarını değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fb70-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="1fb70-106">Sütun sırasını programlama yoluyla değiştirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki sütunların sırasını değiştirme](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1fb70-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="1fb70-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1fb70-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1fb70-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1fb70-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="1fb70-109">Tasarımcı kullanarak sütun sırasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1fb70-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="1fb70-110"><xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1fb70-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="1fb70-111">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="1fb70-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="1fb70-112">Seçili sütun istediğiniz konumda olana kadar **Seçili sütunlar** listesinin sağ tarafındaki yukarı veya aşağı oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1fb70-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fb70-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fb70-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="1fb70-114">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="1fb70-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="1fb70-115">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1fb70-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="1fb70-116">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="1fb70-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
