---
title: 'Nasıl yapılır: Değişkende Birden Fazla Değer Tutma (Visual Basic)'
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
ms.openlocfilehash: 783c75ed4577831b7ca444870c97063e8a057346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646690"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="811b7-102">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="811b7-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="811b7-103">Olması bildirirseniz bir değişkeni birden fazla değer tutan bir *bileşik veri türü*.</span><span class="sxs-lookup"><span data-stu-id="811b7-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="811b7-104">[Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) yapıları, dizileri ve sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="811b7-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="811b7-105">Bileşik veri türünde bir değişken başlangıç veri türleri ve diğer bileşik türler bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="811b7-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="811b7-106">Yapılar ve sınıflar kodun yanı sıra veri basılı tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="811b7-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="811b7-107">Birden fazla değer bir değişkende tutmak için</span><span class="sxs-lookup"><span data-stu-id="811b7-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="811b7-108">Değişken için kullanmak istediğiniz hangi bileşik veri türü belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="811b7-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="811b7-109">Bileşik veri türü zaten tanımlanmazsa, değişken kullanabilmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="811b7-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="811b7-110">Yapısı ile tanımlayan bir [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="811b7-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="811b7-111">Bir dizi tanımlamak bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="811b7-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="811b7-112">İle bir sınıf tanımlama bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="811b7-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="811b7-113">Değişkeni ile bildirme bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="811b7-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="811b7-114">Değişken adı ile izleyin bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="811b7-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="811b7-115">İzleyin `As` anahtar sözcüğüyle uygun bileşik veri türünün adı.</span><span class="sxs-lookup"><span data-stu-id="811b7-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811b7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="811b7-116">See Also</span></span>  
 [<span data-ttu-id="811b7-117">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="811b7-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="811b7-118">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="811b7-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="811b7-119">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="811b7-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="811b7-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="811b7-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="811b7-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="811b7-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="811b7-122">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="811b7-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="811b7-123">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="811b7-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
