---
title: 'Nasıl yapılır: (Visual Basic) bir yapıyı bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906717"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="63ad4-102">Nasıl yapılır: (Visual Basic) bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="63ad4-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="63ad4-103">Yapı bildirimi ile başlayan [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md), ve ile sona `End Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="63ad4-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="63ad4-104">Bu iki deyimden arasında en az bir bildirmelisiniz *öğesi*.</span><span class="sxs-lookup"><span data-stu-id="63ad4-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="63ad4-105">Öğeleri herhangi bir veri türünde olabilir, ancak en az bir paylaşılmayan bir değişken veya paylaşılmayan, özel olmayan bir olay olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63ad4-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="63ad4-106">Yapı öğeleri yapısı bildiriminde başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="63ad4-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="63ad4-107">Bir yapı türünde olması için bir değişken bildirdiğinizde, değerler öğelerine değişken üzerinden erişerek atayın.</span><span class="sxs-lookup"><span data-stu-id="63ad4-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="63ad4-108">Yapılar ve sınıflar arasındaki farklar için bkz [yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="63ad4-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="63ad4-109">Tanıtım amacıyla, bir çalışanın adı, dahili telefon numarası ve maaş izlemek istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="63ad4-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="63ad4-110">Bir yapı, tek bir değişkende bunu yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63ad4-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="63ad4-111">Bir yapıyı bildirmek için</span><span class="sxs-lookup"><span data-stu-id="63ad4-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="63ad4-112">Başlangıç ve bitiş ifadeleri yapısının oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63ad4-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="63ad4-113">Yapısı kullanarak bir erişim düzeyini belirleyebileceğiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük veya izin, Varsayılan olarak `Public`.</span><span class="sxs-lookup"><span data-stu-id="63ad4-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="63ad4-114">Öğeleri yapısı gövdesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63ad4-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="63ad4-115">Bir yapı en az bir öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="63ad4-115">A structure must have at least one element.</span></span> <span data-ttu-id="63ad4-116">Her öğe bildirmek ve bunun için bir erişim düzeyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63ad4-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="63ad4-117">Kullanırsanız [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) erişilebilirlik herhangi bir anahtar, varsayılan olarak `Public`.</span><span class="sxs-lookup"><span data-stu-id="63ad4-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="63ad4-118">`salary` Önceki örnekte alandır `Private`, hatta içeren sınıftan yapısı dışında erişilemez durumda anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="63ad4-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="63ad4-119">Ancak, `giveRaise` oluşan bir yordamdır `Public`, bu nedenle, gelen yapısı çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="63ad4-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="63ad4-120">Benzer şekilde, yükseltebilirsiniz `salaryReviewTime` olaydan yapısı dışında.</span><span class="sxs-lookup"><span data-stu-id="63ad4-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="63ad4-121">Değişkenleri yanı sıra `Sub` yordamları ve olayları, sabitleri, ayrıca tanımlayabilirsiniz `Function` yordamlar ve bir yapı özellikleri.</span><span class="sxs-lookup"><span data-stu-id="63ad4-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="63ad4-122">En fazla bir özellik olarak belirlediğiniz *varsayılan özellik*, sağlanan en az bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="63ad4-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="63ad4-123">Bir olayla işleyebilir bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="63ad4-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="63ad4-124">Daha fazla bilgi için [nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özellik çağırma](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="63ad4-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ad4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63ad4-125">See also</span></span>

- [<span data-ttu-id="63ad4-126">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="63ad4-127">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="63ad4-128">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="63ad4-129">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="63ad4-130">Yapılar</span><span class="sxs-lookup"><span data-stu-id="63ad4-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="63ad4-131">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="63ad4-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="63ad4-132">Yapı Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="63ad4-133">Yapılar ve Diğer Programlama Öğeleri</span><span class="sxs-lookup"><span data-stu-id="63ad4-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="63ad4-134">Yapılar ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="63ad4-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="63ad4-135">User-Defined Veri Türü</span><span class="sxs-lookup"><span data-stu-id="63ad4-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
