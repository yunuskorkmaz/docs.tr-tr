---
title: Blob g/ç
ms.date: 12/13/2019
description: SQLite 'un BLOB g/ç özelliğini nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447050"
---
# <a name="blob-io"></a><span data-ttu-id="59338-103">Blob g/ç</span><span class="sxs-lookup"><span data-stu-id="59338-103">Blob I/O</span></span>

<span data-ttu-id="59338-104">Verilerin veritabanına ve dışına akışını sağlayarak büyük nesneleri okurken ve yazarken bellek kullanımını azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59338-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="59338-105">Bu, özellikle verileri ayrıştırırken veya dönüştürürken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="59338-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="59338-106">Normal olarak bir satır ekleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="59338-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="59338-107">Büyük nesneyi tutmak üzere veritabanına alan ayırmak için `zeroblob()` SQL işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="59338-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="59338-108">`last_insert_rowid()` işlevi, roıd 'sini almak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="59338-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="59338-109">Satırı ekledikten sonra, <xref:Microsoft.Data.Sqlite.SqliteBlob>kullanarak büyük nesneyi yazmak için bir akış açın.</span><span class="sxs-lookup"><span data-stu-id="59338-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="59338-110">Büyük nesneyi veritabanından akışa almak için, büyük nesnenin sütununa ek olarak burada gösterildiği gibi ROWID veya diğer adlarının birini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59338-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="59338-111">Roıd ' yi seçmezseniz, tüm nesnenin belleğe yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="59338-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="59338-112">`GetStream()` tarafından döndürülen nesne doğru şekilde tamamlandığında `SqliteBlob` olur.</span><span class="sxs-lookup"><span data-stu-id="59338-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
