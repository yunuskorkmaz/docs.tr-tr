---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Salt Okunur Yapma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952099"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="8b8f8-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütunları Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="8b8f8-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="8b8f8-103">Varsayılan olarak, kullanıcılar Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görünen metin ve sayısal verileri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8b8f8-104">Değişiklik için amaçlanmış verileri göstermek istiyorsanız, verileri içeren sütunları salt okunurdur yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="8b8f8-105">Denetimi tamamen salt okuma yapma hakkında bilgi için bkz [. nasıl yapılır: Tasarımcı](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi önleyin.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="8b8f8-106">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8b8f8-107">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="8b8f8-108">Tasarımcıyı kullanarak bir sütunu salt okunabilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8b8f8-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="8b8f8-109"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="8b8f8-110">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="8b8f8-111">**Sütun özellikleri** kılavuzunda, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b8f8-112">Sütun **Ekle** iletişim kutusundaki salt **Oku** onay kutusunu seçerek de bir sütunu salt okunabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b8f8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b8f8-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b8f8-114">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="8b8f8-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="8b8f8-115">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme</span><span class="sxs-lookup"><span data-stu-id="8b8f8-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="8b8f8-116">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b8f8-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="8b8f8-117">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="8b8f8-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
