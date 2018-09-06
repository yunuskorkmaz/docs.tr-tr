---
title: 'Kopyalama ve güncelleştirme kayıt ifadeleri (F #)'
description: "'Var olan bir kaydı, güncelleştirmeleri kopyalayan bir kopyalama ve güncelleştirme kayıt expression' alanları belirtilen ve güncelleştirilen bir kaydı döndürür yazmayı öğrenin."
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892275"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="6e785-103">Kopyalama ve güncelleştirme kayıt ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6e785-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="6e785-104">A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanlarını güncelleştirir ve güncelleştirilen kaydı döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6e785-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e785-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e785-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="6e785-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e785-106">Remarks</span></span>

<span data-ttu-id="6e785-107">Böylece için varolan bir kaydı güncelleştirme olası varsayılan olarak, kayıt sabittir.</span><span class="sxs-lookup"><span data-stu-id="6e785-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="6e785-108">Bir kaydın tüm alanlarını güncelleştirilen bir kaydı oluşturmak için yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e785-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="6e785-109">Bu görevi kolaylaştırmak amacıyla bir *kopyalama ve güncelleştirme kayıt ifade* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e785-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="6e785-110">Bu ifade, varolan bir kaydı alır, ifade belirtilen alanları ve ifade tarafından belirtilen eksik alan kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e785-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="6e785-111">Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek varsa, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e785-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="6e785-112">Örneği için yeni oluşturulan bir kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="6e785-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="6e785-113">Yalnızca kullanabilirsiniz, kayıt alanı üzerinde güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6e785-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="6e785-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e785-114">See also</span></span>

- [<span data-ttu-id="6e785-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="6e785-115">Records</span></span>](records.md)
- [<span data-ttu-id="6e785-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6e785-116">F# Language Reference</span></span>](index.md)
