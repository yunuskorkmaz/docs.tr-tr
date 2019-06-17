---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: "', Mevcut bir kayıt veya anonim kaydı, güncelleştirmeleri kopyalayan bir kopyalama ve güncelleştirme expression' alanları belirtilen ve güncelleştirilmiş kayıt veya anonim bir kayıt döndürür yazmayı öğrenin."
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041734"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="d81db-103">Kayıt İfadelerini Kopyalama ve Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="d81db-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="d81db-104">A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanlarını güncelleştirir ve güncelleştirilen kaydı döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="d81db-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="d81db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d81db-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="d81db-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d81db-106">Remarks</span></span>

<span data-ttu-id="d81db-107">Böylece için varolan bir kaydı güncelleştirme olası, varsayılan olarak ve anonim kayıtlarını sabittir.</span><span class="sxs-lookup"><span data-stu-id="d81db-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="d81db-108">Bir kaydın tüm alanlarını güncelleştirilen bir kaydı oluşturmak için yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d81db-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="d81db-109">Bu görevi kolaylaştırmak amacıyla bir *kopyalama ve güncelleştirme ifade* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d81db-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="d81db-110">Bu ifade, varolan bir kaydı alır, ifade belirtilen alanları ve ifade tarafından belirtilen eksik alan kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d81db-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="d81db-111">Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek varsa, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d81db-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="d81db-112">Örneği için yeni oluşturulan bir kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="d81db-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="d81db-113">Yalnızca kullanabilirsiniz, kayıt alanı üzerinde güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d81db-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="d81db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d81db-114">See also</span></span>

- [<span data-ttu-id="d81db-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="d81db-115">Records</span></span>](records.md)
- [<span data-ttu-id="d81db-116">Anonim kayıtları</span><span class="sxs-lookup"><span data-stu-id="d81db-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="d81db-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d81db-117">F# Language Reference</span></span>](index.md)
