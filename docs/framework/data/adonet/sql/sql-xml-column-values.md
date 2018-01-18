---
title: "SQL XML sütun değerleri"
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
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31ec6ae2b50870da7b999e20cd8ae44f1d42e03
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="d5a59-102">SQL XML sütun değerleri</span><span class="sxs-lookup"><span data-stu-id="d5a59-102">SQL XML Column Values</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="d5a59-103">destekleyen `xml` veri türü ve geliştiriciler, standart davranışını kullanarak bu türü içeren sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5a59-103"> supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="d5a59-104">Bir `xml` yalnızca herhangi bir sütun getirildiği sütun alınabilir (içine bir <xref:System.Data.SqlClient.SqlDataReader>, örneğin) ancak sütunun XML olarak içeriğini çalışmak isterseniz, kullanmanız gereken bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d5a59-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a59-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5a59-105">Example</span></span>  
 <span data-ttu-id="d5a59-106">Aşağıdaki konsol uygulaması her içeren iki satırları seçer bir `xml` sütun, gelen **Sales.Store** tablosundaki **AdventureWorks** için veritabanı bir <xref:System.Data.SqlClient.SqlDataReader> örneği.</span><span class="sxs-lookup"><span data-stu-id="d5a59-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="d5a59-107">Değeri, her satır için `xml` sütun kullanarak okunur <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d5a59-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="d5a59-108">Değer depolanan bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d5a59-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d5a59-109">Kullanmanız gereken Not <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yerine <xref:System.Data.IDataRecord.GetValue%2A> içeriği hale getirmek istiyorsanız yöntemi bir <xref:System.Data.SqlTypes.SqlXml> değişkeni; <xref:System.Data.IDataRecord.GetValue%2A> değerini döndürür `xml` sütunu bir dize olarak.</span><span class="sxs-lookup"><span data-stu-id="d5a59-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5a59-110">**AdventureWorks** örnek veritabanı yüklediğinizde varsayılan olarak yüklenmedi [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5a59-110">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5a59-111">Çalıştırarak yükleyebilirsiniz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kurulumu.</span><span class="sxs-lookup"><span data-stu-id="d5a59-111">You can install it by running [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a59-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a59-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="d5a59-113">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="d5a59-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="d5a59-114">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d5a59-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
