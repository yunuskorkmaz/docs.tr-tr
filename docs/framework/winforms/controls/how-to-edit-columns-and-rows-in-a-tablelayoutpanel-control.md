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
ms.openlocfilehash: 820d2f98290650bfaf377bd2d4b863dfb2e6e704
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500790"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c6963-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c6963-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="c6963-103">Koleksiyon Düzenleyicisi kullanabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> adlı Denetim **sütun ve satır stilleri** satırları ve sütunları, denetimlerin Düzenle iletişim kutusunda,.</span><span class="sxs-lookup"><span data-stu-id="c6963-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6963-104">Birden çok satır veya sütuna yayılmasını denetim istiyorsanız ayarlayın `RowSpan` ve `ColumnSpan` denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c6963-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="c6963-105">Daha fazla bilgi için [izlenecek yol: Windows Forms kullanarak TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c6963-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="c6963-106">Bir denetimi hücrede hizalamak istiyorsanız veya bir hücreyi uzatmak için bir denetim istiyorsanız, denetimin kullanın <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6963-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="c6963-107">Daha fazla bilgi için [izlenecek yol: Windows Forms kullanarak TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="c6963-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="c6963-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c6963-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c6963-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c6963-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c6963-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c6963-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="c6963-111">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="c6963-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="c6963-112">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="c6963-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="c6963-113">Tıklayın <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket karakterini (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **satırları ve sütunları Düzenle** açmak için  **Sütun ve satır stilleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="c6963-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="c6963-114">Ayrıca sağ tıklayabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> seçin ve Denetim **satırları ve sütunları Düzenle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="c6963-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="c6963-115">Sütun ekleme veya kaldırma için seçin **sütunları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="c6963-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="c6963-116">Satır eklediğinizde veya kaldırdığınızda için seçin **satırları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="c6963-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="c6963-117">Tıklayın **Ekle** sonuna bir satır veya sütun eklemek için Ekle düğmesine **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="c6963-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="c6963-118">Tıklayın **Ekle** bir satır veya sütun önce geçerli seçilmiş öğe listesine eklemek için düğme.</span><span class="sxs-lookup"><span data-stu-id="c6963-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="c6963-119">Bir satır veya sütun ekliyorsanız seçin **boyut türü** yeni satır veya sütun.</span><span class="sxs-lookup"><span data-stu-id="c6963-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="c6963-120">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="c6963-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="c6963-121">Bir satır veya sütun kaldırmak için tıklayın **Kaldır** seçili öğeyi silmek için düğmeyi **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="c6963-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6963-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6963-122">See Also</span></span>  
 <xref:System.Windows.Forms.SizeType>  
 [<span data-ttu-id="c6963-123">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="c6963-123">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
