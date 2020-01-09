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
# <a name="interoperability"></a>Birlikte Çalışabilirlik

Microsoft. Data. SQLite yerel SQLite kitaplığıyla etkileşmek için SQLitePCLRaw kullanır. SQLitePCLRaw, yerel SQLite API üzerinde bir basit .NET API 'SI sağlar. SqliteConnection ve SqliteDataReader, bu API 'Leri doğrudan çağırmanıza olanak sağlayan temel SQLitePCLRaw nesnelerine erişim sağlar.

Aşağıdaki örnek, yürütülen SQL deyimlerini konsola yazmak için `sqlite3_trace` nasıl çağrılacağını gösterir:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

Aşağıdaki örnekte, bir SQL ifadesinin kaç tane SQLite sanal makine ile derlendiğini görmek için `sqlite3_stmt_status` çağrısı gösterilmektedir:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

SQLitePCLRaw nesneleri, ek yerel SQLite API 'Leri P/Invoke yapmanıza olanak sağlayan yerel nesneler için bir işaretçi da sunar.
