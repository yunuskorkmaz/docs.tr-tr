---
title: "DataTable şema tanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: be5969bf8653512da27785479ac7feae1f6c09a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-schema-definition"></a>DataTable şema tanımı
Sütunları ve kısıtlamalar tarafından kullanılacak şema veya bir tablonun yapısını temsil edilir. Şemasını tanımlayan bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataColumn> nesneleri yanı <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri. Bir tablodaki sütun bir veri kaynağındaki sütunları eşlemek, ifadeler hesaplanan değerler içeren, otomatik olarak değerlerine artırın veya birincil anahtar değerlerini içeriyor.  
  
 Sütunları, ilişkileri ve kısıtlamaları bir tabloda ada göre başvurular büyük/küçük harfe duyarlıdır. Bu nedenle iki veya daha fazla sütun, ilişkileri veya kısıtlamaları aynı ada sahip, ancak bu durumda farklı bir tabloda bulunabilir. Örneğin, sahip **Col1** ve **col1**. İçinde durumda gibi ada göre sütunlardan biri için bir başvuru sütun adı durumunun tam olarak eşleşmelidir; Aksi takdirde özel durum oluşur. Örneğin, varsa tablonun **myTable** sütunları içeren **Col1** ve **col1**, başvuru **Col1** ada göre  **myTable.Columns["Col1"]**, ve **col1** olarak **myTable.Columns["col1"]**. Ya da sütun olarak başvuru girişimi **myTable.Columns["COL1"]** bir özel durum oluşturur.  
  
 Yalnızca bir sütun, ilişki veya belirli bir ad ile kısıtlaması varsa büyük küçük harf duyarlılığı kuralı geçerli değildir. Diğer bir deyişle, diğer hiçbir sütun, ilişki veya tablosundaki kısıtlama nesnesi bu belirli sütun, ilişki veya kısıtlama nesnesi adı eşleşirse, herhangi bir durumu kullanarak adıyla nesne başvurusundan ve hiçbir özel durum oluşur. Örneğin, tablo yalnızca varsa **Col1**, kullanarak başvuru **my. Sütunlar ["COL1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Özelliği **DataTable** bu davranışını etkilemez. **CaseSensitive** özelliği, bir tablo ve kısıtlamalar ve benzeri zorlamayı sıralama, filtreleme, aramayı etkiler veriler, ancak sütun, ilişkileri ve kısıtlamaları başvuruları uygulanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataTable tablosuna sütun ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Kullanarak bir tablo sütunları tanımlamak açıklar **DataColumn** nesneleri.  
  
 [İfade sütunları oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Açıklar nasıl **ifade** bir sütunun özelliği, satırda başka sütunlardan değerlere göre değerleri hesaplamak için kullanılabilir.  
  
 [AutoIncrement sütunlar oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Sayısal değerler, satır başına bir benzersiz sütun değeri sağlamak için otomatik olarak artırmak için bir sütun nasıl ayarlanabilir açıklar.  
  
 [Birincil anahtarlar tanımlama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Bir veya daha fazla bir tablonun birincil anahtarı belirtmek açıklar **DataColumn** nesneleri.  
  
 [DataTable kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Yabancı anahtar ve benzersiz kısıtlamalar sütunlar için bir tabloda nasıl tanımlanacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
