---
title: ToString yöntemi nasıl geçersiz kılınır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705580"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="573b2-102">ToString yöntemi (C# Programlama Kılavuzu) geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="573b2-102">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="573b2-103">C#'daki her sınıf veya <xref:System.Object> yapı, sınıfı dolaylı olarak devralır.</span><span class="sxs-lookup"><span data-stu-id="573b2-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="573b2-104">Bu nedenle, C#'daki <xref:System.Object.ToString%2A> her nesne, bu nesnenin dize temsilini döndüren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="573b2-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="573b2-105">Örneğin, tüm tür `int` değişkenlerinin, `ToString` içeriklerini dize olarak döndürmelerini sağlayan bir yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="573b2-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="573b2-106">Özel bir sınıf veya yapı oluşturduğunuzda, türünüzden istemci koduna ilişkin bilgi sağlamak için <xref:System.Object.ToString%2A> yöntemi geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="573b2-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="573b2-107">Biçim dizeleri ve yöntemle diğer özel biçimlendirme türleri nasıl kullanılacağı hakkında bilgi için bkz. [Formatting Types](../../../standard/base-types/formatting-types.md) `ToString`</span><span class="sxs-lookup"><span data-stu-id="573b2-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="573b2-108">Bu yöntemle hangi bilgilerin sağlanacağına karar verdiğinizde, sınıfınızın veya yapınızın güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="573b2-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="573b2-109">Kötü amaçlı kodtarafından yararlanılabilen herhangi bir bilgi sağlamadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="573b2-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="573b2-110">Sınıfınızdaki veya `ToString` yapınızdaki yöntemi geçersiz kılmak için:</span><span class="sxs-lookup"><span data-stu-id="573b2-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="573b2-111">Aşağıdaki `ToString` değiştiriciler ve iade türü ile bir yöntem bildirin:</span><span class="sxs-lookup"><span data-stu-id="573b2-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="573b2-112">Bir dize döndürür şekilde yöntemi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="573b2-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="573b2-113">Aşağıdaki örnek, sınıfın belirli bir örneğine özgü verilere ek olarak sınıfın adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="573b2-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="573b2-114">`ToString` Yöntemi aşağıdaki kod örneğinde gösterildiği gibi sınayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="573b2-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="573b2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="573b2-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="573b2-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="573b2-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="573b2-117">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="573b2-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="573b2-118">Dize</span><span class="sxs-lookup"><span data-stu-id="573b2-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="573b2-119">Dize</span><span class="sxs-lookup"><span data-stu-id="573b2-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="573b2-120">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="573b2-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="573b2-121">virtual</span><span class="sxs-lookup"><span data-stu-id="573b2-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="573b2-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="573b2-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
