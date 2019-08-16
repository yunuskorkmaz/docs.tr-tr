---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: d88d658b31c87e7ae89bfb4a11fe794bfbb0e848
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040104"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="dfdb1-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="dfdb1-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="dfdb1-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetim, verileri göstermek için sütun içermelidir.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="dfdb1-104">Denetimi el ile doldurmayı planlıyorsanız sütunları kendiniz eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="dfdb1-105">Alternatif olarak, denetimi bir veri kaynağına bağlayabilir ve sütunları otomatik olarak oluşturur ve doldurur.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="dfdb1-106">Veri kaynağı göstermek istediğinizden daha fazla sütun içeriyorsa, istenmeyen sütunları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="dfdb1-107">Aşağıdaki yordamlarda bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="dfdb1-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="dfdb1-109">Tasarımcıyı kullanarak sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="dfdb1-109">To add a column using the designer</span></span>

1. <span data-ttu-id="dfdb1-110"><xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket karakterini (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **sütun Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="dfdb1-111">**Sütun Ekle** iletişim kutusunda, veri kaynağı **sütunu** seçeneğini belirleyin ve veri kaynağından bir sütun seçin ya da **ilişkisiz sütun** seçeneğini belirleyin ve belirtilen alanları kullanarak sütunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="dfdb1-112">Sütunu eklemek için **Ekle** düğmesine tıklayın, var olan sütunlar denetim görüntüleme alanını önceden doldurmadığında tasarımcıda görünmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dfdb1-113">Sütun özelliklerini, denetimin akıllı etiketinden erişebileceğiniz **Sütunları Düzenle** iletişim kutusunda değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="dfdb1-114">Tasarımcıyı kullanarak bir sütunu kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="dfdb1-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="dfdb1-115">Denetimin akıllı etiketindeki **Sütunları Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="dfdb1-116">**Seçili sütunlar** listesinden bir sütun seçin.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="dfdb1-117">Sütunu silmek için **Kaldır** düğmesine tıklayın ve tasarımcı 'nın kaybolmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfdb1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfdb1-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="dfdb1-119">Nasıl yapılır: Windows Forms uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dfdb1-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="dfdb1-120">Nasıl yapılır: Windows Forms denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="dfdb1-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
