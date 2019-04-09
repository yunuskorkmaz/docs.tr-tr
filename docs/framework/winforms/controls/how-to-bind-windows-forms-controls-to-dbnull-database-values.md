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
ms.openlocfilehash: cc3dde0db3dad6faff548951ff06a39d23248d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137767"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="bbcae-102">Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="bbcae-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="bbcae-103">Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndürür bir <xref:System.DBNull> değeri bölümünün yerine uygun değeri işleme, biçimlendirme veya ayrıştırma olayları olmadan.</span><span class="sxs-lookup"><span data-stu-id="bbcae-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="bbcae-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya ayrıştırma veri kaynağı değerleri belirtilen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="bbcae-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbcae-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbcae-105">Example</span></span>  
 <span data-ttu-id="bbcae-106">Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.DBNull> iki farklı durumlarda değeri.</span><span class="sxs-lookup"><span data-stu-id="bbcae-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="bbcae-107">İlk nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Forms.Binding.NullValue%2A> bir dize özelliği için; ikinci nasıl ayarlanacağı gösterilmektedir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir resim özelliği için.</span><span class="sxs-lookup"><span data-stu-id="bbcae-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="bbcae-108">İlişkili özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hataya neden olur ve başka <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="bbcae-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="bbcae-109">Bu durumda, bir özel durum değil.</span><span class="sxs-lookup"><span data-stu-id="bbcae-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbcae-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bbcae-110">Compiling the Code</span></span>  
 <span data-ttu-id="bbcae-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bbcae-111">This example requires:</span></span>  
  
-   <span data-ttu-id="bbcae-112">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="bbcae-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bbcae-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bbcae-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bbcae-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbcae-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbcae-115">See also</span></span>

- [<span data-ttu-id="bbcae-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="bbcae-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="bbcae-117">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="bbcae-117">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="bbcae-118">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="bbcae-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
