---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme'
description: Windows Forms denetimlerinizin satırlarını ve sütunlarını düzenlemek için sütun ve satır stilleri iletişim kutusunu nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619357"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="ad2a6-103">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="ad2a6-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="ad2a6-104"><xref:System.Windows.Forms.TableLayoutPanel>Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, **sütun ve satır stilleri** iletişim kutusu adlı denetimin koleksiyon düzenleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="ad2a6-105">Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, `RowSpan` `ColumnSpan` Denetim üzerindeki ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="ad2a6-106">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="ad2a6-107">Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="ad2a6-108">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="ad2a6-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="ad2a6-109">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="ad2a6-109">To edit rows and columns</span></span>

1. <span data-ttu-id="ad2a6-110"><xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="ad2a6-111"><xref:System.Windows.Forms.TableLayoutPanel>Denetimin tasarımcı eylemleri glifi ' ne ( ![ küçük siyah ok ](./media/designer-actions-glyph.gif) ) tıklayın ve **sütun ve satır stilleri** iletişim kutusunu açmak için **satırları ve sütunları Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="ad2a6-112">Ayrıca denetime sağ tıklayıp <xref:System.Windows.Forms.TableLayoutPanel> kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="ad2a6-113">Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="ad2a6-114">Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="ad2a6-115">**Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="ad2a6-116">Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="ad2a6-117">Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="ad2a6-118">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="ad2a6-119">Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad2a6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad2a6-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="ad2a6-121">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="ad2a6-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
