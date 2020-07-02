---
title: DataGridView hücrelerinde konak denetimleri
description: Kullanıcılarınızın çeşitli yollarla değer girmesini ve düzenlemesini sağlamak için Windows Forms DataGridView hücrelerinde denetimlerin nasıl barındıralınacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619552"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="43fd0-103">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="43fd0-103">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="43fd0-104">Bu <xref:System.Windows.Forms.DataGridView> Denetim, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="43fd0-104">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="43fd0-105">Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43fd0-105">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="43fd0-106">Bunu yapmak için, ve ' den türetilen sınıfları tanımlamanız gerekir <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="43fd0-106">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="43fd0-107">Ayrıca arabiriminden türetilen ve uygulayan bir sınıf tanımlamanız gerekir <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.IDataGridViewEditingControl> .</span><span class="sxs-lookup"><span data-stu-id="43fd0-107">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="43fd0-108">Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="43fd0-108">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="43fd0-109">Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> Denetim görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="43fd0-109">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="43fd0-110">Metin kutusu görüntüleme işlevini yeniden uygulamak zorunda kalmamak için sınıf `CalendarCell` <xref:System.Windows.Forms.DataGridViewTextBoxCell> doğrudan sınıfı devralmak yerine sınıftan türetilir <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="43fd0-110">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43fd0-111">Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi geçersiz kıldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="43fd0-111">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="43fd0-112">Ayrıca temel sınıfın `Clone` özelliklerini yeni hücreye veya sütuna kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43fd0-112">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43fd0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="43fd0-113">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43fd0-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="43fd0-114">Compiling the Code</span></span>  
 <span data-ttu-id="43fd0-115">Aşağıdaki örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="43fd0-115">The following example requires:</span></span>  
  
- <span data-ttu-id="43fd0-116">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="43fd0-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fd0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43fd0-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="43fd0-118">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="43fd0-118">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43fd0-119">DataGridView Denetim Mimarisi</span><span class="sxs-lookup"><span data-stu-id="43fd0-119">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="43fd0-120">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="43fd0-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
