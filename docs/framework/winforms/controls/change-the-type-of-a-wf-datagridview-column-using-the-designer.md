---
title: Tasarımcı kullanarak bir DataGridView sütununun türünü değiştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628624"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="a9422-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a9422-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="a9422-103">Bazen, zaten bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimine eklenmiş olan bir sütunun türünü değiştirmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a9422-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a9422-104">Örneğin, denetimi bir veri kaynağına bağladığınızda otomatik olarak oluşturulan sütunlardan bazılarının türlerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9422-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="a9422-105">Bu, görüntülenen tabloda ilgili tablodaki satırlara yabancı anahtarlar içeren sütunlar olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9422-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="a9422-106">Bu durumda, bu yabancı anahtarları görüntüleyen metin kutusu sütunlarını, ilişkili tablodan daha anlamlı değerler görüntüleyen Birleşik giriş kutusu sütunları ile değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9422-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="a9422-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a9422-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a9422-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a9422-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="a9422-109">Tasarımcıyı kullanarak bir sütunun türünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="a9422-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="a9422-110"><xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesinde bulunan Tasarımcı eylemleri glifinin (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a9422-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="a9422-111">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="a9422-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="a9422-112">**Sütun özellikleri** kılavuzunda `ColumnType` özelliğini yeni sütun türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a9422-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a9422-113">`ColumnType` özelliği, sütun türünü temsil eden sınıfı gösteren bir yalnızca tasarım zamanı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="a9422-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="a9422-114">Bir sütun sınıfında tanımlanan gerçek bir özellik değildir.</span><span class="sxs-lookup"><span data-stu-id="a9422-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9422-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9422-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="a9422-116">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9422-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="a9422-117">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="a9422-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
