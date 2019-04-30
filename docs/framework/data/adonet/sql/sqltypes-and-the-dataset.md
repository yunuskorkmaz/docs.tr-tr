---
title: SqlTypes ve DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: a218a8e0fe3d2c17a0f09a40645c7b3ad26fb5ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780178"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes ve DataSet
ADO.NET 2.0 kullanılmaya türü için gelişmiş destek `DataSet` aracılığıyla <xref:System.Data.SqlTypes> ad alanı. Türlerinde <xref:System.Data.SqlTypes> veri türleri SQL Server veritabanında veri türleri olarak aynı semantiği ve duyarlılık sağlamak üzere tasarlanmıştır. Her bir veri türü <xref:System.Data.SqlTypes> eşdeğeri veri türü SQL Server ile aynı temel alınan veri gösterimi vardır.  
  
 Kullanarak <xref:System.Data.SqlTypes> doğrudan bir <xref:System.Data.DataSet> SQL Server veri türleri ile çalışırken, çeşitli avantajlar confers. <xref:System.Data.SqlTypes> SQL Server yerel veri türleri ile aynı semantiğe destekler. Aşağıdakilerden birini belirterek <xref:System.Data.SqlTypes> tanımındaki bir <xref:System.Data.DataColumn> bir ortak dil çalışma zamanı (CLR) veri türlerini ondalık veya sayısal veri türlerini dönüştürme oluşabilir kesinlik kaybı ortadan kaldırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataTable> açıkça tanımlayan nesne, <xref:System.Data.DataColumn> kullanarak veri türleri <xref:System.Data.SqlTypes> CLR Türleri yerine. Kod doldurur <xref:System.Data.DataTable> AdventureWorks veritabanını SQL Server'daki Sales.SalesOrderDetail tablodaki verilerle. Değerleri SQL Server'dan alınan ve çıktıyı konsol penceresinde görüntülenen her bir sütunun veri türünü gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
