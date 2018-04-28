---
title: 'Kopyalama ve güncelleştirme kayıt ifadeleri (F #)'
description: "'Varolan bir kaydı, güncelleştirmelerinin kopyalayan bir kopyalama ve güncelleştirme kayıt ifadesi' alanları belirtilen ve güncelleştirilmiş kaydı döndürür yazma öğrenin."
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 98a515b5f053e9339588157185848e8315a580f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="3c2ee-103">Kopyalama ve güncelleştirme kayıt ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3c2ee-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="3c2ee-104">A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanları güncelleştirir ve güncelleştirilmiş kayıt döndüren bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="3c2ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c2ee-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="3c2ee-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c2ee-106">Remarks</span></span>
<span data-ttu-id="3c2ee-107">Yani hiçbir varolan bir kaydı güncelleştirmeye olası kayıtları varsayılan olarak, değişmez.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="3c2ee-108">Güncelleştirilmiş bir kaydı bir kaydın tüm alanları oluşturmak için yeniden belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="3c2ee-109">Bu görev basitleştirmek için bir *kopyalama ve güncelleştirme kayıt ifade* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="3c2ee-110">Bu ifade varolan bir kaydı alır, ifade belirtilen alanları ve belirtilen ifade tarafından eksik alan kullanarak aynı türde yeni bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="3c2ee-111">Varolan bir kaydı kopyalayın ve büyük olasılıkla bazı alan değerlerini değiştirmek varsa, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="3c2ee-112">Örneği için yeni oluşturulan bir kayıt alın.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="3c2ee-113">Yalnızca o kaydın kullanabileceğiniz alanında bulunan güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="3c2ee-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="3c2ee-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c2ee-114">See Also</span></span>
[<span data-ttu-id="3c2ee-115">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="3c2ee-115">Records</span></span>](records.md)

[<span data-ttu-id="3c2ee-116">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c2ee-116">F# Language Reference</span></span>](index.md)
