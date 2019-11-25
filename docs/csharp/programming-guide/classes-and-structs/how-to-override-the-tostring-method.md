---
title: ToString yöntemini geçersiz kılma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 3d5b63609ea61764d4042d534c40d8032fb82841
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970467"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="d7363-102">ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d7363-102">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="d7363-103">İçindeki C# her sınıf veya yapı, <xref:System.Object> sınıfını örtülü olarak devralır.</span><span class="sxs-lookup"><span data-stu-id="d7363-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="d7363-104">Bu nedenle, içindeki C# her nesne, bu nesnenin dize gösterimini döndüren <xref:System.Object.ToString%2A> yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="d7363-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="d7363-105">Örneğin, `int` türündeki tüm değişkenler bir `ToString` yöntemine sahiptir ve bu da bunların içeriğini bir dize olarak döndürmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="d7363-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="d7363-106">Özel bir sınıf veya yapı oluşturduğunuzda, istemci koduna yazmanız hakkında bilgi sağlamak için <xref:System.Object.ToString%2A> yöntemini geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7363-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="d7363-107">Biçim dizelerini ve `ToString` yöntemiyle diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d7363-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7363-108">Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d7363-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="d7363-109">Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d7363-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="d7363-110">Sınıfınıza veya yapıda `ToString` yöntemi geçersiz kılmak için:</span><span class="sxs-lookup"><span data-stu-id="d7363-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="d7363-111">Aşağıdaki değiştiriciler ve dönüş türü ile bir `ToString` yöntemi bildirin:</span><span class="sxs-lookup"><span data-stu-id="d7363-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="d7363-112">Yöntemini bir dize döndürmesi için uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d7363-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="d7363-113">Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7363-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="d7363-114">Aşağıdaki kod örneğinde gösterildiği gibi `ToString` yöntemini test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7363-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d7363-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7363-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="d7363-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d7363-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d7363-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="d7363-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d7363-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d7363-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="d7363-119">string</span><span class="sxs-lookup"><span data-stu-id="d7363-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="d7363-120">override</span><span class="sxs-lookup"><span data-stu-id="d7363-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="d7363-121">virtual</span><span class="sxs-lookup"><span data-stu-id="d7363-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="d7363-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="d7363-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
