---
title: 'Nasıl yapılır: Yapıyı Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: bffdc5974eff6b71e0abc4780a61aa300769eed6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058553"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="d936b-102">Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d936b-102">How to: Declare a Structure (Visual Basic)</span></span>

<span data-ttu-id="d936b-103">Yapı [ifadesiyle](../../../language-reference/statements/structure-statement.md)bir yapı bildirimi başlar ve bunu `End Structure` ifadesiyle sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="d936b-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="d936b-104">Bu iki deyim arasında en az bir *öğe*bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d936b-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="d936b-105">Öğeleri herhangi bir veri türünde olabilir, ancak en az bir veya paylaşılmayan olmayan bir değişken ya da paylaşılmayan olmayan bir olay olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d936b-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="d936b-106">Yapı bildiriminde yapı öğelerinden hiçbirini başlatamıyor.</span><span class="sxs-lookup"><span data-stu-id="d936b-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="d936b-107">Bir yapı türünde olması için bir değişken bildirdiğinizde, değişkenine değerleri değişken aracılığıyla erişerek atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d936b-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="d936b-108">Yapılar ve sınıflar arasındaki farklılıklarla ilgili bir tartışma için bkz. [yapılar ve sınıflar](structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d936b-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="d936b-109">Tanıtım amacıyla, bir çalışanın adını, telefon uzantısını ve maaşını izlemek istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="d936b-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="d936b-110">Bir yapı bunu tek bir değişkende yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d936b-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="d936b-111">Bir yapıyı bildirmek için</span><span class="sxs-lookup"><span data-stu-id="d936b-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="d936b-112">Yapı için başlangıç ve bitiş deyimlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d936b-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="d936b-113">[Ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md)veya [özel](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bir yapının erişim düzeyini belirtebilir veya buna varsayılan olarak izin verebilirsiniz `Public` .</span><span class="sxs-lookup"><span data-stu-id="d936b-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="d936b-114">Yapının gövdesine öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d936b-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="d936b-115">Bir yapının en az bir öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d936b-115">A structure must have at least one element.</span></span> <span data-ttu-id="d936b-116">Her öğeyi bildirmeniz ve bunun için bir erişim düzeyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d936b-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="d936b-117">[Dim ifadesini](../../../language-reference/statements/dim-statement.md) herhangi bir anahtar sözcük olmadan kullanırsanız, erişilebilirlik varsayılan olarak olur `Public` .</span><span class="sxs-lookup"><span data-stu-id="d936b-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="d936b-118">`salary`Yukarıdaki örnekteki alan, `Private` kapsayan sınıftan bile yapının dışından erişilemediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d936b-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="d936b-119">Ancak yordam, `giveRaise` `Public` Yapı dışından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d936b-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="d936b-120">Benzer şekilde, `salaryReviewTime` olayı yapının dışından yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d936b-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="d936b-121">Değişkenlere, `Sub` yordamlara ve olaylara ek olarak, `Function` bir yapıda sabitler, yordamlar ve özellikler de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d936b-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="d936b-122">En az bir bağımsız değişken alması şartıyla, en az bir özelliği *varsayılan özellik*olarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d936b-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="d936b-123">Bir olayı, paylaşılan bir yordamla işleyebilirsiniz [Shared](../../../language-reference/modifiers/shared.md) `Sub` .</span><span class="sxs-lookup"><span data-stu-id="d936b-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="d936b-124">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic ' de varsayılan bir özellik bildirme ve çağırma](../procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="d936b-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d936b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d936b-125">See also</span></span>

- [<span data-ttu-id="d936b-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d936b-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="d936b-127">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d936b-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="d936b-128">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d936b-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="d936b-129">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="d936b-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="d936b-130">Yapılar</span><span class="sxs-lookup"><span data-stu-id="d936b-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="d936b-131">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d936b-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="d936b-132">Yapı Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d936b-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="d936b-133">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="d936b-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="d936b-134">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="d936b-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="d936b-135">Kullanıcı Tanımlı Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d936b-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
