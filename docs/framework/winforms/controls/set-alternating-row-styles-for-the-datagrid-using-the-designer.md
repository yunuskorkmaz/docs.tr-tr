---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: a24b4e6af98d2637ecae2352aaa881adcd1c1a45
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666840"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="33b99-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="33b99-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="33b99-103">Tablo verileri genellikle farklı satırlarda arka plan rengine sahip olan bir defter benzeri biçimde sunulur.</span><span class="sxs-lookup"><span data-stu-id="33b99-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="33b99-104">Bu biçim, özellikle çok sayıda sütunu olan geniş tablolar ile, kullanıcıların her satırda hangi hücrelerin olduğunu söylemesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="33b99-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="33b99-105"><xref:System.Windows.Forms.DataGridView> Denetimiyle, alternatif satırlar için tüm stil bilgilerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33b99-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="33b99-106">Alternatif satırları ayırt etmek için arka plan rengine ek olarak, ön plan rengi ve yazı tipi gibi stil özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33b99-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="33b99-107">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="33b99-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="33b99-108">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="33b99-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="33b99-109">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="33b99-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="33b99-110">Değişen satırlar için stiller tanımlayın</span><span class="sxs-lookup"><span data-stu-id="33b99-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="33b99-111"><xref:System.Windows.Forms.DataGridView> Tasarımcıda denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="33b99-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="33b99-112">**Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> yanındaki üç nokta düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) (...) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="33b99-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="33b99-113">**CellStyle Builder** iletişim kutusunda, özellikleri ayarlayarak stili tanımlayın ve Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="33b99-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="33b99-114">Belirttiğiniz stiller, ikinci bir ile başlayan denetimde görüntülenen her bir satır için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33b99-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="33b99-115">Kalan satırların stillerini tanımlamak için <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği kullanarak 2. ve 3. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="33b99-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="33b99-116">Hücreler, birden çok özelliklerden devralınan stiller kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="33b99-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="33b99-117">Stil devralma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="33b99-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33b99-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b99-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="33b99-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="33b99-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="33b99-120">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="33b99-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="33b99-121">Windows Forms DataGridView Denetimi ile Tasarımcı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="33b99-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="33b99-122">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="33b99-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="33b99-123">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="33b99-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
