---
title: 'Nasıl yapılır: Değişkende birden çok değer tut (Visual Basic)'
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054192"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="447cf-102">Nasıl yapılır: Değişkende birden çok değer tut (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="447cf-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="447cf-103">Bir değişken, *bileşik veri türünde*olduğunu bildirirseniz birden fazla değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="447cf-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="447cf-104">[Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) yapılar, diziler ve sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="447cf-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="447cf-105">Bileşik veri türünün bir değişkeni, Öğesel veri türlerinin ve diğer bileşik türlerin bir birleşimini tutabilir.</span><span class="sxs-lookup"><span data-stu-id="447cf-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="447cf-106">Yapılar ve sınıflar, kodu ve verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="447cf-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="447cf-107">Bir değişkende birden fazla değeri tutmak için</span><span class="sxs-lookup"><span data-stu-id="447cf-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="447cf-108">Değişkeniniz için kullanmak istediğiniz bileşik veri türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="447cf-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="447cf-109">Bileşik veri türü önceden tanımlanmamışsa, değişkeninizin onu kullanabilmesi için onu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="447cf-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="447cf-110">[Structure ifadesiyle](../../../../visual-basic/language-reference/statements/structure-statement.md)bir yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="447cf-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="447cf-111">[Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir dizi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="447cf-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="447cf-112">[Sınıf ifadesiyle](../../../../visual-basic/language-reference/statements/class-statement.md)bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="447cf-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="447cf-113">Değişkeninizi bir `Dim` ifadesiyle bildirin.</span><span class="sxs-lookup"><span data-stu-id="447cf-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="447cf-114">Bir `As` yan tümcesiyle değişken adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="447cf-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="447cf-115">Uygun bileşik veri türünün adı ile anahtarsözcüğünüizleyin.`As`</span><span class="sxs-lookup"><span data-stu-id="447cf-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="447cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="447cf-116">See also</span></span>

- [<span data-ttu-id="447cf-117">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="447cf-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="447cf-118">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="447cf-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="447cf-119">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="447cf-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="447cf-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="447cf-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="447cf-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="447cf-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="447cf-122">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="447cf-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="447cf-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="447cf-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
