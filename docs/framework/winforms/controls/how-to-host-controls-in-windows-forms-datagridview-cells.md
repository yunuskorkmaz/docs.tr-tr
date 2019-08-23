---
title: 'Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966602"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="7f2fc-102">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="7f2fc-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="7f2fc-103">Bu <xref:System.Windows.Forms.DataGridView> denetim, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="7f2fc-104">Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="7f2fc-105">Bunu yapmak için, ve ' <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.DataGridViewCell>den türetilen sınıfları tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="7f2fc-106">Ayrıca <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.IDataGridViewEditingControl> arabiriminden türetilen ve uygulayan bir sınıf tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="7f2fc-107">Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="7f2fc-108">Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> denetim görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="7f2fc-109">Metin kutusu görüntüleme işlevini yeniden `CalendarCell` uygulamak zorunda kalmamak için sınıf doğrudan <xref:System.Windows.Forms.DataGridViewCell> sınıfı devralmak yerine <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıftan türetilir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f2fc-110">Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemi geçersiz kıldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="7f2fc-111">Ayrıca temel sınıfın özelliklerini yeni hücreye veya sütuna `Clone` kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f2fc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f2fc-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f2fc-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7f2fc-113">Compiling the Code</span></span>  
 <span data-ttu-id="7f2fc-114">Aşağıdaki örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7f2fc-114">The following example requires:</span></span>  
  
- <span data-ttu-id="7f2fc-115">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2fc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f2fc-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="7f2fc-117">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7f2fc-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7f2fc-118">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="7f2fc-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="7f2fc-119">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="7f2fc-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
