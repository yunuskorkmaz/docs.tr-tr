---
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
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393902"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="edd7c-102">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edd7c-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="edd7c-103">Bir değişken, *bileşik veri türünde*olduğunu bildirirseniz birden fazla değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="edd7c-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="edd7c-104">[Bileşik veri türleri](composite-data-types.md) yapılar, diziler ve sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="edd7c-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="edd7c-105">Bileşik veri türünün bir değişkeni, Öğesel veri türlerinin ve diğer bileşik türlerin bir birleşimini tutabilir.</span><span class="sxs-lookup"><span data-stu-id="edd7c-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="edd7c-106">Yapılar ve sınıflar, kodu ve verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="edd7c-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="edd7c-107">Bir değişkende birden fazla değeri tutmak için</span><span class="sxs-lookup"><span data-stu-id="edd7c-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="edd7c-108">Değişkeniniz için kullanmak istediğiniz bileşik veri türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="edd7c-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="edd7c-109">Bileşik veri türü önceden tanımlanmamışsa, değişkeninizin onu kullanabilmesi için onu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="edd7c-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="edd7c-110">[Structure ifadesiyle](../../../language-reference/statements/structure-statement.md)bir yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="edd7c-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="edd7c-111">[Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir dizi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="edd7c-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="edd7c-112">[Sınıf ifadesiyle](../../../language-reference/statements/class-statement.md)bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="edd7c-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="edd7c-113">Değişkeninizi bir ifadesiyle bildirin `Dim` .</span><span class="sxs-lookup"><span data-stu-id="edd7c-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="edd7c-114">Bir yan tümcesiyle değişken adını izleyin `As` .</span><span class="sxs-lookup"><span data-stu-id="edd7c-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="edd7c-115">`As`Uygun bileşik veri türünün adı ile anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="edd7c-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="edd7c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edd7c-116">See also</span></span>

- [<span data-ttu-id="edd7c-117">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="edd7c-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="edd7c-118">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="edd7c-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="edd7c-119">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="edd7c-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="edd7c-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="edd7c-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="edd7c-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="edd7c-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="edd7c-122">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="edd7c-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="edd7c-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="edd7c-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
