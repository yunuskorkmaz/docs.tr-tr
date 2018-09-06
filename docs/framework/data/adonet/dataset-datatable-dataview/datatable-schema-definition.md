---
title: DataTable şema tanımı
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 60e7f6a13bd7fd10398d300690bd73c3abc0d700
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748865"
---
# <a name="datatable-schema-definition"></a>DataTable şema tanımı
Şema veya bir tablonun yapısını, sütunları ve kısıtlamaları tarafından temsil edilir. Şemasını tanımlayan bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataColumn> nesneleri olarak <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri. Bir tablodaki sütunları bir veri kaynağındaki sütun eşleme, ifadeleri hesaplanan değerleri içeren, otomatik olarak değerlerini artırın veya birincil anahtar değerlerini içerir.  
  
 Sütunlar, ilişkiler ve kısıtlamalar bir tablodaki adına göre başvuruları büyük/küçük harfe duyarlıdır. Bu nedenle iki veya daha fazla sütun, ilişkileri veya kısıtlamaları, aynı ada sahip, ancak bu durumda farklı bir tabloda bulunabilir. Örneğin, sahip **Col1** ve **col1**. İçinde çalışması gibi bir başvuru adına göre sütunlarından biri için sütun adı harf tam olarak eşleşmelidir; Aksi takdirde, bir özel durum oluşturulur. Örneğin, varsa tablonun **myTable** sütunları içeren **Col1** ve **col1**, başvuru **Col1** ada göre  **myTable.Columns["Col1"]**, ve **col1** olarak **myTable.Columns["col1"]**. Sütun ya da başvuru girişimi **myTable.Columns["COL1"]** bir özel durum oluşturur.  
  
 Yalnızca bir sütun, ilişki veya belirli bir ada sahip kısıtlaması varsa, büyük küçük harf duyarlılığı kuralı uygulanmaz. Diğer bir deyişle, diğer hiçbir sütun, ilişki veya tabloda kısıtlama nesnesi, belirli bir sütun, ilişki veya kısıtlama nesnesi adıyla eşleşen nesne adına göre herhangi bir durumu kullanarak başvurabilir ve hiçbir özel durum. Örneğin, tablonun yalnızca varsa **Col1**, kullanarak başvurabilirsiniz **benim. Sütunlar ["COL1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Özelliği **DataTable** bu davranışı etkilemez. **CaseSensitive** özelliği, verileri bir tablo ve kısıtlamalar ve benzeri zorlamayı sıralama, arama, filtreleme, etkiler, ancak başvurularını sütunlar, ilişkiler ve kısıtlamalar uygulanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataTable’a Sütun Ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Kullanarak bir tablo sütunları tanımlamayı açıklar **DataColumn** nesneleri.  
  
 [İfade Sütunları Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Açıklayan nasıl **ifade** özelliği sütunun değerlerini satırdaki diğer sütunlardan değerlere göre hesaplamak için kullanılabilir.  
  
 [AutoIncrement Sütunları Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Satır başına bir benzersiz sütun değeri sağlamak için sayısal değerler otomatik olarak artırmak için bir sütun nasıl ayarlanabilir açıklar.  
  
 [Birincil Anahtarlar Tanımlama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 En az bir tablonun birincil anahtarı belirtmek açıklar **DataColumn** nesneleri.  
  
 [DataTable Kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Bir tablodaki sütunları benzersiz kısıtlamaları ve yabancı anahtar tanımlamayı açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
