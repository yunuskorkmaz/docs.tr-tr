---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343291"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="d5ad8-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5ad8-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="d5ad8-103">Windows Forms <xref:System.Windows.Forms.DataGridView> denetim verilerini görüntülemek için sütunları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="d5ad8-104">Bir denetimi el ile doldurmak planlıyorsanız, kendiniz sütunlar eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="d5ad8-105">Alternatif olarak, denetimi oluşturur ve sütunları otomatik olarak dolduran bir veri kaynağına da bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="d5ad8-106">Veri kaynağı görüntülemek istediğiniz birden fazla sütun içeriyorsa, istenmeyen sütunları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="d5ad8-107">Aşağıdaki yordamlar gerektiren bir **Windows uygulama** proje içeren bir form ile bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d5ad8-108">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d5ad8-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5ad8-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d5ad8-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d5ad8-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d5ad8-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="d5ad8-112">Tasarımcı kullanarak bir sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="d5ad8-112">To add a column using the designer</span></span>  
  
1. <span data-ttu-id="d5ad8-113">Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Sütun Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2. <span data-ttu-id="d5ad8-114">İçinde **Sütun Ekle** iletişim kutusunda **sınırlama sütunu** seçeneği ve veri kaynağından bir sütun seçin ya da seçin **bağlantısız sütun** seçenek ve sütun tanımlama Belirtilen alanlara kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3. <span data-ttu-id="d5ad8-115">Tıklayın **Ekle** düğmesini Tasarımcısı'nda mevcut sütunları denetimi görüntüleme alanı zaten doldurmuyorsa görünmesine neden olan bir sütun ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5ad8-116">Sütun özellikleri değiştirebilirsiniz **sütunları Düzenle** denetimin akıllı etiketten erişebileceğiniz iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="d5ad8-117">Tasarımcı kullanarak bir sütunu kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="d5ad8-117">To remove a column using the designer</span></span>  
  
1. <span data-ttu-id="d5ad8-118">Seçin **sütunları Düzenle** denetimin akıllı etiketinde.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2. <span data-ttu-id="d5ad8-119">Bir sütun seçin **seçili sütun** listesi.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-119">Select a column from the **Selected Columns** list.</span></span>  
  
3. <span data-ttu-id="d5ad8-120">Tıklayın **Kaldır** bu Tasarımcısından kaybolmasına neden sütununu Sil düğmesini.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ad8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d5ad8-122">Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5ad8-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="d5ad8-123">Nasıl yapılır: Windows Forms’a Denetimler Ekleme</span><span class="sxs-lookup"><span data-stu-id="d5ad8-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
