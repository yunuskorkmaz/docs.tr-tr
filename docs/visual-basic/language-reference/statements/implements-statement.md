---
title: Implements açıklaması (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 865e99aa0e27591d10fde1465047a2e6bf183bbf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581787"
---
# <a name="implements-statement"></a><span data-ttu-id="16fe9-102">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="16fe9-102">Implements Statement</span></span>
<span data-ttu-id="16fe9-103">Görüntülenen sınıf veya yapı tanımında uygulanması gereken bir veya daha fazla arabirimi veya arabirim üyesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16fe9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16fe9-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="16fe9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="16fe9-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="16fe9-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16fe9-106">Required.</span></span> <span data-ttu-id="16fe9-107">Özellikleri, yordamları ve olayları sınıf veya yapıda ilgili Üyeler tarafından uygulanacak olan bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="16fe9-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="16fe9-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16fe9-108">Required.</span></span> <span data-ttu-id="16fe9-109">Uygulanan bir arabirimin üyesi.</span><span class="sxs-lookup"><span data-stu-id="16fe9-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16fe9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16fe9-110">Remarks</span></span>  
 <span data-ttu-id="16fe9-111">Arabirim, arabirimin sarmalarındaki üyeleri (özellikler, yordamlar ve olaylar) temsil eden prototipli türlerin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="16fe9-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="16fe9-112">Arabirimler yalnızca üyeler için bildirimleri içerir; sınıflar ve yapılar bu üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="16fe9-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="16fe9-113">Daha fazla bilgi için bkz. [arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="16fe9-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="16fe9-114">@No__t_0 deyimin `Class` veya `Structure` deyimden hemen önce izlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="16fe9-115">Bir arabirim uyguladığınızda, arabiriminde belirtilen tüm üyeleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="16fe9-116">Herhangi bir üyenin atlanması, söz dizimi hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="16fe9-117">Tek bir üyeyi uygulamak için, sınıf veya yapıda üyeyi bildirdiğinizde [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) anahtar sözcüğünü (`Implements` deyimden ayrı) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16fe9-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="16fe9-118">Daha fazla bilgi için bkz. [arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="16fe9-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="16fe9-119">Sınıflar, özelliklerin ve yordamların [özel](../../../visual-basic/language-reference/modifiers/private.md) uygulamalarını kullanabilir, ancak bu üyelere yalnızca uygulama sınıfının bir örneğini arabirimin türü olarak belirtilen bir değişkene atama yoluyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16fe9-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="16fe9-120">Example</span></span>  
 <span data-ttu-id="16fe9-121">Aşağıdaki örnek, bir arabirimin üyelerini uygulamak için `Implements` deyimin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="16fe9-122">Bir olay, özellik ve yordamla birlikte `ICustomerInfo` adlı bir arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16fe9-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="16fe9-123">Sınıf `customerInfo`, arabirimde tanımlanan tüm üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="16fe9-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="16fe9-124">Sınıfının `customerInfo`, sınıfın `ICustomerInfo` arabiriminin tüm üyelerini uyguladığını göstermek için `Implements` ifadesini ayrı bir kaynak kodu satırında kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="16fe9-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="16fe9-125">Sonra, sınıftaki her üye, bu arabirim üyesini uyguladığını göstermek için üye bildiriminin bir parçası olarak `Implements` anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="16fe9-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16fe9-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="16fe9-126">Example</span></span>  
 <span data-ttu-id="16fe9-127">Aşağıdaki iki yordamda, önceki örnekte uygulanan arabirimi nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16fe9-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="16fe9-128">Uygulamayı test etmek için bu yordamları projenize ekleyin ve `testImplements` yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="16fe9-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="16fe9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16fe9-129">See also</span></span>

- [<span data-ttu-id="16fe9-130">Uygular</span><span class="sxs-lookup"><span data-stu-id="16fe9-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="16fe9-131">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="16fe9-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="16fe9-132">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="16fe9-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
