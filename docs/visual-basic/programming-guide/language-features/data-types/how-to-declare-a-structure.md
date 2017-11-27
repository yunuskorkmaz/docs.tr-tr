---
title: "Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8203327e189d095c9f7ceeb3b68ea24efe9ba882
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="95293-102">Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95293-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="95293-103">Yapı bildirimleri ile başlayan [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md), ve onunla bitiş `End` `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="95293-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End` `Structure` statement.</span></span> <span data-ttu-id="95293-104">Bu iki ifade arasında en az bir bildirmelisiniz *öğesi*.</span><span class="sxs-lookup"><span data-stu-id="95293-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="95293-105">Öğeleri herhangi bir veri türü olabilir, ancak en az bir paylaşılmayan bir değişken ya da paylaşılmayan, de olay olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95293-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="95293-106">Yapı bildirimleri yapısı öğelerinde başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="95293-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="95293-107">Bir yapı türüne sahip olması için bir değişken bildirirken, değerler öğelerine değişken üzerinden erişerek atayın.</span><span class="sxs-lookup"><span data-stu-id="95293-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="95293-108">Yapılar ve sınıflar arasındaki farklar tartışma için bkz [yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="95293-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="95293-109">Tanıtım amacıyla, bir çalışanın adı, dahili telefon numarası ve maaş izlemek istediğiniz bir durum düşünün.</span><span class="sxs-lookup"><span data-stu-id="95293-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="95293-110">Bir yapısı, tek bir değişkende bunu yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="95293-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="95293-111">Bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="95293-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="95293-112">Başlangıç ve bitiş deyimleri yapısı için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="95293-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="95293-113">Bir yapı kullanarak erişim düzeyini belirleyebileceğiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü veya sağlar, Varsayılan olarak `Public`.</span><span class="sxs-lookup"><span data-stu-id="95293-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="95293-114">Öğeleri yapısı gövdesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95293-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="95293-115">Bir yapı en az bir öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95293-115">A structure must have at least one element.</span></span> <span data-ttu-id="95293-116">Her öğe bildirme ve bir erişim düzeyini belirtin.</span><span class="sxs-lookup"><span data-stu-id="95293-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="95293-117">Kullanırsanız [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) erişilebilirlik hiçbir anahtar, varsayılan olarak `Public`.</span><span class="sxs-lookup"><span data-stu-id="95293-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
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
  
     <span data-ttu-id="95293-118">`salary` Önceki örnekte alandır `Private`, yani bile içeren sınıfından yapısı dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="95293-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="95293-119">Ancak, `giveRaise` yordam `Public`, bu nedenle, gelen dışında yapısı çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="95293-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="95293-120">Benzer şekilde, yükseltebilirsiniz `salaryReviewTime` olayından yapısı dışında.</span><span class="sxs-lookup"><span data-stu-id="95293-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="95293-121">Değişkenlerinin yanı sıra `Sub` yordamları ve olaylar, sabitleri, ayrıca tanımlayabilirsiniz `Function` yordamları ve yapı özellikleri.</span><span class="sxs-lookup"><span data-stu-id="95293-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="95293-122">En çok bir özellik olarak belirleyebilirsiniz *varsayılan özellik*, sağlanan en az bir değişken alır.</span><span class="sxs-lookup"><span data-stu-id="95293-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="95293-123">Bir olay işleyebilir bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="95293-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="95293-124">Daha fazla bilgi için bkz: [nasıl yapılır: bildirme ve Visual Basic'te bir varsayılan özellik çağrı](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="95293-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95293-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95293-125">See Also</span></span>  
 [<span data-ttu-id="95293-126">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="95293-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="95293-127">Başlangıç veri türleri</span><span class="sxs-lookup"><span data-stu-id="95293-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="95293-128">Bileşik veri türleri</span><span class="sxs-lookup"><span data-stu-id="95293-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="95293-129">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="95293-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="95293-130">Yapıları</span><span class="sxs-lookup"><span data-stu-id="95293-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="95293-131">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="95293-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="95293-132">Yapı değişkenleri</span><span class="sxs-lookup"><span data-stu-id="95293-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="95293-133">Yapılar ve diğer programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="95293-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="95293-134">Yapılar ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="95293-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="95293-135">Kullanıcı tanımlı veri türü</span><span class="sxs-lookup"><span data-stu-id="95293-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
