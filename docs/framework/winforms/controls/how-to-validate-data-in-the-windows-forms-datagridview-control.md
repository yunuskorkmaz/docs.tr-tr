---
title: DataGridView Denetimindeki verileri doğrulama
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
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728314"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="99663-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="99663-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="99663-103">Aşağıdaki kod örneği, bir kullanıcı tarafından <xref:System.Windows.Forms.DataGridView> denetimine girilen verilerin nasıl doğrulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99663-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="99663-104">Bu örnekte, <xref:System.Windows.Forms.DataGridView> Northwind örnek veritabanının `Customers` tablosundaki satırlarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="99663-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="99663-105">Kullanıcı `CompanyName` sütununda bir hücreyi düzenlediğinde, boş olmadığını denetleyerek değeri geçerlilik için test edilir.</span><span class="sxs-lookup"><span data-stu-id="99663-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="99663-106"><xref:System.Windows.Forms.DataGridView.CellValidating> olayının olay işleyicisi değerin boş bir dize olduğunu belirlerse, <xref:System.Windows.Forms.DataGridView> boş olmayan bir dize girilene kadar kullanıcının hücreden çıkılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="99663-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="99663-107">Bu kod örneği hakkında ayrıntılı bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView Denetimindeki verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="99663-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99663-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="99663-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99663-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="99663-109">Compiling the Code</span></span>  
 <span data-ttu-id="99663-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="99663-110">This example requires:</span></span>  
  
- <span data-ttu-id="99663-111">System, System. Data, System. Windows. Forms ve System. XML derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="99663-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="99663-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="99663-112">.NET Framework Security</span></span>  
 <span data-ttu-id="99663-113">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="99663-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="99663-114">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="99663-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="99663-115">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="99663-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99663-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99663-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="99663-117">İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="99663-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="99663-118">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="99663-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="99663-119">İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma</span><span class="sxs-lookup"><span data-stu-id="99663-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="99663-120">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="99663-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
