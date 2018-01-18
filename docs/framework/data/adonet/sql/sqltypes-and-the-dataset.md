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
# <a name="sqltypes-and-the-dataset"></a>SqlTypes ve veri kümesi
Sunulan ADO.NET 2.0 türü için gelişmiş destek `DataSet` aracılığıyla <xref:System.Data.SqlTypes> ad alanı. Türler <xref:System.Data.SqlTypes> veri türleri SQL Server veritabanında veri türleri olarak aynı semantiği ve duyarlık sağlamak üzere tasarlanmıştır. Her bir veri türü <xref:System.Data.SqlTypes> eşdeğer veri türü SQL Server ile aynı temel alınan veri temsili sahiptir.  
  
 Kullanarak <xref:System.Data.SqlTypes> doğrudan bir <xref:System.Data.DataSet> birkaç avantaj SQL Server veri türleriyle çalışırken confers. <xref:System.Data.SqlTypes>SQL Server yerel veri türleri aynı topluca destekler. Aşağıdakilerden birini belirterek <xref:System.Data.SqlTypes> tanımındaki bir <xref:System.Data.DataColumn> ortak dil çalışma zamanı (CLR) veri türlerinden biri için ondalık veya sayısal veri türlerini dönüştürme oluşabilir duyarlık kaybına ortadan kaldırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataTable> açıkça tanımlayan nesne <xref:System.Data.DataColumn> kullanarak, veri türleri <xref:System.Data.SqlTypes> CLR Türleri yerine. Kod doldurur <xref:System.Data.DataTable> AdventureWorks veritabanını SQL Server'ın Sales.SalesOrderDetail tabloda verilerle. SQL Server'dan değerleri alınır ve konsol penceresinde görüntülenen çıktı her sütunun veri türünü gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
