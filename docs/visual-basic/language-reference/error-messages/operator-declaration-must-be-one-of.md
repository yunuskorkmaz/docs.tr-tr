---
description: 'Hakkında daha fazla bilgi edinin: BC33000: Işleç bildirimi şunlardan biri olmalıdır: +,-, *,,/, ^, &amp; , LIKE, mod, and, or, XOR, Not,  <<,  >>...'
title: 'İşleç bildirimi şunlardan biri olmalıdır: +,-, *,-,-, ^, &amp; , LIKE, mod, and, or, XOR, Not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 0ad82a6414387278622a10624952ebc35e7e9b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795566"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="24126-103">BC33000: işleç bildirimi şunlardan biri olmalıdır: +,-, \*, \, /, ^, &amp; , LIKE, mod, and, or, XOR, Not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="24126-103">BC33000: Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="24126-104">Yalnızca aşırı yükleme için uygun bir işleç bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24126-104">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="24126-105">Aşağıdaki tabloda, bildirebilmeniz için kullanabileceğiniz işleçler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="24126-105">The following table lists the operators you can declare.</span></span>

|<span data-ttu-id="24126-106">Tür</span><span class="sxs-lookup"><span data-stu-id="24126-106">Type</span></span>|<span data-ttu-id="24126-107">İşleçler</span><span class="sxs-lookup"><span data-stu-id="24126-107">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="24126-108">Birli</span><span class="sxs-lookup"><span data-stu-id="24126-108">Unary</span></span>|<span data-ttu-id="24126-109">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="24126-109">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="24126-110">İkili</span><span class="sxs-lookup"><span data-stu-id="24126-110">Binary</span></span>|<span data-ttu-id="24126-111">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="24126-111">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="24126-112">Dönüştürme (birli)</span><span class="sxs-lookup"><span data-stu-id="24126-112">Conversion (unary)</span></span>|`CType`|

 <span data-ttu-id="24126-113">`=`İkili listedeki işlecin atama işleci değil karşılaştırma operatörü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24126-113">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="24126-114">**Hata kimliği:** BC33000</span><span class="sxs-lookup"><span data-stu-id="24126-114">**Error ID:** BC33000</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="24126-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="24126-115">To correct this error</span></span>

- <span data-ttu-id="24126-116">Fazla yüklenebilir işleçler kümesinden bir işleç seçin.</span><span class="sxs-lookup"><span data-stu-id="24126-116">Select an operator from the set of overloadable operators.</span></span>

- <span data-ttu-id="24126-117">Doğrudan aşırı yükleyemez olmayan bir işleci aşırı yükleme işlevselliğine ihtiyacınız varsa, `Function` uygun parametreleri alan ve uygun değeri döndüren bir yordam oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24126-117">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>

## <a name="see-also"></a><span data-ttu-id="24126-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24126-118">See also</span></span>

- [<span data-ttu-id="24126-119">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="24126-119">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="24126-120">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="24126-120">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="24126-121">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="24126-121">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="24126-122">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="24126-122">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="24126-123">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="24126-123">Function Statement</span></span>](../statements/function-statement.md)
