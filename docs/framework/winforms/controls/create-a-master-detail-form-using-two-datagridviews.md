---
title: 'Nasıl yapılır: iki Windows Forms DataGridView denetimi kullanarak ana / ayrıntı formu oluşturma'
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
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 483955a4ec8d96ede413176421b787f84ab45eeb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="fbb88-102">Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbb88-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="fbb88-103">Aşağıdaki kod örneği iki kullanarak ana/ayrıntı formu oluşturur <xref:System.Windows.Forms.DataGridView> iki bağlama denetimleri <xref:System.Windows.Forms.BindingSource> bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="fbb88-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="fbb88-104">Veri kaynağı bir <xref:System.Data.DataSet> içeren `Customers` ve `Orders` ile birlikte Northwind SQL Server örnek veritabanındaki tablolar bir <xref:System.Data.DataRelation> aracılığıyla iki ilişkili `CustomerID` sütun.</span><span class="sxs-lookup"><span data-stu-id="fbb88-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="fbb88-105">Bir <xref:System.Windows.Forms.BindingSource> üst öğeye bağlı `Customers` veri kümesindeki tablo.</span><span class="sxs-lookup"><span data-stu-id="fbb88-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="fbb88-106">Bu veriler master görüntülenir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="fbb88-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fbb88-107">Diğer <xref:System.Windows.Forms.BindingSource> ilk veri bağlayıcısı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fbb88-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="fbb88-108"><xref:System.Windows.Forms.BindingSource.DataMember%2A> İkinci özelliğinin <xref:System.Windows.Forms.BindingSource> ayarlanır <xref:System.Data.DataRelation> adı.</span><span class="sxs-lookup"><span data-stu-id="fbb88-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="fbb88-109">Bu ilişkili ayrıntı neden <xref:System.Windows.Forms.DataGridView> alt satırları görüntülemek için Denetim `Orders` asıl geçerli satırda karşılık tablo <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="fbb88-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="fbb88-110">Bu kod örneği tam bir açıklaması için bkz: [izlenecek yol: bir ana öğe/ayrıntı formu kullanarak iki Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="fbb88-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb88-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbb88-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbb88-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fbb88-112">Compiling the Code</span></span>  
 <span data-ttu-id="fbb88-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fbb88-113">This example requires:</span></span>  
  
 <span data-ttu-id="fbb88-114">Sistem, System.Data, System.Windows.Forms ve System.XML derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fbb88-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
-   <span data-ttu-id="fbb88-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fbb88-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fbb88-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbb88-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="fbb88-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fbb88-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbb88-118">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fbb88-118">.NET Framework Security</span></span>  
 <span data-ttu-id="fbb88-119">Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fbb88-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="fbb88-120">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="fbb88-120">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="fbb88-121">Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="fbb88-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb88-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbb88-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="fbb88-123">İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbb88-123">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="fbb88-124">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fbb88-124">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="fbb88-125">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="fbb88-125">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
