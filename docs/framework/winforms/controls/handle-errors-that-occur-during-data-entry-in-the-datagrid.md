---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma'
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
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd095d272c07727490df235328827f5ee9907b49
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7d12-102">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="c7d12-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7d12-103">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:System.Windows.Forms.DataGridView> rapor veri girişi sırasında oluşan hataları kullanıcıya denetimine.</span><span class="sxs-lookup"><span data-stu-id="c7d12-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="c7d12-104">Bu kod örneği tam bir açıklaması için bkz: [izlenecek yol: Windows Forms DataGridView denetimine veri girişi sırasında bu Occur hataları işleme](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="c7d12-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7d12-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7d12-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7d12-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c7d12-106">Compiling the Code</span></span>  
 <span data-ttu-id="c7d12-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c7d12-107">This example requires:</span></span>  
  
-   <span data-ttu-id="c7d12-108">Sistem, System.Data, System.Windows.Forms ve System.XML derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c7d12-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="c7d12-109">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c7d12-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c7d12-110">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="c7d12-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="c7d12-111">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c7d12-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c7d12-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c7d12-112">.NET Framework Security</span></span>  
 <span data-ttu-id="c7d12-113">Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c7d12-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="c7d12-114">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="c7d12-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="c7d12-115">Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="c7d12-115">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d12-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7d12-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="c7d12-117">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="c7d12-117">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="c7d12-118">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="c7d12-118">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c7d12-119">İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="c7d12-119">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c7d12-120">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="c7d12-120">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
