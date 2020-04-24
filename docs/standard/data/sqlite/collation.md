---
title: Harmanlama
ms.date: 12/13/2019
description: Özel bir harmanlama sırası oluşturmayı öğrenin.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242978"
---
# <a name="collation"></a><span data-ttu-id="4e8f8-103">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="4e8f8-103">Collation</span></span>

<span data-ttu-id="4e8f8-104">Harmanlama dizileri, sıralama ve eşitlik belirlenmesi için metın değerleri karşılaştırılırken SQLite tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="4e8f8-105">SQL sorgularında sütun veya işlem başına oluşturma sırasında hangi harmanlamayı kullanacağınızı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="4e8f8-106">SQLite varsayılan olarak üç harmanlama dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="4e8f8-107">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="4e8f8-107">Collation</span></span> | <span data-ttu-id="4e8f8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e8f8-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="4e8f8-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="4e8f8-109">RTRIM</span></span>     | <span data-ttu-id="4e8f8-110">Sondaki boşluğu yoksayar</span><span class="sxs-lookup"><span data-stu-id="4e8f8-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="4e8f8-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="4e8f8-111">NOCASE</span></span>    | <span data-ttu-id="4e8f8-112">ASCII karakterleri A-Z için büyük/küçük harfe duyarsız</span><span class="sxs-lookup"><span data-stu-id="4e8f8-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="4e8f8-113">Ý</span><span class="sxs-lookup"><span data-stu-id="4e8f8-113">BINARY</span></span>    | <span data-ttu-id="4e8f8-114">Büyük/küçük harfe duyarlı.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-114">Case-sensitive.</span></span> <span data-ttu-id="4e8f8-115">Baytları doğrudan karşılaştırır</span><span class="sxs-lookup"><span data-stu-id="4e8f8-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="4e8f8-116">Özel harmanlama</span><span class="sxs-lookup"><span data-stu-id="4e8f8-116">Custom collation</span></span>

<span data-ttu-id="4e8f8-117">Ayrıca kendi harmanlama dizlerinizi tanımlayabilir veya kullanarak <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>yerleşik olanları geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="4e8f8-118">Aşağıdaki örnekte, Unicode karakterlerini desteklemek için NOCASE harmanlamasının geçersiz kılınması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="4e8f8-119">[Tam örnek kod](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) GitHub ' da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="4e8f8-120">LIKE işleci</span><span class="sxs-lookup"><span data-stu-id="4e8f8-120">Like operator</span></span>

<span data-ttu-id="4e8f8-121">SQLite içindeki LIKE işleci harmanlamaları dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="4e8f8-122">Varsayılan uygulama, NOCASE harmanlamasıyla aynı semantiğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="4e8f8-123">Yalnızca A-Z ASCII karakterleri için büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="4e8f8-124">Aşağıdaki pragma ifadesini kullanarak LIKE işlecinin büyük küçük harfe duyarlı olmasını kolayca sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4e8f8-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="4e8f8-125">LIKE işlecinin uygulanmasını geçersiz kılma hakkında ayrıntılar için [Kullanıcı tanımlı işlevlere](user-defined-functions.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e8f8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e8f8-126">See also</span></span>

* [<span data-ttu-id="4e8f8-127">Kullanıcı tanımlı işlevler</span><span class="sxs-lookup"><span data-stu-id="4e8f8-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="4e8f8-128">SQL Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="4e8f8-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
