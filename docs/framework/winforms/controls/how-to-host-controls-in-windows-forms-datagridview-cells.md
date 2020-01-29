---
title: DataGridView hücrelerinde konak denetimleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736531"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="62b96-102">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="62b96-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="62b96-103"><xref:System.Windows.Forms.DataGridView> denetimi, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="62b96-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="62b96-104">Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62b96-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="62b96-105">Bunu yapmak için, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>türetilen sınıfları tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62b96-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="62b96-106">Ayrıca, <xref:System.Windows.Forms.Control> türetilen ve <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimini uygulayan bir sınıf tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62b96-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="62b96-107">Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="62b96-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="62b96-108">Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="62b96-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="62b96-109">Metin kutusu görüntüleme işlevini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıfı, <xref:System.Windows.Forms.DataGridViewCell> sınıfını doğrudan devralmak yerine <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="62b96-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62b96-110"><xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> türettiğinizde ve türetilmiş sınıfa yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemini geçersiz kıldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="62b96-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="62b96-111">Temel sınıfın özelliklerinin yeni hücreye veya sütuna kopyalanabilmesi için temel sınıfın `Clone` yöntemini de çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="62b96-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b96-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b96-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62b96-113">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="62b96-113">Compiling the Code</span></span>  
 <span data-ttu-id="62b96-114">Aşağıdaki örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="62b96-114">The following example requires:</span></span>  
  
- <span data-ttu-id="62b96-115">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="62b96-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b96-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62b96-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="62b96-117">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="62b96-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="62b96-118">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="62b96-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="62b96-119">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="62b96-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
