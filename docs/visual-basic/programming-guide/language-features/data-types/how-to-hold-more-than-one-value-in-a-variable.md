---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir değişkende birden fazla değer tutma (Visual Basic)'
title: 'Nasıl yapılır: Değişkende Birden Fazla Değer Tutma'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 5248bc29f58cccf3b8ced95d3fba8f0d39033a83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484008"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="963cc-103">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="963cc-103">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="963cc-104">Bir değişken, *bileşik veri türünde* olduğunu bildirirseniz birden fazla değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="963cc-104">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="963cc-105">[Bileşik veri türleri](composite-data-types.md) yapılar, diziler ve sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="963cc-105">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="963cc-106">Bileşik veri türünün bir değişkeni, Öğesel veri türlerinin ve diğer bileşik türlerin bir birleşimini tutabilir.</span><span class="sxs-lookup"><span data-stu-id="963cc-106">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="963cc-107">Yapılar ve sınıflar, kodu ve verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="963cc-107">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="963cc-108">Bir değişkende birden fazla değeri tutmak için</span><span class="sxs-lookup"><span data-stu-id="963cc-108">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="963cc-109">Değişkeniniz için kullanmak istediğiniz bileşik veri türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="963cc-109">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="963cc-110">Bileşik veri türü önceden tanımlanmamışsa, değişkeninizin onu kullanabilmesi için onu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="963cc-110">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="963cc-111">[Structure ifadesiyle](../../../language-reference/statements/structure-statement.md)bir yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="963cc-111">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="963cc-112">[Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir dizi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="963cc-112">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="963cc-113">[Sınıf ifadesiyle](../../../language-reference/statements/class-statement.md)bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="963cc-113">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="963cc-114">Değişkeninizi bir ifadesiyle bildirin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="963cc-114">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="963cc-115">Bir yan tümcesiyle değişken adını izleyin `As` .</span><span class="sxs-lookup"><span data-stu-id="963cc-115">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="963cc-116">`As`Uygun bileşik veri türünün adı ile anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="963cc-116">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="963cc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="963cc-117">See also</span></span>

- [<span data-ttu-id="963cc-118">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="963cc-118">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="963cc-119">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="963cc-119">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="963cc-120">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="963cc-120">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="963cc-121">Yapılar</span><span class="sxs-lookup"><span data-stu-id="963cc-121">Structures</span></span>](structures.md)
- [<span data-ttu-id="963cc-122">Diziler</span><span class="sxs-lookup"><span data-stu-id="963cc-122">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="963cc-123">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="963cc-123">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="963cc-124">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="963cc-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
