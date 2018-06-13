---
title: out (Genel Değiştirici) (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269620"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="324fe-102">out (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="324fe-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="324fe-103">Genel tür parametreleri için `out` anahtar sözcüğü tür parametresi eşdeğişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="324fe-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="324fe-104">Kullanabileceğiniz `out` anahtar sözcüğü genel arabirimler ve temsilciler.</span><span class="sxs-lookup"><span data-stu-id="324fe-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="324fe-105">Kovaryans genel parametresi tarafından belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="324fe-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="324fe-106">Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="324fe-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="324fe-107">Kovaryans ve kontravaryans referans türleri için desteklenir, ancak değer türlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="324fe-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="324fe-108">Tür parametresi tarafından belirtilen daha fazla türetilmiş türler döndürülecek yöntemlerinden eşdeğişken türü parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="324fe-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="324fe-109">Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IEnumerable%601>T türü eşdeğişken, bir nesnenin atayabilirsiniz `IEnumerable(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntem kullanmadan türü.</span><span class="sxs-lookup"><span data-stu-id="324fe-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="324fe-110">Aynı türde, ancak daha fazla türetilmiş genel tür parametresi olan başka bir temsilci eşdeğişken temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="324fe-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="324fe-111">Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="324fe-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="324fe-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="324fe-112">Example</span></span>  
 <span data-ttu-id="324fe-113">Aşağıdaki örnek, bildirme, genişletmek ve eşdeğişken genel arabirimini uygulayan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="324fe-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="324fe-114">Ayrıca, eşdeğişken arabirimini uygulayan sınıflar için örtük dönüşüm kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="324fe-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="324fe-115">Bir genel arabiriminde bir tür parametresi aşağıdaki koşullar uymazsa eşdeğişken bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="324fe-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="324fe-116">Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız değişkenleri bir tür olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="324fe-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="324fe-117">Bu kural için bir istisna vardır.</span><span class="sxs-lookup"><span data-stu-id="324fe-117">There is one exception to this rule.</span></span> <span data-ttu-id="324fe-118">Eşdeğişken arabiriminde karşıtı Genel temsilci bir yöntem parametresi olarak varsa, bu temsilci için genel tür parametresi olarak eşdeğişken türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="324fe-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="324fe-119">Eşdeğişken hakkında daha fazla bilgi ve karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="324fe-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="324fe-120">Tür parametresi, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="324fe-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="324fe-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="324fe-121">Example</span></span>  
 <span data-ttu-id="324fe-122">Aşağıdaki örnek, bildirme, oluşturma ve eşdeğişken genel temsilcisi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="324fe-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="324fe-123">Ayrıca, temsilci türleri örtük dönüştürmeye nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="324fe-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="324fe-124">Yalnızca bir yöntemin dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri için kullanılmaz, genel bir temsilci türü eşdeğişken olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="324fe-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="324fe-125">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="324fe-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="324fe-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="324fe-126">See Also</span></span>  
 [<span data-ttu-id="324fe-127">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="324fe-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="324fe-128">in</span><span class="sxs-lookup"><span data-stu-id="324fe-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="324fe-129">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="324fe-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
