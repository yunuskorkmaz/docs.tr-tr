---
title: 'Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: 19505c690728147d2a67c26371e1cea4c281ab08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013055"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="69a41-102">Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma</span><span class="sxs-lookup"><span data-stu-id="69a41-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="69a41-103">Kullanarak formlar arasında verileri kolayca paylaşabilirsiniz <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="69a41-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="69a41-104">Örneğin, veri kaynağı verileri özetleyen bir salt okunur ve veri kaynağındaki geçerli seçilmiş öğe hakkındaki ayrıntılı bilgileri içeren başka bir düzenlenebilir formunda görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a41-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="69a41-105">Bu örnekte, bu senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69a41-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a41-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="69a41-106">Example</span></span>  
 <span data-ttu-id="69a41-107">Aşağıdaki kod örneğinde nasıl paylaşacağınızı gösterir bir <xref:System.Windows.Forms.BindingSource> ve bağlı verileri formlar arasında.</span><span class="sxs-lookup"><span data-stu-id="69a41-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="69a41-108">Bu örnekte, paylaşılan <xref:System.Windows.Forms.BindingSource> alt formunun oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="69a41-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="69a41-109">Alt formun ana biçiminde geçerli seçilmiş öğe için veri düzenlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="69a41-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a41-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Olayı <xref:System.Windows.Forms.BindingSource> bileşeni örnekte iki eşitlenmiş kalmasını sağlamak için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="69a41-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="69a41-111">Neden hakkında daha fazla bilgi için bu gerçekleştirilir, bkz: [nasıl yapılır: Birden çok denetimin eşitlenmiş kalmasını aynı veri kaynağına bağlanan](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="69a41-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69a41-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="69a41-112">Compiling the Code</span></span>  
 <span data-ttu-id="69a41-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="69a41-113">This example requires:</span></span>  
  
- <span data-ttu-id="69a41-114">Sistem, System.Windows.Forms, System.Drawing, System.Data ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="69a41-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="69a41-115">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="69a41-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="69a41-116">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a41-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a41-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a41-117">See also</span></span>

- [<span data-ttu-id="69a41-118">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="69a41-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="69a41-119">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="69a41-119">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="69a41-120">Nasıl yapılır: Hataları ve ortaya çıkan özel durumlar veri bağlama ile işleme</span><span class="sxs-lookup"><span data-stu-id="69a41-120">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
