---
title: 'Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama'
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
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60bff96bbb732162867a4e63e651982b359ae88d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="50e49-102">Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="50e49-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="50e49-103">Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndüren bir <xref:System.DBNull> değeri, yerine uygun değeri işleme, biçimlendirme veya olayları ayrıştırma olmadan.</span><span class="sxs-lookup"><span data-stu-id="50e49-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="50e49-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya veri kaynağı değerlerini ayrıştırma belirtilen bir nesneye.</span><span class="sxs-lookup"><span data-stu-id="50e49-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50e49-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="50e49-105">Example</span></span>  
 <span data-ttu-id="50e49-106">Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.DBNull> iki farklı durumlarda değeri.</span><span class="sxs-lookup"><span data-stu-id="50e49-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="50e49-107">İlk nasıl ayarlanacağını gösterir <xref:System.Windows.Forms.Binding.NullValue%2A> dizesi özelliği için; ikinci nasıl ayarlanacağını gösterir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir görüntü özelliği için.</span><span class="sxs-lookup"><span data-stu-id="50e49-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="50e49-108">Bağlı özellik türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olması gerekir veya bir hata neden olacak ve daha fazla <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="50e49-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="50e49-109">Bu durumda, bir özel durum değil.</span><span class="sxs-lookup"><span data-stu-id="50e49-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50e49-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="50e49-110">Compiling the Code</span></span>  
 <span data-ttu-id="50e49-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="50e49-111">This example requires:</span></span>  
  
-   <span data-ttu-id="50e49-112">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="50e49-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="50e49-113">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="50e49-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="50e49-114">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="50e49-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="50e49-115">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="50e49-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e49-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50e49-116">See Also</span></span>  
 [<span data-ttu-id="50e49-117">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="50e49-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="50e49-118">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="50e49-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [<span data-ttu-id="50e49-119">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="50e49-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
