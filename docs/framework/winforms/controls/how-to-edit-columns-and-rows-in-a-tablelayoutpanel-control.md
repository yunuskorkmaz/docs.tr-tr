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
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040290"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="f0eec-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f0eec-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="f0eec-103">Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, <xref:System.Windows.Forms.TableLayoutPanel> **sütun ve satır stilleri** iletişim kutusu adlı denetimin koleksiyon düzenleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0eec-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="f0eec-104">Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, denetim üzerindeki `RowSpan` ve `ColumnSpan` özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0eec-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="f0eec-105">Daha fazla bilgi için bkz [. İzlenecek yol: TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.</span><span class="sxs-lookup"><span data-stu-id="f0eec-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="f0eec-106">Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0eec-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="f0eec-107">Daha fazla bilgi için bkz [. İzlenecek yol: TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.</span><span class="sxs-lookup"><span data-stu-id="f0eec-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="f0eec-108">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="f0eec-108">To edit rows and columns</span></span>

1. <span data-ttu-id="f0eec-109"><xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f0eec-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="f0eec-110">![](./media/vs-winformsmttagglyph.gif "") Denetimin akıllı etiket glifi ' ne (akıllı etiket karakteri VS_WinFormSmtTagGlyph) tıklayın ve sütun ve satır stilleri iletişim kutusunu açmak için satırları ve sütunları Düzenle ' yi seçin. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="f0eec-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="f0eec-111">Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> denetime sağ tıklayıp kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0eec-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="f0eec-112">Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f0eec-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="f0eec-113">Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f0eec-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="f0eec-114">**Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0eec-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="f0eec-115">Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0eec-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="f0eec-116">Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="f0eec-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="f0eec-117">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="f0eec-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="f0eec-118">Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.</span><span class="sxs-lookup"><span data-stu-id="f0eec-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0eec-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0eec-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="f0eec-120">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="f0eec-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
