---
title: SQL XML Sütun Değerleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 03b09d3a53c725bb0e84ba6b5d98944267bc564c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780793"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="68812-102">SQL XML Sütun Değerleri</span><span class="sxs-lookup"><span data-stu-id="68812-102">SQL XML Column Values</span></span>
<span data-ttu-id="68812-103">SQL Server `xml` veri türünü destekler ve geliştiriciler, <xref:System.Data.SqlClient.SqlCommand> sınıfının standart davranışını kullanarak bu tür dahil sonuç kümelerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="68812-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="68812-104">Bir sütun, herhangi bir sütun alındığı gibi (örneğin, bir <xref:System.Data.SqlClient.SqlDataReader>) alınabilir <xref:System.Xml.XmlReader>, ancak sütunun içeriğiyle XML olarak çalışmak istiyorsanız, ' yi kullanmanız gerekir. `xml`</span><span class="sxs-lookup"><span data-stu-id="68812-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68812-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="68812-105">Example</span></span>  
 <span data-ttu-id="68812-106">Aşağıdaki konsol uygulaması, her biri bir `xml` sütun içeren iki satırı, **AdventureWorks** veritabanındaki <xref:System.Data.SqlClient.SqlDataReader> **Sales. Store** tablosundan bir örneğe seçer.</span><span class="sxs-lookup"><span data-stu-id="68812-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="68812-107">Her satır için, `xml` sütunun değeri, <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>kullanılarak okundu.</span><span class="sxs-lookup"><span data-stu-id="68812-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="68812-108">Değer bir <xref:System.Xml.XmlReader>içinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="68812-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="68812-109">İçeriği bir <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.IDataRecord.GetValue%2A> değişkeneayarlamakistiyorsanızyöntemiyerine<xref:System.Data.SqlTypes.SqlXml> kullanmanız gerektiğini unutmayın; sütunundeğerini`xml` bir dize olarak döndürür. <xref:System.Data.IDataRecord.GetValue%2A></span><span class="sxs-lookup"><span data-stu-id="68812-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68812-110">SQL Server yüklediğinizde **AdventureWorks** örnek veritabanı varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="68812-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="68812-111">SQL Server kurulumunu çalıştırarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68812-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="68812-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68812-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="68812-113">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="68812-113">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="68812-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="68812-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
