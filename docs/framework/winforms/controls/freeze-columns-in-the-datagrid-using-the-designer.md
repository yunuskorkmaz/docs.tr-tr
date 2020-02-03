---
title: Tasarımcıyı kullanarak DataGridView Denetimindeki sütunları dondurma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: af8e07d7b1b0524e33688fd9d879818aa13be041
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745674"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="8bd63-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="8bd63-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="8bd63-103">Kullanıcılar bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görüntülendiklerinde verileri görüntülerken bazen tek bir sütuna veya sütun kümesine sıklıkla başvurmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bd63-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="8bd63-104">Örneğin, çok sayıda sütun içeren bir müşteri bilgileri tablosu görüntülediğinizde, diğer sütunların görünür bölgenin dışına kaymasını sağlayan müşteri adını her zaman görüntülemesi yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="8bd63-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>

 <span data-ttu-id="8bd63-105">Bu davranışı başarmak için denetimdeki sütunları dondurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd63-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="8bd63-106">Bir sütunu dondurduktan sonra, sol tarafında (veya sağdan sola dil betiklerine ait olan) tüm sütunlar da dondurulur.</span><span class="sxs-lookup"><span data-stu-id="8bd63-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="8bd63-107">Dondurulmuş sütunlar, diğer tüm sütunlar kaydırılarken yerinde kalır.</span><span class="sxs-lookup"><span data-stu-id="8bd63-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="8bd63-108">Sütun yeniden sıralama etkinse, Dondurulmuş sütunlar dondurulmamış sütunlardan farklı bir grup olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8bd63-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="8bd63-109">Kullanıcılar her iki gruptaki sütunları yeniden konumlandırabilirsiniz, ancak bir sütunu bir gruptan diğerine taşıyamaz.</span><span class="sxs-lookup"><span data-stu-id="8bd63-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>

 <span data-ttu-id="8bd63-110">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8bd63-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8bd63-111">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8bd63-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="8bd63-112">Tasarımcıyı kullanarak bir sütunu dondurmak için</span><span class="sxs-lookup"><span data-stu-id="8bd63-112">To freeze a column using the designer</span></span>

1. <span data-ttu-id="8bd63-113"><xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd63-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="8bd63-114">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="8bd63-114">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="8bd63-115">**Sütun özellikleri** kılavuzunda <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8bd63-115">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8bd63-116">Ayrıca **sütun Ekle** Iletişim kutusunda **dondurulmuş** kutuyu seçerek sütunu eklerken dondurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd63-116">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd63-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd63-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8bd63-118">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="8bd63-118">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="8bd63-119">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimindeki Sütun Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8bd63-119">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- <span data-ttu-id="8bd63-120">[Nasıl yapılır: Genelleştirme için Windows Forms içinde sağdan sola metin görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bd63-120">[How to: Display Right-to-Left Text in Windows Forms for Globalization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))</span></span>
- [<span data-ttu-id="8bd63-121">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bd63-121">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="8bd63-122">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="8bd63-122">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
