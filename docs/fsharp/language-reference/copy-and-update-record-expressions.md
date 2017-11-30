---
title: "Kopyalama ve güncelleştirme kayıt ifadeleri (F #)"
description: "'Varolan bir kaydı, güncelleştirmelerinin kopyalayan bir kopyalama ve güncelleştirme kayıt ifadesi' alanları belirtilen ve güncelleştirilmiş kaydı döndürür yazma öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="6da88-104">Kopyalama ve güncelleştirme kayıt ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6da88-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="6da88-105">A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanları güncelleştirir ve güncelleştirilmiş kayıt döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6da88-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="6da88-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6da88-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="6da88-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6da88-107">Remarks</span></span>
<span data-ttu-id="6da88-108">Yani hiçbir varolan bir kaydı güncelleştirmeye olası kayıtları varsayılan olarak, değişmez.</span><span class="sxs-lookup"><span data-stu-id="6da88-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="6da88-109">Güncelleştirilmiş bir kaydı bir kaydın tüm alanları oluşturmak için yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6da88-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="6da88-110">Bu görev basitleştirmek için bir *kopyalama ve güncelleştirme kayıt ifade* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6da88-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="6da88-111">Bu ifade varolan bir kaydı alır, ifade belirtilen alanları ve belirtilen ifade tarafından eksik alan kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6da88-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="6da88-112">Varolan bir kaydı kopyalayın ve büyük olasılıkla bazı alan değerlerini değiştirmek varsa, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6da88-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="6da88-113">Örneği için yeni oluşturulan bir kayıt alın.</span><span class="sxs-lookup"><span data-stu-id="6da88-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="6da88-114">Yalnızca o kaydın kullanabileceğiniz alanında bulunan güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="6da88-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="6da88-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6da88-115">See Also</span></span>
[<span data-ttu-id="6da88-116">Kayıtları</span><span class="sxs-lookup"><span data-stu-id="6da88-116">Records</span></span>](records.md)

[<span data-ttu-id="6da88-117">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="6da88-117">F# Language Reference</span></span>](index.md)
