---
title: Kopyalama ve güncelleştirme kayıt ifadeleri
description: "'Var olan bir kaydı, güncelleştirmeleri kopyalayan bir kopyalama ve güncelleştirme kayıt expression' alanları belirtilen ve güncelleştirilen bir kaydı döndürür yazmayı öğrenin."
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 5f9b13ebf6c456aff73872b7522d7670c068dd88
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613316"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="c7767-103">Kopyalama ve güncelleştirme kayıt ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c7767-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="c7767-104">A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanlarını güncelleştirir ve güncelleştirilen kaydı döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="c7767-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7767-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7767-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="c7767-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7767-106">Remarks</span></span>

<span data-ttu-id="c7767-107">Böylece için varolan bir kaydı güncelleştirme olası varsayılan olarak, kayıt sabittir.</span><span class="sxs-lookup"><span data-stu-id="c7767-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="c7767-108">Bir kaydın tüm alanlarını güncelleştirilen bir kaydı oluşturmak için yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7767-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="c7767-109">Bu görevi kolaylaştırmak amacıyla bir *kopyalama ve güncelleştirme kayıt ifade* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7767-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="c7767-110">Bu ifade, varolan bir kaydı alır, ifade belirtilen alanları ve ifade tarafından belirtilen eksik alan kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7767-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="c7767-111">Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek varsa, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7767-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="c7767-112">Örneği için yeni oluşturulan bir kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="c7767-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="c7767-113">Yalnızca kullanabilirsiniz, kayıt alanı üzerinde güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c7767-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="c7767-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7767-114">See also</span></span>

- [<span data-ttu-id="c7767-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="c7767-115">Records</span></span>](records.md)
- [<span data-ttu-id="c7767-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c7767-116">F# Language Reference</span></span>](index.md)