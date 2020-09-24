---
title: SQL XML Sütun Değerleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: cd55e2263d4b71fe62910ac918e331ebe37833eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177286"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="721cf-102">SQL XML Sütun Değerleri</span><span class="sxs-lookup"><span data-stu-id="721cf-102">SQL XML Column Values</span></span>

<span data-ttu-id="721cf-103">SQL Server `xml` veri türünü destekler ve geliştiriciler, sınıfının standart davranışını kullanarak bu tür dahil sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="721cf-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="721cf-104">Bir `xml` sütun, herhangi bir sütun alındığı gibi ( <xref:System.Data.SqlClient.SqlDataReader> Örneğin, bir) alınabilir, ancak SÜTUNUN içeriğiyle XML olarak çalışmak istiyorsanız, ' yi kullanmanız gerekir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="721cf-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="721cf-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="721cf-105">Example</span></span>  

 <span data-ttu-id="721cf-106">Aşağıdaki konsol uygulaması, her biri bir sütun içeren iki satırı, `xml` **AdventureWorks** veritabanındaki **Sales. Store** tablosundan bir <xref:System.Data.SqlClient.SqlDataReader> örneğe seçer.</span><span class="sxs-lookup"><span data-stu-id="721cf-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="721cf-107">Her satır için, sütunun değeri, `xml` yöntemi kullanılarak okundu <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="721cf-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="721cf-108">Değer bir içinde depolanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="721cf-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="721cf-109"><xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.IDataRecord.GetValue%2A> İçeriği bir değişkene ayarlamak istiyorsanız yöntemi yerine kullanmanız gerektiğini unutmayın <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> `xml` sütunun değerini bir dize olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="721cf-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="721cf-110">SQL Server yüklediğinizde **AdventureWorks** örnek veritabanı varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="721cf-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="721cf-111">SQL Server kurulumunu çalıştırarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="721cf-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="721cf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="721cf-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="721cf-113">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="721cf-113">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="721cf-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="721cf-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
