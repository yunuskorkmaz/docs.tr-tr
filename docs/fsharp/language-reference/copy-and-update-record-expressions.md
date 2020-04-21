---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: Varolan bir kaydı veya anonim kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilen kaydı veya anonim kaydı döndüren bir 'kopyalama ve güncelleştirme ifadesini' nasıl yazacağız öğrenin.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739281"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="0dd60-103">Kayıt İfadelerini Kopyalama ve Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="0dd60-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="0dd60-104">*Kayıt ifadesini kopyala ve güncelleştir,* varolan bir kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilen kaydı döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0dd60-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="0dd60-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dd60-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="0dd60-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dd60-106">Remarks</span></span>

<span data-ttu-id="0dd60-107">Kayıtlar ve anonim kayıtlar varsayılan olarak değişmez olduğundan, varolan bir kaydı güncelleştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0dd60-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="0dd60-108">Güncelleştirilmiş bir kayıt oluşturmak için bir kaydın tüm alanlarının yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dd60-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="0dd60-109">Bu görevi basitleştirmek için bir *kopyalama ve güncelleştirme ifadesi* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dd60-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="0dd60-110">Bu ifade varolan bir kaydı alır, ifade ve ifade tarafından belirtilen eksik alandan belirtilen alanları kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0dd60-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="0dd60-111">Bu, varolan bir kaydı kopyalamanız ve büyük olasılıkla bazı alan değerlerini değiştirmeniz gerektiğinde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0dd60-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="0dd60-112">Örneğin yeni oluşturulan bir kaydı ele alalım.</span><span class="sxs-lookup"><span data-stu-id="0dd60-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="0dd60-113">Bu kayıtta yalnızca iki alanı güncelleştirmek için *kopyala ve güncelleştir kaydı ifadesini*kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0dd60-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="0dd60-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd60-114">See also</span></span>

- [<span data-ttu-id="0dd60-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="0dd60-115">Records</span></span>](records.md)
- [<span data-ttu-id="0dd60-116">Anonim Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="0dd60-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="0dd60-117">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="0dd60-117">F# Language Reference</span></span>](index.md)
