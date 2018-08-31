---
title: 'Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: de59fb49ca5dbe1282cd828f7d6995dda449d31b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257307"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="2e6e4-102">Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2e6e4-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="2e6e4-103">Nesneler çok biçimli olduğundan türetilmiş bir tür tutmak için bir temel sınıf türünde bir değişken için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="2e6e4-104">Türetilen türün örnek yöntemleri erişmek için türetilmiş bir tür değerine geri değerine dönüştürme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-104">To access the derived type's instance methods, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="2e6e4-105">Ancak, basit bir denemeye atma riskini cast bu gibi durumlarda oluşturur bir <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="2e6e4-106">Diğer bir deyişle neden C# sağlar [olduğu](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="2e6e4-107">Bu işleçler, bir özel durum oluşturulmasına neden olmadan bir tür dönüştürme başarılı olup olmadığını test etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="2e6e4-108">Genel olarak, `as` işleci olduğundan daha verimli cast başarıyla yapılabilir gerçekten atama değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="2e6e4-109">`is` İşleci bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="2e6e4-110">Bu nedenle yalnızca bir nesnenin türünü belirlemek istiyorsanız ancak aslında cast gerekmez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e6e4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e6e4-111">Example</span></span>  
 <span data-ttu-id="2e6e4-112">Aşağıdaki örnekler nasıl kullanılacağını `is` ve `as` operatörlerinin bir başvurudan atama türünü başka bir özel durum riski olmadan.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="2e6e4-113">Örnek ayrıca nasıl kullanılacağını gösterir `as` boş değer atanabilen değer türleri ile işleci.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2e6e4-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e6e4-114">See Also</span></span>  
 [<span data-ttu-id="2e6e4-115">Türler</span><span class="sxs-lookup"><span data-stu-id="2e6e4-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="2e6e4-116">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2e6e4-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="2e6e4-117">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="2e6e4-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
