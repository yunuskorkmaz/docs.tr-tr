---
title: Iki DataGridView denetimi kullanarak ana ayrıntı formu oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737325"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="f3b88-102">Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3b88-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="f3b88-103">Aşağıdaki kod örneği, iki <xref:System.Windows.Forms.BindingSource> bileşeni ile bağlantılı iki <xref:System.Windows.Forms.DataGridView> denetimini kullanarak bir ana/ayrıntı formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3b88-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="f3b88-104">Veri kaynağı Northwind SQL Server örnek veritabanından `Customers` ve `Orders` tabloları içeren bir <xref:System.Data.DataSet> <xref:System.Data.DataRelation> sütunu ile ilişkili bir `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="f3b88-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="f3b88-105">Bir <xref:System.Windows.Forms.BindingSource>, veri kümesindeki üst `Customers` tabloya bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f3b88-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="f3b88-106">Bu veriler ana <xref:System.Windows.Forms.DataGridView> denetiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f3b88-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f3b88-107">Diğer <xref:System.Windows.Forms.BindingSource> ilk veri bağlayıcısına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f3b88-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="f3b88-108">İkinci <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliği <xref:System.Data.DataRelation> adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f3b88-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="f3b88-109">Bu, ilişkili ayrıntı <xref:System.Windows.Forms.DataGridView> denetiminin ana <xref:System.Windows.Forms.DataGridView> denetimindeki geçerli satıra karşılık gelen alt `Orders` tablosunun satırlarını görüntülemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f3b88-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="f3b88-110">Bu kod örneği hakkında ayrıntılı bir açıklama için bkz. [Izlenecek yol: iki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="f3b88-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b88-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3b88-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3b88-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f3b88-112">Compiling the Code</span></span>  
 <span data-ttu-id="f3b88-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f3b88-113">This example requires:</span></span>  
  
 <span data-ttu-id="f3b88-114">Sisteme, System. Data, System. Windows. Forms ve System. XML derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="f3b88-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f3b88-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f3b88-115">.NET Framework Security</span></span>  
 <span data-ttu-id="f3b88-116">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="f3b88-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="f3b88-117">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="f3b88-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="f3b88-118">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="f3b88-118">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b88-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3b88-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="f3b88-120">İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3b88-120">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="f3b88-121">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f3b88-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f3b88-122">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="f3b88-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
