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
# <a name="sqltypes-and-the-dataset"></a>SqlTypes ve DataSet
ADO.NET 2,0, `DataSet` <xref:System.Data.SqlTypes> ad alanı aracılığıyla için geliştirilmiş tür desteği getirmiştir. İçindeki <xref:System.Data.SqlTypes> türler, bir SQL Server veritabanındaki veri türleriyle aynı semantiğe ve duyarlığa sahip veri türleri sağlamak üzere tasarlanmıştır. İçindeki <xref:System.Data.SqlTypes> her veri türü, aynı temel veri gösterimiyle SQL Server benzer bir veri türüne sahiptir.  
  
 Doğrudan <xref:System.Data.SqlTypes> bir<xref:System.Data.DataSet> yapılandırmalarda kullanmak SQL Server veri türleriyle çalışırken çeşitli avantajlar sağlar. <xref:System.Data.SqlTypes>SQL Server yerel veri türleriyle aynı semantiğini destekler. Öğesinin tanımında <xref:System.Data.SqlTypes> <xref:System.Data.DataColumn> birini belirtmek, ondalık veya sayısal veri türlerini ortak dil çalışma zamanı (CLR) veri türlerinden birine dönüştürürken oluşabilecek duyarlık kaybını ortadan kaldırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, clr türleri <xref:System.Data.DataTable> yerine kullanarak <xref:System.Data.DataColumn> <xref:System.Data.SqlTypes> veri türlerini açıkça tanımlayarak bir nesnesi oluşturur. Kod, <xref:System.Data.DataTable> SQL Server AdventureWorks veritabanındaki Sales. SalesOrderDetail tablosundan verileri ile doldurur. Konsol penceresinde gösterilen çıktı, her sütunun veri türünü ve SQL Server alınan değerleri gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
