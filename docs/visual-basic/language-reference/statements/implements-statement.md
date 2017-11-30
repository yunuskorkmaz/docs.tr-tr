---
title: Implements Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a><span data-ttu-id="c9ed1-102">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="c9ed1-102">Implements Statement</span></span>
<span data-ttu-id="c9ed1-103">Bir veya daha fazla arabirimleri veya sınıfında uygulanan arabirim üyeleri veya göründüğü yapı tanımı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ed1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9ed1-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="c9ed1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c9ed1-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="c9ed1-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-106">Required.</span></span> <span data-ttu-id="c9ed1-107">Sınıf veya yapı karşılık gelen üyeleri tarafından uygulanacak, özellikler, yordamlar ve olayları olan bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="c9ed1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-108">Required.</span></span> <span data-ttu-id="c9ed1-109">Uygulanan bir arabirim üye.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ed1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9ed1-110">Remarks</span></span>  
 <span data-ttu-id="c9ed1-111">Bir koleksiyonu bir arabirimdir prototipler oluşturmayı üyeleri (özellikleri, yordamlar ve olayları) temsil eden arabirim yalıtır.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="c9ed1-112">Arabirimleri yalnızca üyeleri için bildirimleri içerir; sınıfları ve yapıları bu üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="c9ed1-113">Daha fazla bilgi için bkz: [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed1-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="c9ed1-114">`Implements` Deyimi hemen uymalıdır `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="c9ed1-115">Arabirim uyguladığınızda arabirimde bildirilen tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="c9ed1-116">Herhangi bir üyenin atlama bir sözdizimi hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="c9ed1-117">Ayrı bir üyesiyle uygulamak için belirttiğiniz [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md) anahtar sözcüğü (ayrı olduğu `Implements` deyimi) bildirme zaman sınıf veya yapı üye.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="c9ed1-118">Daha fazla bilgi için bkz: [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c9ed1-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="c9ed1-119">Sınıfları kullanma [özel](../../../visual-basic/language-reference/modifiers/private.md) özellikleri ve yordamları, ancak bu üyeleri uygulamalarıdır yalnızca uygulama sınıfının bir örneğini bir değişkenin içine bildirilen arabirimi türünde olmasını atama tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ed1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9ed1-120">Example</span></span>  
 <span data-ttu-id="c9ed1-121">Aşağıdaki örnekte nasıl kullanılacağını gösterir `Implements` bir arabirim üyelerini uygulama bildirimi.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="c9ed1-122">Adlı bir arabirim tanımlar `ICustomerInfo` bir olay, bir özellik ve bir yordam.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="c9ed1-123">Sınıf `customerInfo` arabiriminde tanımlanan tüm üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="c9ed1-124">Unutmayın sınıfı `customerInfo` kullanan `Implements` sınıfın tüm üyelerini uygulayan göstermek için ayrı bir kaynak kod satırdaki deyim `ICustomerInfo` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="c9ed1-125">Her üye sınıfında kullanır `Implements` anahtar sözcüğü bu arabirim üyesini uygulayan belirtmek için üye bildiriminden bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ed1-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9ed1-126">Example</span></span>  
 <span data-ttu-id="c9ed1-127">Aşağıdaki iki yordamdan önceki örnekte uygulanan arabirimi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="c9ed1-128">Uygulanmasını test etmek için bu yordamları, proje çağrısı ekleyin ve `testImplements` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c9ed1-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ed1-129">See Also</span></span>  
 [<span data-ttu-id="c9ed1-130">Uygular</span><span class="sxs-lookup"><span data-stu-id="c9ed1-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="c9ed1-131">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="c9ed1-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="c9ed1-132">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9ed1-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
