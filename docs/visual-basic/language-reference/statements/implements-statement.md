---
title: Implements deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: cdcbe20157b9647040e3610d0632bd8e3fb9df65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681072"
---
# <a name="implements-statement"></a><span data-ttu-id="edf88-102">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="edf88-102">Implements Statement</span></span>
<span data-ttu-id="edf88-103">Bir veya daha fazla arabirimleri veya sınıfta uygulanması gereken arabirim üyeleri veya yapı tanımı göründüğü belirtir.</span><span class="sxs-lookup"><span data-stu-id="edf88-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edf88-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="edf88-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="edf88-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="edf88-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="edf88-106">Required.</span></span> <span data-ttu-id="edf88-107">Karşılık gelen sınıf veya yapının üyeleri tarafından uygulanacak olan özellikleri, yordamları ve olayları olduğundan bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="edf88-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="edf88-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="edf88-108">Required.</span></span> <span data-ttu-id="edf88-109">Uygulanan bir arabirim üyesi.</span><span class="sxs-lookup"><span data-stu-id="edf88-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edf88-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edf88-110">Remarks</span></span>  
 <span data-ttu-id="edf88-111">Bir koleksiyon bir arabirimdir arabirim üyeleri (özellikleri, yordamları ve olayları) temsil eden prototiplerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="edf88-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="edf88-112">Arabirimler yalnızca üyelerinin bildirimlerine içerir; Bu üyeleri, sınıfları ve yapıları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="edf88-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="edf88-113">Daha fazla bilgi için [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="edf88-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="edf88-114">`Implements` Deyimi hemen izlemelidir `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="edf88-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="edf88-115">Bir arabirim, arabirimde bildirilen tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="edf88-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="edf88-116">Herhangi bir üyenin atlama söz dizimi hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="edf88-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="edf88-117">Tek bir üye uygulamak için belirttiğiniz [uygular](../../../visual-basic/language-reference/statements/implements-clause.md) anahtar sözcüğü (ayrı olduğu `Implements` deyimi) sınıf veya yapı üyesi bildirdiğinizde.</span><span class="sxs-lookup"><span data-stu-id="edf88-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="edf88-118">Daha fazla bilgi için [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="edf88-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="edf88-119">Sınıfları kullanabilirsiniz [özel](../../../visual-basic/language-reference/modifiers/private.md) özellikler ve yordamlar, ancak bu üyeleri uygulamalarıdır uygulayan sınıfa örneği bir değişkene içinde bildirilen arabirim türünde olmasını atama tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="edf88-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf88-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="edf88-120">Example</span></span>  
 <span data-ttu-id="edf88-121">Aşağıdaki örnek nasıl kullanılacağını gösterir `Implements` deyimi bir arabirimin üyeleri uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="edf88-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="edf88-122">Adlı bir arabirim tanımlar `ICustomerInfo` bir olay, bir özellik ve bir yordam.</span><span class="sxs-lookup"><span data-stu-id="edf88-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="edf88-123">Sınıf `customerInfo` arabirim içinde tanımlanmış tüm üyelerini uygular.</span><span class="sxs-lookup"><span data-stu-id="edf88-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="edf88-124">Unutmayın sınıfı `customerInfo` kullanan `Implements` sınıf tüm üyelerini uyguladığını göstermek için ayrı bir kaynak kod satırında deyimi `ICustomerInfo` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="edf88-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="edf88-125">Her sınıf üyesi'ı kullanan `Implements` anahtar sözcüğü, arabirim üyesini uyguladığını belirtmek için üye bildiriminin bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="edf88-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf88-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="edf88-126">Example</span></span>  
 <span data-ttu-id="edf88-127">Aşağıdaki iki yordamdan önceki örnekte uygulanan arabirimi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="edf88-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="edf88-128">Uygulamasını test etmek için bu yordamları, proje ve çağrı ekleme `testImplements` yordamı.</span><span class="sxs-lookup"><span data-stu-id="edf88-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="edf88-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edf88-129">See also</span></span>
- [<span data-ttu-id="edf88-130">Uygulayan</span><span class="sxs-lookup"><span data-stu-id="edf88-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="edf88-131">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="edf88-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="edf88-132">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="edf88-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
