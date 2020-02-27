---
title: Tasarımcıyı kullanarak DataGridView Denetimindeki sütunları gizleme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: c5344e10a69d86b1733f5462f9c2df0f0e71b8d5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628845"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="5e282-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Gizleme</span><span class="sxs-lookup"><span data-stu-id="5e282-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="5e282-103">Bazen, bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde kullanılabilir olan sütunlardan yalnızca bazılarını göstermek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5e282-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5e282-104">Örneğin, yönetim kimlik bilgilerine sahip kullanıcılara bir çalışan maaş sütununu diğer kullanıcılardan gizleyerek göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e282-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="5e282-105">Alternatif olarak, denetimi çok sayıda sütun içeren bir veri kaynağına bağlamak isteyebilirsiniz, yalnızca bir kısmı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5e282-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="5e282-106">Bu durumda, genellikle bu sütunları gizlemek yerine, görüntüleme konusunda İlgilendiğiniz sütunları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="5e282-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="5e282-107">Daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5e282-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="5e282-108">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e282-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5e282-109">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5e282-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="5e282-110">Tasarımcıyı kullanarak bir sütunu gizlemek için</span><span class="sxs-lookup"><span data-stu-id="5e282-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="5e282-111"><xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesinde bulunan Tasarımcı eylemleri glifinin (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5e282-111">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="5e282-112">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="5e282-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="5e282-113">**Sütun özellikleri** kılavuzunda <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5e282-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5e282-114">**Sütun Ekle** Iletişim kutusundaki **görünür** onay kutusunu temizleyerek bir sütunu eklerken de gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e282-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e282-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e282-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5e282-116">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="5e282-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="5e282-117">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e282-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="5e282-118">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="5e282-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
