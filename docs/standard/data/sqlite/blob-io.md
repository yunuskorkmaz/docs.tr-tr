---
title: Blob G/Ç
ms.date: 12/08/2020
description: SQLite 'un BLOB g/ç özelliğini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 8b305669f3155d2366215e9a05beb5ed51533d81
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110051"
---
# <a name="blob-io"></a>Blob G/Ç

> [!NOTE]
> SqliteBlob sınıfı 3,0 sürümüne eklenmiştir.

Verilerin veritabanına ve dışına akışını sağlayarak büyük nesneleri okurken ve yazarken bellek kullanımını azaltabilirsiniz. Bu, özellikle verileri ayrıştırırken veya dönüştürürken yararlı olabilir.

Normal olarak bir satır ekleyerek başlayın. `zeroblob()`Büyük nesneyi tutmak üzere veritabanına alan ayırmak için SQL işlevini kullanın. `last_insert_rowid()`İşlevi, roıd 'sini almak için uygun bir yol sağlar.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Satırı ekledikten sonra, kullanarak büyük nesneyi yazmak için bir akış açın <xref:Microsoft.Data.Sqlite.SqliteBlob> .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Büyük nesneyi veritabanından akışa almak için, büyük nesnenin sütununa ek olarak burada gösterildiği gibi ROWID veya diğer adlarının birini seçmeniz gerekir. Roıd ' yi seçmezseniz, tüm nesnenin belleğe yüklenmesi gerekir. Tarafından döndürülen nesne `GetStream()` `SqliteBlob` doğru şekilde tamamlandığında bir olur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
