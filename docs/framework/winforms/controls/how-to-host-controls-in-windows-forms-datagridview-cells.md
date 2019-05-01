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
ms.openlocfilehash: 008b6da56c3428d0edcc44778b4d3bef1a52c443
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941238"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="56e2e-102">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="56e2e-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="56e2e-103"><xref:System.Windows.Forms.DataGridView> Denetim kullanıcılarınızın girin ve çeşitli şekillerde değerlerini düzenlemek birden fazla sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="56e2e-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="56e2e-104">Ancak, bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerin ile kendi sütun türleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e2e-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="56e2e-105">Bunu yapmak için türetilen sınıfları tanımlama <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="56e2e-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="56e2e-106">Türetilen bir sınıf da tanımlamanız gerekir <xref:System.Windows.Forms.Control> ve uygulayan <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56e2e-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="56e2e-107">Aşağıdaki kod örneği, bir takvim sütun oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56e2e-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="56e2e-108">Bu sütunun hücre normal metin kutusu hücrelerindeki, ancak kullanıcı bir hücreye düzenlediğinde tarihleri görüntüleme bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="56e2e-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="56e2e-109">Metin kutusunun görüntüleme işlevlerini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıf türetilir <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıf devralma yerine <xref:System.Windows.Forms.DataGridViewCell> doğrudan sınıf.</span><span class="sxs-lookup"><span data-stu-id="56e2e-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56e2e-110">Olduğunda, türetilen <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıf için yeni özellikler eklemek için geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="56e2e-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="56e2e-111">Ayrıca temel sınıfın çağırmalıdır `Clone` yöntemi, böylece yeni hücresinde veya sütununda için temel sınıf özelliklerini kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="56e2e-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e2e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="56e2e-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56e2e-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="56e2e-113">Compiling the Code</span></span>  
 <span data-ttu-id="56e2e-114">Aşağıdaki örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="56e2e-114">The following example requires:</span></span>  
  
- <span data-ttu-id="56e2e-115">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="56e2e-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="56e2e-116">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="56e2e-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="56e2e-117">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e2e-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e2e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56e2e-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="56e2e-119">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="56e2e-119">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="56e2e-120">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="56e2e-120">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="56e2e-121">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="56e2e-121">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
