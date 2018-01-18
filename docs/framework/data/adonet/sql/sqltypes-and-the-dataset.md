---
title: "SqlTypes ve veri kümesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 61308d6c2c66e1c163431ced8d9c66980705b9c7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="9de23-102">SqlTypes ve veri kümesi</span><span class="sxs-lookup"><span data-stu-id="9de23-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="9de23-103">Sunulan ADO.NET 2.0 türü için gelişmiş destek `DataSet` aracılığıyla <xref:System.Data.SqlTypes> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9de23-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="9de23-104">Türler <xref:System.Data.SqlTypes> veri türleri SQL Server veritabanında veri türleri olarak aynı semantiği ve duyarlık sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9de23-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="9de23-105">Her bir veri türü <xref:System.Data.SqlTypes> eşdeğer veri türü SQL Server ile aynı temel alınan veri temsili sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9de23-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="9de23-106">Kullanarak <xref:System.Data.SqlTypes> doğrudan bir <xref:System.Data.DataSet> birkaç avantaj SQL Server veri türleriyle çalışırken confers.</span><span class="sxs-lookup"><span data-stu-id="9de23-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="9de23-107"><xref:System.Data.SqlTypes>SQL Server yerel veri türleri aynı topluca destekler.</span><span class="sxs-lookup"><span data-stu-id="9de23-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="9de23-108">Aşağıdakilerden birini belirterek <xref:System.Data.SqlTypes> tanımındaki bir <xref:System.Data.DataColumn> ortak dil çalışma zamanı (CLR) veri türlerinden biri için ondalık veya sayısal veri türlerini dönüştürme oluşabilir duyarlık kaybına ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9de23-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9de23-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9de23-109">Example</span></span>  
 <span data-ttu-id="9de23-110">Aşağıdaki örnekte bir <xref:System.Data.DataTable> açıkça tanımlayan nesne <xref:System.Data.DataColumn> kullanarak, veri türleri <xref:System.Data.SqlTypes> CLR Türleri yerine.</span><span class="sxs-lookup"><span data-stu-id="9de23-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="9de23-111">Kod doldurur <xref:System.Data.DataTable> AdventureWorks veritabanını SQL Server'ın Sales.SalesOrderDetail tabloda verilerle.</span><span class="sxs-lookup"><span data-stu-id="9de23-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="9de23-112">SQL Server'dan değerleri alınır ve konsol penceresinde görüntülenen çıktı her sütunun veri türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9de23-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9de23-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9de23-113">See Also</span></span>  
 [<span data-ttu-id="9de23-114">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="9de23-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="9de23-115">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9de23-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="9de23-116">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9de23-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
