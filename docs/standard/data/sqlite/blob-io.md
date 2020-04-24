---
title: Blob G/Ç
ms.date: 12/13/2019
description: SQLite 'un BLOB g/ç özelliğini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447050"
---
# <a name="blob-io"></a>Blob G/Ç

Verilerin veritabanına ve dışına akışını sağlayarak büyük nesneleri okurken ve yazarken bellek kullanımını azaltabilirsiniz. Bu, özellikle verileri ayrıştırırken veya dönüştürürken yararlı olabilir.

Normal olarak bir satır ekleyerek başlayın. Büyük nesneyi `zeroblob()` tutmak üzere veritabanına alan ayırmak için SQL işlevini kullanın. İşlevi `last_insert_rowid()` , roıd 'sini almak için uygun bir yol sağlar.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Satırı ekledikten sonra, kullanarak <xref:Microsoft.Data.Sqlite.SqliteBlob>büyük nesneyi yazmak için bir akış açın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Büyük nesneyi veritabanından akışa almak için, büyük nesnenin sütununa ek olarak burada gösterildiği gibi ROWID veya diğer adlarının birini seçmeniz gerekir. Roıd ' yi seçmezseniz, tüm nesnenin belleğe yüklenmesi gerekir. Tarafından `GetStream()` döndürülen nesne doğru şekilde tamamlandığında bir `SqliteBlob` olur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
