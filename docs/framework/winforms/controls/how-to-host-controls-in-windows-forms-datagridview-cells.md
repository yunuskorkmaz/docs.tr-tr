---
title: "Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fd74b54a4e8c91762a3f32c6c89877470c10960
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="f18e2-102">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="f18e2-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="f18e2-103"><xref:System.Windows.Forms.DataGridView> Denetimi girin ve çeşitli şekillerde değerlerini düzenlemek, kullanıcılarınızın etkinleştirme birkaç sütun türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f18e2-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="f18e2-104">Ancak, bu sütun türleri veri girişi gereksinimlerinizi karşılamazsa, seçtiğiniz denetimleri konak hücrelerle kendi sütun türleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f18e2-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="f18e2-105">Bunu yapmak için öğesinden türetilen sınıflarını tanımlamak <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="f18e2-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="f18e2-106">Türetilen bir sınıfı tanımlamanız gerekir <xref:System.Windows.Forms.Control> ve uygulayan <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f18e2-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="f18e2-107">Aşağıdaki kod örneğinde bir takvim sütun oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f18e2-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="f18e2-108">Bu sütunun hücre normal metin kutusu hücrelerindeki, ancak kullanıcı hücrenin düzenlediğinde tarihleri görüntüleme bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür.</span><span class="sxs-lookup"><span data-stu-id="f18e2-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="f18e2-109">Metin kutusu görüntü işlevlerini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıfı türer <xref:System.Windows.Forms.DataGridViewTextBoxCell> devralma yerine sınıfı <xref:System.Windows.Forms.DataGridViewCell> doğrudan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f18e2-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f18e2-110">Türetilen zaman <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıfın yeni özellikler ekleme, geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f18e2-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="f18e2-111">Temel sınıfın da çağırmalıdır `Clone` yöntemi böylece temel sınıfının özelliklerini yeni hücresinde veya sütununda kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f18e2-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18e2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f18e2-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f18e2-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f18e2-113">Compiling the Code</span></span>  
 <span data-ttu-id="f18e2-114">Aşağıdaki örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f18e2-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="f18e2-115">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f18e2-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f18e2-116">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f18e2-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f18e2-117">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="f18e2-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f18e2-118">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f18e2-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18e2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f18e2-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [<span data-ttu-id="f18e2-120">Windows Forms DataGridView denetimini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f18e2-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f18e2-121">DataGridView denetimi mimarisi</span><span class="sxs-lookup"><span data-stu-id="f18e2-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="f18e2-122">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="f18e2-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
