---
title: "Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="bc0b5-102">Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bc0b5-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="bc0b5-103">Nesneler biçimli olduğundan türetilmiş bir tür tutmak için bir temel sınıf türünde bir değişken için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="bc0b5-104">Türetilen türün yöntemi erişmek için türetilmiş bir tür değerine geri dönüştürmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="bc0b5-105">Ancak, basit bir girişiminde atma riskini bu gibi durumlarda cast oluşturur bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="bc0b5-106">Diğer bir deyişle neden C# sağlar [olan](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçler.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="bc0b5-107">Bir özel durum oluşturulmasına neden olmadan bir cast başarılı olup olmadığını sınamak için aşağıdaki işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="bc0b5-108">Genel olarak, `as` işleci olduğundan daha verimli cast başarıyla yapılabilmesi için gerçekten cast değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="bc0b5-109">`is` İşleci bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="bc0b5-110">Bu nedenle yalnızca bir nesnenin türünü belirlemek istiyorsanız ancak aslında cast gerekmez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc0b5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc0b5-111">Example</span></span>  
 <span data-ttu-id="bc0b5-112">Aşağıdaki örnekler nasıl kullanılacağını `is` ve `as` başka bir özel durum atma riski olmadan için bir başvuru cast işleçleri yazın.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="bc0b5-113">Bu örnek ayrıca nasıl kullanılacağını gösterir `as` boş değer atanabilen değer türleri olan işleci.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bc0b5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-114">See Also</span></span>  
 [<span data-ttu-id="bc0b5-115">Türler</span><span class="sxs-lookup"><span data-stu-id="bc0b5-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="bc0b5-116">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="bc0b5-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="bc0b5-117">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="bc0b5-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
