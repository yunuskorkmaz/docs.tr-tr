---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039628"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="a1e28-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a1e28-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="a1e28-103">Bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimini bir veri kaynağına bağladığınızda, otomatik olarak oluşturulan sütunların görüntüleme sırası veri kaynağı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a1e28-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="a1e28-104">Bu sıra tercih ettiğiniz değilse, Tasarımcıyı kullanarak sütunların sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1e28-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="a1e28-105">Ayrıca denetime ilişkisiz sütunlar eklemek ve görüntüleme sıralarını değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1e28-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="a1e28-106">Sütun sırasını programlı olarak değiştirme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms DataGridView Denetimindeki](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)sütunların sırasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a1e28-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="a1e28-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1e28-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a1e28-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1e28-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="a1e28-109">Tasarımcı kullanarak sütun sırasını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="a1e28-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="a1e28-110"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a1e28-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="a1e28-111">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="a1e28-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="a1e28-112">Seçili sütun istediğiniz konumda olana kadar **Seçili sütunlar** listesinin sağ tarafındaki yukarı veya aşağı oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1e28-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1e28-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e28-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a1e28-114">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="a1e28-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="a1e28-115">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1e28-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="a1e28-116">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="a1e28-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
