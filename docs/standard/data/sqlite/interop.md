---
title: Birlikte Çalışabilirlik
ms.date: 12/13/2019
description: Diğer SQLite kitaplıklarıyla birlikte çalışma hakkında bilgi edinin.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447239"
---
# <a name="interoperability"></a><span data-ttu-id="ac9ce-103">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ac9ce-103">Interoperability</span></span>

<span data-ttu-id="ac9ce-104">Microsoft. Data. SQLite yerel SQLite kitaplığıyla etkileşmek için SQLitePCLRaw kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac9ce-104">Microsoft.Data.Sqlite uses SQLitePCLRaw to interact with the native SQLite library.</span></span> <span data-ttu-id="ac9ce-105">SQLitePCLRaw, yerel SQLite API üzerinde bir basit .NET API 'SI sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac9ce-105">SQLitePCLRaw provides a thin .NET API over the native SQLite API.</span></span> <span data-ttu-id="ac9ce-106">SqliteConnection ve SqliteDataReader, bu API 'Leri doğrudan çağırmanıza olanak sağlayan temel SQLitePCLRaw nesnelerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac9ce-106">SqliteConnection and SqliteDataReader provide access to the underlying SQLitePCLRaw objects letting you call these APIs directly.</span></span>

<span data-ttu-id="ac9ce-107">Aşağıdaki örnek, yürütülen SQL deyimlerini konsola yazmak için `sqlite3_trace` nasıl çağrılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ac9ce-107">The following example shows how to call `sqlite3_trace` to write executed SQL statements to the console:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

<span data-ttu-id="ac9ce-108">Aşağıdaki örnekte, bir SQL ifadesinin kaç tane SQLite sanal makine ile derlendiğini görmek için `sqlite3_stmt_status` çağrısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ac9ce-108">And the following example shows calling `sqlite3_stmt_status` to see how many SQLite virtual machine steps a SQL statement compiled into:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

<span data-ttu-id="ac9ce-109">SQLitePCLRaw nesneleri, ek yerel SQLite API 'Leri P/Invoke yapmanıza olanak sağlayan yerel nesneler için bir işaretçi da sunar.</span><span class="sxs-lookup"><span data-stu-id="ac9ce-109">The SQLitePCLRaw objects even expose a pointer to the native objects letting you P/Invoke additional native SQLite APIs.</span></span>
