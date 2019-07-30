---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: Varolan bir kaydı veya anonim kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilmiş kaydı veya anonim kaydı döndüren ' kopyalama ve güncelleştirme ifadesi ' yazmayı öğrenin.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630385"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="9e681-103">Kayıt İfadelerini Kopyalama ve Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="9e681-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="9e681-104">Bir *kopyalama ve güncelleştirme kaydı ifadesi* , var olan bir kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilmiş kaydı döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="9e681-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e681-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e681-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="9e681-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e681-106">Remarks</span></span>

<span data-ttu-id="9e681-107">Kayıtlar ve anonim kayıtlar varsayılan olarak sabittir, böylece var olan bir kayda yönelik bir güncelleştirme yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e681-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="9e681-108">Güncelleştirilmiş bir kayıt oluşturmak için bir kaydın tüm alanlarının yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e681-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="9e681-109">Bu görevi basitleştirmek için, bir *kopyalama ve güncelleştirme ifadesi* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e681-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="9e681-110">Bu ifade mevcut bir kaydı alır, ifadeden belirtilen alanları ve ifade tarafından belirtilen eksik alanı kullanarak aynı türden yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e681-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="9e681-111">Bu, var olan bir kaydı kopyalamanız ve muhtemelen alan değerlerinden bazılarını değiştirmeniz gerektiğinde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e681-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="9e681-112">Yeni oluşturulan bir kayıt örneğini alın.</span><span class="sxs-lookup"><span data-stu-id="9e681-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="9e681-113">Yalnızca söz konusu kayıt alanında güncelleştirme yaptıysanız, aşağıdaki gibi *kopyalama ve güncelleştirme kayıt ifadesini* kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e681-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="9e681-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e681-114">See also</span></span>

- [<span data-ttu-id="9e681-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="9e681-115">Records</span></span>](records.md)
- [<span data-ttu-id="9e681-116">Anonim kayıtlar</span><span class="sxs-lookup"><span data-stu-id="9e681-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="9e681-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e681-117">F# Language Reference</span></span>](index.md)
