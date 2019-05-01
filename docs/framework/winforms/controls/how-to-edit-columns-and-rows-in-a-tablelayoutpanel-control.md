---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941524"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="99486-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="99486-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="99486-103">Koleksiyon Düzenleyicisi kullanabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> adlı Denetim **sütun ve satır stilleri** satırları ve sütunları, denetimlerin Düzenle iletişim kutusunda,.</span><span class="sxs-lookup"><span data-stu-id="99486-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99486-104">Birden çok satır veya sütuna yayılmasını denetim istiyorsanız ayarlayın `RowSpan` ve `ColumnSpan` denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="99486-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="99486-105">Daha fazla bilgi için [izlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="99486-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="99486-106">Bir denetimi hücrede hizalamak istiyorsanız veya bir hücreyi uzatmak için bir denetim istiyorsanız, denetimin kullanın <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="99486-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="99486-107">Daha fazla bilgi için [izlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="99486-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="99486-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="99486-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="99486-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="99486-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="99486-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="99486-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="99486-111">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="99486-111">To edit rows and columns</span></span>  
  
1. <span data-ttu-id="99486-112">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="99486-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="99486-113">Tıklayın <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **satırları ve sütunları Düzenle** açmak için  **Sütun ve satır stilleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="99486-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="99486-114">Ayrıca sağ tıklayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> seçin ve Denetim **satırları ve sütunları Düzenle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="99486-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3. <span data-ttu-id="99486-115">Sütun ekleme veya kaldırma için seçin **sütunları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="99486-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4. <span data-ttu-id="99486-116">Satır eklediğinizde veya kaldırdığınızda için seçin **satırları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="99486-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5. <span data-ttu-id="99486-117">Tıklayın **Ekle** sonuna bir satır veya sütun eklemek için Ekle düğmesine **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="99486-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6. <span data-ttu-id="99486-118">Tıklayın **Ekle** bir satır veya sütun önce geçerli seçilmiş öğe listesine eklemek için düğme.</span><span class="sxs-lookup"><span data-stu-id="99486-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7. <span data-ttu-id="99486-119">Bir satır veya sütun ekliyorsanız seçin **boyut türü** yeni satır veya sütun.</span><span class="sxs-lookup"><span data-stu-id="99486-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="99486-120">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="99486-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8. <span data-ttu-id="99486-121">Bir satır veya sütun kaldırmak için tıklayın **Kaldır** seçili öğeyi silmek için düğmeyi **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="99486-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99486-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99486-122">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="99486-123">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="99486-123">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
