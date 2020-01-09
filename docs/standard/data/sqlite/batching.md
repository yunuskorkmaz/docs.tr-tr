---
title: Toplu işleme
ms.date: 12/13/2019
description: Tek bir komutta SQL deyimlerinin bir toplu işini yürütmeyi öğrenin.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447057"
---
# <a name="batching"></a><span data-ttu-id="5012d-103">Toplu işleme</span><span class="sxs-lookup"><span data-stu-id="5012d-103">Batching</span></span>

<span data-ttu-id="5012d-104">SQLite, toplu işlem SQL deyimlerini tek bir komutta birlikte yerel olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5012d-104">SQLite doesn't natively support batching SQL statements together into a single command.</span></span> <span data-ttu-id="5012d-105">Ancak ilgili bir ağ olmadığından, yine de performansa gerçekten yardımcı olmaz.</span><span class="sxs-lookup"><span data-stu-id="5012d-105">But because there's no network involved, it wouldn't really help performance anyway.</span></span> <span data-ttu-id="5012d-106">Ancak Microsoft. Data. SQLite, diğer ADO.NET sağlayıcıları gibi davranması için bir kolaylık olarak deyimin toplu işleme uygulamasını uygular.</span><span class="sxs-lookup"><span data-stu-id="5012d-106">Microsoft.Data.Sqlite does, however, implement statement batching as a convenience to make it behave more like other ADO.NET providers.</span></span>

<span data-ttu-id="5012d-107"><xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>çağrılırken, deyimler sonuçları döndüren ilk birine yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5012d-107">When calling <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, statements are executed up to the first one that returns results.</span></span> <span data-ttu-id="5012d-108"><xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> çağırmak, sonuçları döndürene veya toplu işlemin sonuna gelene kadar deyimleri yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="5012d-108">Calling <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continues executing statements until the next one that returns results or until it reaches the end of the batch.</span></span> <span data-ttu-id="5012d-109"><xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> veya <xref:System.Data.Common.DbDataReader.Close%2A> çağırmak `NextResult()`tarafından kullanılmayan kalan deyimleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="5012d-109">Calling <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> or <xref:System.Data.Common.DbDataReader.Close%2A> executes any remaining statements that haven't been consumed by `NextResult()`.</span></span> <span data-ttu-id="5012d-110">Bir veri okuyucusunu atlamazsanız, Sonlandırıcı kalan deyimleri yürütmeye çalışır, ancak karşılaştığı hatalar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5012d-110">If you don't dispose a data reader, the finalizer tries to execute the remaining statements, but any errors it encounters are ignored.</span></span> <span data-ttu-id="5012d-111">Bu nedenle, toplu işlemler kullanılırken `DbDataReader` nesneleri atmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5012d-111">Because of this, it's important to dispose `DbDataReader` objects when using batches.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a><span data-ttu-id="5012d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5012d-112">See also</span></span>

* [<span data-ttu-id="5012d-113">Toplu ekleme</span><span class="sxs-lookup"><span data-stu-id="5012d-113">Bulk Insert</span></span>](bulk-insert.md)
