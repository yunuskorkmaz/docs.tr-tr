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
# <a name="blob-io"></a><span data-ttu-id="f3471-103">Blob G/Ç</span><span class="sxs-lookup"><span data-stu-id="f3471-103">Blob I/O</span></span>

> [!NOTE]
> <span data-ttu-id="f3471-104">SqliteBlob sınıfı 3,0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f3471-104">The SqliteBlob class was added in version 3.0.</span></span>

<span data-ttu-id="f3471-105">Verilerin veritabanına ve dışına akışını sağlayarak büyük nesneleri okurken ve yazarken bellek kullanımını azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3471-105">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="f3471-106">Bu, özellikle verileri ayrıştırırken veya dönüştürürken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3471-106">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="f3471-107">Normal olarak bir satır ekleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="f3471-107">Start by inserting a row as normal.</span></span> <span data-ttu-id="f3471-108">`zeroblob()`Büyük nesneyi tutmak üzere veritabanına alan ayırmak için SQL işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3471-108">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="f3471-109">`last_insert_rowid()`İşlevi, roıd 'sini almak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3471-109">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="f3471-110">Satırı ekledikten sonra, kullanarak büyük nesneyi yazmak için bir akış açın <xref:Microsoft.Data.Sqlite.SqliteBlob> .</span><span class="sxs-lookup"><span data-stu-id="f3471-110">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="f3471-111">Büyük nesneyi veritabanından akışa almak için, büyük nesnenin sütununa ek olarak burada gösterildiği gibi ROWID veya diğer adlarının birini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3471-111">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="f3471-112">Roıd ' yi seçmezseniz, tüm nesnenin belleğe yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3471-112">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="f3471-113">Tarafından döndürülen nesne `GetStream()` `SqliteBlob` doğru şekilde tamamlandığında bir olur.</span><span class="sxs-lookup"><span data-stu-id="f3471-113">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
