---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 6c6090b3bd853b2e265ee4811051b4999b10ca86
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469031"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6115a-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="6115a-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6115a-103">Aşağıdaki kod örneği, içinde bir kullanıcı tarafından girilen verileri doğrulamak gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6115a-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6115a-104">Bu örnekte, <xref:System.Windows.Forms.DataGridView> satırlardan doldurulur `Customers` Northwind örnek veritabanıyla kurulan tablosu.</span><span class="sxs-lookup"><span data-stu-id="6115a-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="6115a-105">Kullanıcı bir hücreye zaman düzenlediğini `CompanyName` sütununda, değerini test geçerliliğini, boş olmadığını kontrol ederek.</span><span class="sxs-lookup"><span data-stu-id="6115a-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="6115a-106">Varsa için olay işleyicisini <xref:System.Windows.Forms.DataGridView.CellValidating> olay bulur değeri boş bir dize olduğunu <xref:System.Windows.Forms.DataGridView> kullanıcının boş olmayan bir dize girilene kadar hücre çıkmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6115a-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="6115a-107">Bu kod örneği tam bir açıklaması için bkz. [izlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6115a-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6115a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6115a-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6115a-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6115a-109">Compiling the Code</span></span>  
 <span data-ttu-id="6115a-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6115a-110">This example requires:</span></span>  
  
-   <span data-ttu-id="6115a-111">Sistem, System.Data, System.Windows.Forms ve System.XML derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="6115a-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="6115a-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6115a-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6115a-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6115a-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6115a-114">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6115a-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6115a-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6115a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="6115a-116">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6115a-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="6115a-117">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="6115a-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="6115a-118">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="6115a-118">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6115a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6115a-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="6115a-120">İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="6115a-120">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6115a-121">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="6115a-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6115a-122">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="6115a-122">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="6115a-123">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="6115a-123">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
