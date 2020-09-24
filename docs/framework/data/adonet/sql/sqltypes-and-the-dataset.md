---
title: SqlTypes ve DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 04f95cd7d3f6e52f644f23dd8a32c77d56a5ddda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147520"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes ve DataSet

ADO.NET 2,0, `DataSet` ad alanı aracılığıyla için geliştirilmiş tür desteği getirmiştir  <xref:System.Data.SqlTypes> . İçindeki türler, <xref:System.Data.SqlTypes> bir SQL Server veritabanındaki veri türleriyle aynı semantiğe ve duyarlığa sahip veri türleri sağlamak üzere tasarlanmıştır. İçindeki her veri türü <xref:System.Data.SqlTypes> , aynı temel veri gösterimiyle SQL Server benzer bir veri türüne sahiptir.  
  
 <xref:System.Data.SqlTypes>Doğrudan bir <xref:System.Data.DataSet> yapılandırmalarda kullanmak SQL Server veri türleriyle çalışırken çeşitli avantajlar sağlar. <xref:System.Data.SqlTypes> SQL Server yerel veri türleriyle aynı semantiğini destekler. Öğesinin tanımında birini belirtmek, <xref:System.Data.SqlTypes> <xref:System.Data.DataColumn> ondalık veya sayısal veri türlerini ortak dil çalışma zamanı (CLR) veri türlerinden birine dönüştürürken oluşabilecek duyarlık kaybını ortadan kaldırır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.DataTable> <xref:System.Data.DataColumn> clr türleri yerine kullanarak veri türlerini açıkça tanımlayarak bir nesnesi oluşturur <xref:System.Data.SqlTypes> . Kod, <xref:System.Data.DataTable> SQL Server AdventureWorks veritabanındaki Sales. SalesOrderDetail tablosundan verileri ile doldurur. Konsol penceresinde gösterilen çıktı, her sütunun veri türünü ve SQL Server alınan değerleri gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
