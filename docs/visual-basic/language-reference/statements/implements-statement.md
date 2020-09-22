---
title: Implements Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873236"
---
# <a name="implements-statement"></a><span data-ttu-id="d20e5-102">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="d20e5-102">Implements Statement</span></span>

<span data-ttu-id="d20e5-103">Görüntülenen sınıf veya yapı tanımında uygulanması gereken bir veya daha fazla arabirimi veya arabirim üyesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d20e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d20e5-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="d20e5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d20e5-105">Parts</span></span>  

 `interfacename`  
 <span data-ttu-id="d20e5-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-106">Required.</span></span> <span data-ttu-id="d20e5-107">Özellikleri, yordamları ve olayları sınıf veya yapıda ilgili Üyeler tarafından uygulanacak olan bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="d20e5-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="d20e5-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-108">Required.</span></span> <span data-ttu-id="d20e5-109">Uygulanan bir arabirimin üyesi.</span><span class="sxs-lookup"><span data-stu-id="d20e5-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d20e5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d20e5-110">Remarks</span></span>  

 <span data-ttu-id="d20e5-111">Arabirim, arabirimin sarmalarındaki üyeleri (özellikler, yordamlar ve olaylar) temsil eden prototipli türlerin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="d20e5-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="d20e5-112">Arabirimler yalnızca üyeler için bildirimleri içerir; sınıflar ve yapılar bu üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="d20e5-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="d20e5-113">Daha fazla bilgi için bkz. [arabirimler](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d20e5-113">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="d20e5-114">`Implements`Deyimin hemen arkasından `Class` veya ifadesini izlemesi gerekir `Structure` .</span><span class="sxs-lookup"><span data-stu-id="d20e5-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="d20e5-115">Bir arabirim uyguladığınızda, arabiriminde belirtilen tüm üyeleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="d20e5-116">Herhangi bir üyenin atlanması, söz dizimi hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="d20e5-117">Tek bir üyeyi uygulamak için, [Implements](implements-clause.md) `Implements` sınıf veya yapıda üyeyi bildirdiğinizde Implements anahtar sözcüğünü (deyimden ayrı olan) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d20e5-117">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="d20e5-118">Daha fazla bilgi için bkz. [arabirimler](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d20e5-118">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="d20e5-119">Sınıflar, özelliklerin ve yordamların [özel](../modifiers/private.md) uygulamalarını kullanabilir, ancak bu üyelere yalnızca uygulama sınıfının bir örneğini arabirimin türü olarak belirtilen bir değişkene atama yoluyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-119">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20e5-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d20e5-120">Example</span></span>  

 <span data-ttu-id="d20e5-121">Aşağıdaki örnek, `Implements` bir arabirimin üyelerini uygulamak için ifadesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="d20e5-122">`ICustomerInfo`Bir olay, özellik ve bir yordam ile adlı bir arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d20e5-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="d20e5-123">Sınıfı, `customerInfo` arabiriminde tanımlanan tüm üyeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="d20e5-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="d20e5-124">Sınıfının, `customerInfo` `Implements` sınıfın tüm üyelerini uyguladığından emin olmak için deyimin ayrı bir kaynak kod satırında kullandığını unutmayın `ICustomerInfo` .</span><span class="sxs-lookup"><span data-stu-id="d20e5-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="d20e5-125">Sonra, sınıftaki her üye, `Implements` Bu arabirim üyesini uyguladığını göstermek için anahtar sözcüğünü kendi üye bildiriminin bir parçası olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="d20e5-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20e5-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d20e5-126">Example</span></span>  

 <span data-ttu-id="d20e5-127">Aşağıdaki iki yordamda, önceki örnekte uygulanan arabirimi nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d20e5-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="d20e5-128">Uygulamayı test etmek için projenize bu yordamları ekleyin ve `testImplements` yordamı çağırın.</span><span class="sxs-lookup"><span data-stu-id="d20e5-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="d20e5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d20e5-129">See also</span></span>

- [<span data-ttu-id="d20e5-130">Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d20e5-130">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="d20e5-131">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="d20e5-131">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="d20e5-132">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d20e5-132">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
