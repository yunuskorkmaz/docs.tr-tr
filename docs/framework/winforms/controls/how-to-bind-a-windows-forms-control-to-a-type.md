---
title: 'Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama'
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
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dede24814474c9b344815a077f480935fb894be9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="62dcc-102">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="62dcc-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="62dcc-103">Verilerle etkileşimli denetimleri oluştururken, bazen, bir nesne yerine bir tür bir denetimi bağlamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62dcc-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="62dcc-104">Ne zaman veri kullanılamayabilir, ancak bir türün ortak arabirim bilgilerini görüntülemek, veri bağlama denetimleri hala gerekir özellikle tasarım zamanında, bu durum ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="62dcc-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="62dcc-105">Örneğin, bağlayabilirsiniz bir <xref:System.Windows.Forms.DataGridView> denetlemek için bir Web hizmeti tarafından sunulan bir nesne ve istediğiniz <xref:System.Windows.Forms.DataGridView> sütunlarını tasarım zamanında üyeyi içeren özel bir tür adlarını etiketlemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="62dcc-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="62dcc-106">Bir denetim türü ile kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="62dcc-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62dcc-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="62dcc-107">Example</span></span>  
 <span data-ttu-id="62dcc-108">Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak özel bir tür denetimi bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="62dcc-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="62dcc-109">Örnek çalıştırdığınızda, fark edeceksiniz <xref:System.Windows.Forms.DataGridView> özelliklerini yansıtan sütunları etiketli bir `Customer` denetimi verilerle doldurulur önce nesne.</span><span class="sxs-lookup"><span data-stu-id="62dcc-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="62dcc-110">Örnek veri eklemek için bir müşteri Ekle düğmesi bulunur <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="62dcc-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="62dcc-111">Düğmeye tıkladığınızda yeni bir `Customer` nesne eklenmiş olup <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="62dcc-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="62dcc-112">Gerçek hayattaki bir senaryoda, verileri bir Web hizmeti veya diğer veri kaynağı için bir çağrı tarafından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="62dcc-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62dcc-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="62dcc-113">Compiling the Code</span></span>  
 <span data-ttu-id="62dcc-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="62dcc-114">This example requires:</span></span>  
  
-   <span data-ttu-id="62dcc-115">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="62dcc-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="62dcc-116">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="62dcc-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="62dcc-117">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62dcc-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="62dcc-118">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="62dcc-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62dcc-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62dcc-119">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="62dcc-120">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="62dcc-120">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
