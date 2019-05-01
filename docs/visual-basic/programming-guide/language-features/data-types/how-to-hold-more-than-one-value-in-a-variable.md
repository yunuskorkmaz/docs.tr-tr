---
title: 'Nasıl yapılır: (Visual Basic) değişkende birden fazla değer tutma'
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
ms.openlocfilehash: e2e1648ea508ecdd744adb8d2a4f7fdbc1e586c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906496"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="74d85-102">Nasıl yapılır: (Visual Basic) değişkende birden fazla değer tutma</span><span class="sxs-lookup"><span data-stu-id="74d85-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="74d85-103">Olması bildirirseniz bir değişkeni birden fazla değer içeren bir *bileşik veri türü*.</span><span class="sxs-lookup"><span data-stu-id="74d85-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="74d85-104">[Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) yapıları, diziler ve sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="74d85-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="74d85-105">Bileşik veri türünde bir değişken başlangıç veri türleri ve diğer bileşik türler bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="74d85-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="74d85-106">Yapılar ve sınıflar, verilerin yanı sıra, kod barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="74d85-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="74d85-107">Bir değişkende birden fazla değerini tutmak için</span><span class="sxs-lookup"><span data-stu-id="74d85-107">To hold more than one value in a variable</span></span>  
  
1. <span data-ttu-id="74d85-108">Bileşik veri türüne değişkeniniz için kullanmak istediğiniz belirleyin.</span><span class="sxs-lookup"><span data-stu-id="74d85-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2. <span data-ttu-id="74d85-109">Bileşik veri türü zaten tanımlı değilse, değişken kullanabilmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="74d85-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    - <span data-ttu-id="74d85-110">Bir yapı tanımla bir [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="74d85-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    - <span data-ttu-id="74d85-111">Bir dizi tanımlamak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="74d85-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    - <span data-ttu-id="74d85-112">İle bir sınıf tanımlayan bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="74d85-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3. <span data-ttu-id="74d85-113">İle bir değişken bildirmek bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="74d85-113">Declare your variable with a `Dim` statement.</span></span>  
  
4. <span data-ttu-id="74d85-114">Değişken adı ile bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="74d85-114">Follow the variable name with an `As` clause.</span></span>  
  
5. <span data-ttu-id="74d85-115">İzleyin `As` anahtar sözcüğü ile uygun bileşik veri türünün adı.</span><span class="sxs-lookup"><span data-stu-id="74d85-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d85-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74d85-116">See also</span></span>

- [<span data-ttu-id="74d85-117">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="74d85-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="74d85-118">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="74d85-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="74d85-119">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="74d85-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="74d85-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="74d85-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="74d85-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="74d85-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="74d85-122">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="74d85-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="74d85-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="74d85-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
