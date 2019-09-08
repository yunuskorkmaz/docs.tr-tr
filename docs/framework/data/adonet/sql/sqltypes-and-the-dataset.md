---
title: SqlTypes ve DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791491"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="d2ae7-102">SqlTypes ve DataSet</span><span class="sxs-lookup"><span data-stu-id="d2ae7-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="d2ae7-103">ADO.NET 2,0, `DataSet` <xref:System.Data.SqlTypes> ad alanı aracılığıyla için geliştirilmiş tür desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="d2ae7-104">İçindeki <xref:System.Data.SqlTypes> türler, bir SQL Server veritabanındaki veri türleriyle aynı semantiğe ve duyarlığa sahip veri türleri sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="d2ae7-105">İçindeki <xref:System.Data.SqlTypes> her veri türü, aynı temel veri gösterimiyle SQL Server benzer bir veri türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="d2ae7-106">Doğrudan <xref:System.Data.SqlTypes> bir<xref:System.Data.DataSet> yapılandırmalarda kullanmak SQL Server veri türleriyle çalışırken çeşitli avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="d2ae7-107"><xref:System.Data.SqlTypes>SQL Server yerel veri türleriyle aynı semantiğini destekler.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="d2ae7-108">Öğesinin tanımında <xref:System.Data.SqlTypes> <xref:System.Data.DataColumn> birini belirtmek, ondalık veya sayısal veri türlerini ortak dil çalışma zamanı (CLR) veri türlerinden birine dönüştürürken oluşabilecek duyarlık kaybını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2ae7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2ae7-109">Example</span></span>  
 <span data-ttu-id="d2ae7-110">Aşağıdaki örnek, clr türleri <xref:System.Data.DataTable> yerine kullanarak <xref:System.Data.DataColumn> <xref:System.Data.SqlTypes> veri türlerini açıkça tanımlayarak bir nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="d2ae7-111">Kod, <xref:System.Data.DataTable> SQL Server AdventureWorks veritabanındaki Sales. SalesOrderDetail tablosundan verileri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="d2ae7-112">Konsol penceresinde gösterilen çıktı, her sütunun veri türünü ve SQL Server alınan değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d2ae7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ae7-113">See also</span></span>

- [<span data-ttu-id="d2ae7-114">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="d2ae7-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d2ae7-115">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d2ae7-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d2ae7-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2ae7-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
