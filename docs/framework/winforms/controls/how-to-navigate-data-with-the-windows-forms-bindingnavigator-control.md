---
title: BindingNavigator denetimi ile verilerde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736004"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="5264c-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="5264c-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="5264c-103">Windows Forms ' deki <xref:System.Windows.Forms.BindingNavigator> denetiminin, geliştiricilerin oluşturdukları formlara basit bir veri gezintisi ve düzenleme kullanıcı arabirimi sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5264c-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="5264c-104"><xref:System.Windows.Forms.BindingNavigator> denetimi, bir veri kümesindeki ilk, son, sonraki ve önceki kayda gezinti için önceden yapılandırılmış düğmelerin yanı sıra kayıt ekleme ve silme düğmelerine sahip bir <xref:System.Windows.Forms.ToolStrip> denetimidir.</span><span class="sxs-lookup"><span data-stu-id="5264c-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="5264c-105"><xref:System.Windows.Forms.BindingNavigator> denetimine düğme eklemek kolaydır çünkü <xref:System.Windows.Forms.ToolStrip> bir denetim.</span><span class="sxs-lookup"><span data-stu-id="5264c-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5264c-106">Örnekler için bkz. [nasıl yapılır: Windows Forms BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="5264c-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="5264c-107"><xref:System.Windows.Forms.BindingNavigator> denetimindeki her düğme için, aynı işlevselliğe programlı olarak izin veren <xref:System.Windows.Forms.BindingSource> bileşeninin karşılık gelen bir üyesi vardır.</span><span class="sxs-lookup"><span data-stu-id="5264c-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="5264c-108">Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemine karşılık gelir, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemine karşılık gelir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="5264c-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="5264c-109">Sonuç olarak, veri kayıtlarında gezinmek için <xref:System.Windows.Forms.BindingNavigator> denetiminin etkinleştirilmesi, <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini formdaki uygun <xref:System.Windows.Forms.BindingSource> bileşeni olarak ayarlamak kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="5264c-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="5264c-110">BindingNavigator denetimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5264c-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="5264c-111">`bindingSource1` adlı ve `textBox1` ve `textBox2`adlı iki <xref:System.Windows.Forms.TextBox> denetim <xref:System.Windows.Forms.BindingSource> bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5264c-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="5264c-112">`bindingSource1` verilere ve metin kutusu denetimlerine `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="5264c-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="5264c-113">Bunu yapmak için, aşağıdaki kodu formunuza yapıştırın ve formun Oluşturucu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminden `LoadData` çağırın.</span><span class="sxs-lookup"><span data-stu-id="5264c-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="5264c-114">Formunuza `bindingNavigator1` adlı <xref:System.Windows.Forms.BindingNavigator> bir denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5264c-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="5264c-115">`bindingNavigator1` için <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> özelliğini `bindingSource1`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5264c-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="5264c-116">Bunu tasarımcı veya kod içinde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5264c-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="5264c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5264c-117">Example</span></span>  
 <span data-ttu-id="5264c-118">Aşağıdaki kod örneği, daha önce listelenen adımlar için tüm örnektir.</span><span class="sxs-lookup"><span data-stu-id="5264c-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5264c-119">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="5264c-119">Compiling the Code</span></span>  
 <span data-ttu-id="5264c-120">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5264c-120">This example requires:</span></span>  
  
- <span data-ttu-id="5264c-121">System, System. Data, System. Drawing, System. Windows. Forms ve System. xml derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="5264c-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5264c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5264c-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="5264c-123">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="5264c-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="5264c-124">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="5264c-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
