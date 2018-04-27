---
title: SQL XML sütun değerleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c4eecbe66df3224e6dc3f118be474f25712afe8a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="1af69-102">SQL XML sütun değerleri</span><span class="sxs-lookup"><span data-stu-id="1af69-102">SQL XML Column Values</span></span>
<span data-ttu-id="1af69-103">SQL Server destekler `xml` veri türü ve geliştiriciler, standart davranışını kullanarak bu türü içeren sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1af69-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="1af69-104">Bir `xml` yalnızca herhangi bir sütun getirildiği sütun alınabilir (içine bir <xref:System.Data.SqlClient.SqlDataReader>, örneğin) ancak sütunun XML olarak içeriğini çalışmak isterseniz, kullanmanız gereken bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1af69-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1af69-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1af69-105">Example</span></span>  
 <span data-ttu-id="1af69-106">Aşağıdaki konsol uygulaması her içeren iki satırları seçer bir `xml` sütun, gelen **Sales.Store** tablosundaki **AdventureWorks** için veritabanı bir <xref:System.Data.SqlClient.SqlDataReader> örneği.</span><span class="sxs-lookup"><span data-stu-id="1af69-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="1af69-107">Değeri, her satır için `xml` sütun kullanarak okunur <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="1af69-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="1af69-108">Değer depolanan bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1af69-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="1af69-109">Kullanmanız gereken Not <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yerine <xref:System.Data.IDataRecord.GetValue%2A> içeriği hale getirmek istiyorsanız yöntemi bir <xref:System.Data.SqlTypes.SqlXml> değişkeni; <xref:System.Data.IDataRecord.GetValue%2A> değerini döndürür `xml` sütunu bir dize olarak.</span><span class="sxs-lookup"><span data-stu-id="1af69-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1af69-110">**AdventureWorks** örnek veritabanını SQL Server'ı yüklediğinizde varsayılan olarak yüklenmedi.</span><span class="sxs-lookup"><span data-stu-id="1af69-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="1af69-111">SQL Server Kurulumu çalıştırarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1af69-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1af69-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1af69-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="1af69-113">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="1af69-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="1af69-114">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1af69-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
