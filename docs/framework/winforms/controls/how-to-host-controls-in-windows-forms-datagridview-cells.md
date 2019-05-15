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
ms.openlocfilehash: 20b9f33b31df9145205a13b8649153e51d840a6c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592433"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="02908-102">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="02908-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="02908-103"><xref:System.Windows.Forms.DataGridView> Denetim kullanıcılarınızın girin ve çeşitli şekillerde değerlerini düzenlemek birden fazla sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="02908-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="02908-104">Ancak, bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerin ile kendi sütun türleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02908-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="02908-105">Bunu yapmak için türetilen sınıfları tanımlama <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="02908-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="02908-106">Türetilen bir sınıf da tanımlamanız gerekir <xref:System.Windows.Forms.Control> ve uygulayan <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02908-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="02908-107">Aşağıdaki kod örneği, bir takvim sütun oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="02908-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="02908-108">Bu sütunun hücre normal metin kutusu hücrelerindeki, ancak kullanıcı bir hücreye düzenlediğinde tarihleri görüntüleme bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="02908-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="02908-109">Metin kutusunun görüntüleme işlevlerini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıf türetilir <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıf devralma yerine <xref:System.Windows.Forms.DataGridViewCell> doğrudan sınıf.</span><span class="sxs-lookup"><span data-stu-id="02908-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02908-110">Olduğunda, türetilen <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıf için yeni özellikler eklemek için geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02908-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="02908-111">Ayrıca temel sınıfın çağırmalıdır `Clone` yöntemi, böylece yeni hücresinde veya sütununda için temel sınıf özelliklerini kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="02908-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02908-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="02908-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02908-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="02908-113">Compiling the Code</span></span>  
 <span data-ttu-id="02908-114">Aşağıdaki örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="02908-114">The following example requires:</span></span>  
  
- <span data-ttu-id="02908-115">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="02908-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02908-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02908-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="02908-117">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="02908-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="02908-118">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="02908-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="02908-119">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="02908-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
