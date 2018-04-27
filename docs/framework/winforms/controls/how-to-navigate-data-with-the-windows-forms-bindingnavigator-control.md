---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a47273f9598b3776276c14d41e88f7f0dff5bed
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="e683d-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="e683d-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="e683d-103">Geliştirilirken <xref:System.Windows.Forms.BindingNavigator> Windows Forms denetiminde oluşturdukları formlarında basit veri gezinme ve düzenleme kullanıcı arabirimi ile son kullanıcılar sağlamak için geliştiriciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e683d-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="e683d-104"><xref:System.Windows.Forms.BindingNavigator> Denetimi bir <xref:System.Windows.Forms.ToolStrip> denetimi düğmeleri ile önceden yapılandırılmış ilk gezinme için son olarak, bir veri kümesi olarak ekleyin ve kayıt silme düğmeleri, önceki ve sonraki kayıt.</span><span class="sxs-lookup"><span data-stu-id="e683d-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="e683d-105">Düğmelere ekleme <xref:System.Windows.Forms.BindingNavigator> denetim kolaydır, çünkü bir <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="e683d-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="e683d-106">Ayrıca bkz. [nasıl yapılır: yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e683d-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="e683d-107">Her düğme için <xref:System.Windows.Forms.BindingNavigator> denetlemek, karşılık gelen bir üyesi <xref:System.Windows.Forms.BindingSource> program aracılığıyla aynı işlevselliği sağlayan bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e683d-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="e683d-108">Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e683d-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="e683d-109">Sonuç olarak, etkinleştirme <xref:System.Windows.Forms.BindingNavigator> veri kayıtlarını gitmek için denetimidir basit bir ayarı olarak kendi <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğine uygun <xref:System.Windows.Forms.BindingSource> formdaki bileşen.</span><span class="sxs-lookup"><span data-stu-id="e683d-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="e683d-110">BindingNavigator denetimi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e683d-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="e683d-111">Ekleme bir <xref:System.Windows.Forms.BindingSource> adlı bileşeni `bindingSource1` ve iki <xref:System.Windows.Forms.TextBox> adlı denetimleri `textBox1` ve `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="e683d-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="e683d-112">Bağlama `bindingSource1` veri ve textbox denetimleri `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="e683d-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="e683d-113">Bunu yapmak için aşağıdaki kodu form ve çağrı yapıştırın `LoadData` formun oluşturucusundan veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e683d-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="e683d-114">Ekleme bir <xref:System.Windows.Forms.BindingNavigator> adlı Denetim `bindingNavigator1` formunuza.</span><span class="sxs-lookup"><span data-stu-id="e683d-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="e683d-115">Ayarlama <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliği için `bindingNavigator1` için `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="e683d-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="e683d-116">Tasarımcı ile veya kod bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e683d-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="e683d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e683d-117">Example</span></span>  
 <span data-ttu-id="e683d-118">Aşağıdaki kod örneğinde, daha önce listelenen adımları için tam örnektir.</span><span class="sxs-lookup"><span data-stu-id="e683d-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e683d-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e683d-119">Compiling the Code</span></span>  
 <span data-ttu-id="e683d-120">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e683d-120">This example requires:</span></span>  
  
-   <span data-ttu-id="e683d-121">Sistem, System.Data, System.Drawing, System.Windows.Forms ve System.Xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e683d-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="e683d-122">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e683d-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e683d-123">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="e683d-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e683d-124">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e683d-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e683d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e683d-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="e683d-126">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="e683d-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="e683d-127">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="e683d-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
