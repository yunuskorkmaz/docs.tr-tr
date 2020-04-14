---
title: Harmanlama
ms.date: 12/13/2019
description: Özel bir harmanlama dizisi oluşturmayı öğrenin.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242978"
---
# <a name="collation"></a><span data-ttu-id="fb26e-103">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="fb26e-103">Collation</span></span>

<span data-ttu-id="fb26e-104">Dizileri harmanlama, düzen ve eşitliği belirlemek için TEXT değerlerini karşılaştırırken SQLite tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb26e-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="fb26e-105">SQL sorgularında sütun oluştururken veya işlem başına kullanırken hangi harmanlamanın kullanılacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb26e-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="fb26e-106">SQLite varsayılan olarak üç harmanlama dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="fb26e-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="fb26e-107">Harmanlama</span><span class="sxs-lookup"><span data-stu-id="fb26e-107">Collation</span></span> | <span data-ttu-id="fb26e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb26e-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="fb26e-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="fb26e-109">RTRIM</span></span>     | <span data-ttu-id="fb26e-110">Sondaki beyaz boşluğu yok sayar</span><span class="sxs-lookup"><span data-stu-id="fb26e-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="fb26e-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="fb26e-111">NOCASE</span></span>    | <span data-ttu-id="fb26e-112">ASCII karakterleri a-z için büyük/küçük harf duyarsız</span><span class="sxs-lookup"><span data-stu-id="fb26e-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="fb26e-113">Ikili</span><span class="sxs-lookup"><span data-stu-id="fb26e-113">BINARY</span></span>    | <span data-ttu-id="fb26e-114">Duyarlı.</span><span class="sxs-lookup"><span data-stu-id="fb26e-114">Case-sensitive.</span></span> <span data-ttu-id="fb26e-115">Baytları doğrudan karşılaştırır</span><span class="sxs-lookup"><span data-stu-id="fb26e-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="fb26e-116">Özel harmanlama</span><span class="sxs-lookup"><span data-stu-id="fb26e-116">Custom collation</span></span>

<span data-ttu-id="fb26e-117">Ayrıca kendi harmanlama dizilerinizi tanımlayabilir veya yerleşik sekanları <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb26e-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="fb26e-118">Aşağıdaki örnek, Unicode karakterlerini desteklemek için NOCASE harmanlama geçersiz kılınan gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb26e-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="fb26e-119">[Tam örnek kodu](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) GitHub'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb26e-119">The [full sample code](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="fb26e-120">Operatör gibi</span><span class="sxs-lookup"><span data-stu-id="fb26e-120">Like operator</span></span>

<span data-ttu-id="fb26e-121">SQLite LIKE operatör collations onurlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="fb26e-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="fb26e-122">Varsayılan uygulama NOCASE harmanlama aynı semantik vardır.</span><span class="sxs-lookup"><span data-stu-id="fb26e-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="fb26e-123">A'dan Z'ye KADAR ASCII karakterleri için sadece büyük bir duyarsızlık.</span><span class="sxs-lookup"><span data-stu-id="fb26e-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="fb26e-124">Aşağıdaki pragma deyimini kullanarak LIKE işleci kılıfını kolayca hassas hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fb26e-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="fb26e-125">LIKE işlecinin uygulanmasını geçersiz kılmayla ilgili ayrıntılar için [Kullanıcı tanımlı işlevlere](user-defined-functions.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="fb26e-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb26e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb26e-126">See also</span></span>

* [<span data-ttu-id="fb26e-127">Kullanıcı tanımlı işlevler</span><span class="sxs-lookup"><span data-stu-id="fb26e-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="fb26e-128">SQL Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="fb26e-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
