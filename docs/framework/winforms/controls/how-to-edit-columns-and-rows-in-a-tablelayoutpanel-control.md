---
title: "Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84dbcfcbad30f9ef08548874c5e68ed658aa0914
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="1008d-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1008d-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="1008d-103">Koleksiyon Düzenleyicisi kullanımını <xref:System.Windows.Forms.TableLayoutPanel> adlı Denetim **sütun ve satır stilleri** iletişim kutusu, satırları ve sütunları, denetimlerinizin düzenlemek için.</span><span class="sxs-lookup"><span data-stu-id="1008d-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1008d-104">Birden çok satır veya sütun yayılan bir denetim istiyorsanız ayarlayın `RowSpan` ve `ColumnSpan` denetimi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1008d-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="1008d-105">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="1008d-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="1008d-106">Hücre içindeki bir denetimi hizalama istiyorsanız veya içinde bir hücre uzatmak için bir denetim istiyorsanız, denetimin kullanmak <xref:System.Windows.Forms.Control.Anchor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1008d-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="1008d-107">Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="1008d-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="1008d-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1008d-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1008d-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1008d-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1008d-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1008d-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="1008d-111">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="1008d-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="1008d-112">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="1008d-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="1008d-113">Tıklatın <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **Düzenle satırları ve sütunları** açmak için  **Sütun ve satır stilleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="1008d-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="1008d-114">Ayrıca sağ tıklayarak <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve seçin **Düzenle satırları ve sütunları** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="1008d-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="1008d-115">Sütun eklemek veya kaldırmak için seçin **sütunları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="1008d-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="1008d-116">Satır eklediğinizde veya kaldırdığınızda için seçin **satırları** gelen **üye türü** aşağı açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="1008d-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="1008d-117">Tıklatın **Ekle** sonuna satır veya sütun eklemek için düğmeyi **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="1008d-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="1008d-118">Tıklatın **Ekle** bir satır veya sütun seçili öğenin önce listesine eklemek için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1008d-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="1008d-119">Bir satır veya sütun ekliyorsanız seçin **boyutu türü** yeni satır veya sütun.</span><span class="sxs-lookup"><span data-stu-id="1008d-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="1008d-120">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="1008d-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="1008d-121">Bir satır veya sütun kaldırmak için tıklatın **kaldırmak** şu anda seçilen öğeyi silmek için düğmesini **üye** listesi.</span><span class="sxs-lookup"><span data-stu-id="1008d-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1008d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1008d-122">See Also</span></span>  
 <xref:System.Windows.Forms.SizeType>  
 [<span data-ttu-id="1008d-123">TableLayoutPanel denetimi</span><span class="sxs-lookup"><span data-stu-id="1008d-123">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
