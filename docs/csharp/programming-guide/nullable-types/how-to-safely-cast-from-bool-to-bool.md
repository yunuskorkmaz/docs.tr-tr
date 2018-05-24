---
title: 'Nasıl yapılır: bool? Değerinden bool Değerine Güvenli bir Şekilde Atama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: e04e34abd477730f9dd01486ec6bddcde4943edc
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="044c9-102">Nasıl yapılır: bool? Değerinden bool Değerine Güvenli bir Şekilde Atama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="044c9-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="044c9-103">`bool?` Boş değer atanabilir tür üç farklı değerler içerebilir: `true`, `false`, ve `null`.</span><span class="sxs-lookup"><span data-stu-id="044c9-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="044c9-104">Bu nedenle, `bool?` türü ile gibi koşulları kullanılamaz `if`, `for`, veya `while`.</span><span class="sxs-lookup"><span data-stu-id="044c9-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="044c9-105">Örneğin, aşağıdaki kod derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="044c9-105">For example, the following code causes a compiler error.</span></span>  
  
```csharp  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="044c9-106">Ne belirsiz olmasından dolayı buna izin verilmiyor `null` koşullu bağlamında anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="044c9-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="044c9-107">Kullanmak için bir `bool?` koşullu bir deyimde ilk denetleyin, <xref:System.Nullable%601.HasValue%2A> değerini olmadığından emin olmak için özellik `null`ve ardından hangisine `bool`.</span><span class="sxs-lookup"><span data-stu-id="044c9-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="044c9-108">Daha fazla bilgi için bkz: [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="044c9-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="044c9-109">Cast gerçekleştirirseniz bir `bool?` değerini `null`, <xref:System.InvalidOperationException> koşullu testinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="044c9-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="044c9-110">Aşağıdaki örnek, gelen güvenli bir şekilde atama yollarından biri gösterir `bool?` için `bool`:</span><span class="sxs-lookup"><span data-stu-id="044c9-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="044c9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="044c9-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="044c9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="044c9-112">See Also</span></span>  
 [<span data-ttu-id="044c9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="044c9-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="044c9-114">Değişmez Değer Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="044c9-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="044c9-115">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="044c9-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="044c9-116">?? İşleç</span><span class="sxs-lookup"><span data-stu-id="044c9-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
