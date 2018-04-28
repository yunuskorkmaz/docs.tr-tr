---
title: 'Nasıl Yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma'
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
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1907f25e2d9bfe5fc6e93020add47d8a52379e87
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="67e12-102">Nasıl Yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma</span><span class="sxs-lookup"><span data-stu-id="67e12-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="67e12-103">Verileri kullanarak formlar arasında kolayca paylaşabilir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="67e12-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="67e12-104">Örneğin, veri kaynağı verileri özetleyen bir salt okunur ve veri kaynağındaki şu anda seçili öğe hakkında ayrıntılı bilgi içeren başka bir düzenlenebilir formunda görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e12-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="67e12-105">Bu örnekte, bu senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="67e12-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e12-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="67e12-106">Example</span></span>  
 <span data-ttu-id="67e12-107">Aşağıdaki kod örneğinde nasıl paylaşacağınızı gösterir bir <xref:System.Windows.Forms.BindingSource> ve bağlı verileri formlar arasında.</span><span class="sxs-lookup"><span data-stu-id="67e12-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="67e12-108">Bu örnekte, paylaşılan <xref:System.Windows.Forms.BindingSource> alt formu oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="67e12-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="67e12-109">Alt formun ana formdaki şu anda seçili öğe için verileri düzenlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="67e12-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67e12-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Olayı <xref:System.Windows.Forms.BindingSource> bileşen iki forms eşitlenmiş kalmasını sağlamak için örnekte işlenir.</span><span class="sxs-lookup"><span data-stu-id="67e12-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="67e12-111">Neden hakkında daha fazla bilgi için bu yapılır, bkz: [nasıl yapılır: aynı veri kaynağı kalır eşitlenmesi için birden çok denetimleri bağlı sağlamak](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="67e12-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67e12-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="67e12-112">Compiling the Code</span></span>  
 <span data-ttu-id="67e12-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="67e12-113">This example requires:</span></span>  
  
-   <span data-ttu-id="67e12-114">Sistem, System.Windows.Forms, System.Drawing, System.Data ve System.Xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="67e12-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="67e12-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="67e12-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="67e12-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e12-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="67e12-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="67e12-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e12-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67e12-118">See Also</span></span>  
 [<span data-ttu-id="67e12-119">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="67e12-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="67e12-120">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="67e12-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="67e12-121">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="67e12-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
