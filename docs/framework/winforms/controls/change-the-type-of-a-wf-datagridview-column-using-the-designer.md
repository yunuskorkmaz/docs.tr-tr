---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Sütununun Türünü Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f40ab6fe000f9104b10d5841f52eadf102a91a6b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040477"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="cb771-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Sütununun Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="cb771-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="cb771-103">Bazen Windows Forms <xref:System.Windows.Forms.DataGridView> denetimine eklenmiş bir sütunun türünü değiştirmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cb771-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="cb771-104">Örneğin, denetimi bir veri kaynağına bağladığınızda otomatik olarak oluşturulan sütunlardan bazılarının türlerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb771-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="cb771-105">Bu, görüntülenen tabloda ilgili tablodaki satırlara yabancı anahtarlar içeren sütunlar olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb771-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="cb771-106">Bu durumda, bu yabancı anahtarları görüntüleyen metin kutusu sütunlarını, ilişkili tablodan daha anlamlı değerler görüntüleyen Birleşik giriş kutusu sütunları ile değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb771-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="cb771-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb771-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="cb771-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb771-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="cb771-109">Tasarımcıyı kullanarak bir sütunun türünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="cb771-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="cb771-110"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cb771-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="cb771-111">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="cb771-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="cb771-112">**Sütun özellikleri** kılavuzunda, `ColumnType` özelliği yeni sütun türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cb771-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cb771-113">`ColumnType` Özelliği, sütun türünü temsil eden sınıfı gösteren bir yalnızca tasarım zamanı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="cb771-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="cb771-114">Bir sütun sınıfında tanımlanan gerçek bir özellik değildir.</span><span class="sxs-lookup"><span data-stu-id="cb771-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb771-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb771-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="cb771-116">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb771-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="cb771-117">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="cb771-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
