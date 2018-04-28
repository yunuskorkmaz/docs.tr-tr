---
title: 'Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme'
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
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 464ceb42416c91ae84c20c65fba2629479b1a0cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="6b37c-102">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="6b37c-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="6b37c-103">Denetimlere bağlama görmemeleri özel durumlar ve hataları temel iş nesnelerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6b37c-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="6b37c-104">Bu hataları ve özel durumları müdahale ve sonra kurtarmak veya hata bilgilerini kullanıcıya işleyerek geçirmek <xref:System.Windows.Forms.Binding.BindingComplete> belirli bir olay <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, veya <xref:System.Windows.Forms.CurrencyManager> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6b37c-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b37c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b37c-105">Example</span></span>  
 <span data-ttu-id="6b37c-106">Bu kod örneği, hataları ve veri bağlama işlemi sırasında gerçekleşen özel durumları işlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b37c-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="6b37c-107">Hataları işleme tarafından müdahale yapmayı gösteren <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> olayı <xref:System.Windows.Forms.Binding> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6b37c-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="6b37c-108">Bu olay işleyerek hataları ve özel durumları müdahale için için bağlama biçimlendirme etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b37c-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="6b37c-109">Bağlama oluşturulan ya da bağlama koleksiyonuna veya ayarlayarak eklenen biçimlendirme etkinleştirebilirsiniz <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="6b37c-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="6b37c-110">Ne zaman kodunu çalıştıran ve boş bir dize bölümü adı veya bir değer 100'den için girilen parça numarası için bir ileti kutusu görünür girilir.</span><span class="sxs-lookup"><span data-stu-id="6b37c-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="6b37c-111">Bu bir işleme sonucudur <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> bu textbox bağlamaları için olay.</span><span class="sxs-lookup"><span data-stu-id="6b37c-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b37c-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6b37c-112">Compiling the Code</span></span>  
 <span data-ttu-id="6b37c-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6b37c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="6b37c-114">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6b37c-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6b37c-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6b37c-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b37c-116">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="6b37c-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6b37c-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6b37c-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b37c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b37c-118">See Also</span></span>  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [<span data-ttu-id="6b37c-119">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6b37c-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
