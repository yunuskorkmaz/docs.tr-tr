---
title: 'Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 278fd4ed0622673a49bfaa2567501b832bd535d3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469966"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="d58a6-102">Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="d58a6-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="d58a6-103">Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndürür bir <xref:System.DBNull> değeri bölümünün yerine uygun değeri işleme, biçimlendirme veya ayrıştırma olayları olmadan.</span><span class="sxs-lookup"><span data-stu-id="d58a6-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="d58a6-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya ayrıştırma veri kaynağı değerleri belirtilen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="d58a6-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d58a6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d58a6-105">Example</span></span>  
 <span data-ttu-id="d58a6-106">Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.DBNull> iki farklı durumlarda değeri.</span><span class="sxs-lookup"><span data-stu-id="d58a6-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="d58a6-107">İlk nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Forms.Binding.NullValue%2A> bir dize özelliği için; ikinci nasıl ayarlanacağı gösterilmektedir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir resim özelliği için.</span><span class="sxs-lookup"><span data-stu-id="d58a6-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="d58a6-108">İlişkili özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hataya neden olur ve başka <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="d58a6-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="d58a6-109">Bu durumda, bir özel durum değil.</span><span class="sxs-lookup"><span data-stu-id="d58a6-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d58a6-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d58a6-110">Compiling the Code</span></span>  
 <span data-ttu-id="d58a6-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d58a6-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d58a6-112">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="d58a6-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d58a6-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d58a6-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d58a6-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d58a6-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="d58a6-115">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d58a6-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58a6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d58a6-116">See Also</span></span>  
 [<span data-ttu-id="d58a6-117">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="d58a6-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="d58a6-118">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="d58a6-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [<span data-ttu-id="d58a6-119">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="d58a6-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
