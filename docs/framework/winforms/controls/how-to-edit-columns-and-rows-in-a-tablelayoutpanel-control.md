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
ms.openlocfilehash: 4473b20eea57088104a51eb1b6c080219223d214
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628650"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="4b34a-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="4b34a-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="4b34a-103">Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, **sütun ve satır stilleri** iletişim kutusu olarak adlandırılan <xref:System.Windows.Forms.TableLayoutPanel> denetimin koleksiyon düzenleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b34a-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="4b34a-104">Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, denetimin `RowSpan` ve `ColumnSpan` özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4b34a-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="4b34a-105">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="4b34a-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="4b34a-106">Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b34a-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="4b34a-107">Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="4b34a-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="4b34a-108">Satırları ve sütunları düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="4b34a-108">To edit rows and columns</span></span>

1. <span data-ttu-id="4b34a-109">**Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4b34a-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="4b34a-110"><xref:System.Windows.Forms.TableLayoutPanel> denetimin tasarımcı eylemleri simgesine (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve **satır ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="4b34a-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="4b34a-111">Ayrıca <xref:System.Windows.Forms.TableLayoutPanel> denetimine sağ tıklayıp, kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b34a-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="4b34a-112">Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="4b34a-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="4b34a-113">Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="4b34a-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="4b34a-114">**Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4b34a-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="4b34a-115">Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4b34a-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="4b34a-116">Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="4b34a-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="4b34a-117">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="4b34a-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="4b34a-118">Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.</span><span class="sxs-lookup"><span data-stu-id="4b34a-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b34a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b34a-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="4b34a-120">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="4b34a-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
