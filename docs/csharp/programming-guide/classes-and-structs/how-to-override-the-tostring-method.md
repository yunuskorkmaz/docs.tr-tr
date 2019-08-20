---
title: 'Nasıl yapılır: ToString yöntemini geçersiz kılma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: a2cf05dc6b288ffdaf1a20cf594231f48046a724
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596752"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="04ce4-102">Nasıl yapılır: ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04ce4-102">How to: Override the ToString Method (C# Programming Guide)</span></span>

<span data-ttu-id="04ce4-103">İçindeki C# her sınıf veya yapı, <xref:System.Object> sınıfı örtük olarak devralır.</span><span class="sxs-lookup"><span data-stu-id="04ce4-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="04ce4-104">Bu nedenle, içindeki C# her nesne, <xref:System.Object.ToString%2A> bu nesnenin dize gösterimini döndüren yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="04ce4-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="04ce4-105">Örneğin, türündeki `int` tüm değişkenlerin bir `ToString` yöntemi vardır ve bu, içeriklerinin bir dize olarak döndürülmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="04ce4-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="04ce4-106">Özel bir sınıf veya yapı oluşturduğunuzda, istemci koduna yazmanız hakkında bilgi sağlamak <xref:System.Object.ToString%2A> için yöntemini geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="04ce4-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="04ce4-107">Biçim dizelerini ve `ToString` yöntemi ile diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="04ce4-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04ce4-108">Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="04ce4-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="04ce4-109">Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="04ce4-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="04ce4-110">Sınıfınıza veya `ToString` yapısına yöntemi geçersiz kılmak için:</span><span class="sxs-lookup"><span data-stu-id="04ce4-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="04ce4-111">Aşağıdaki Değiştiricilere ve dönüş türüne sahip bir `ToString` Yöntem bildirin:</span><span class="sxs-lookup"><span data-stu-id="04ce4-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="04ce4-112">Yöntemini bir dize döndürmesi için uygulayın.</span><span class="sxs-lookup"><span data-stu-id="04ce4-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="04ce4-113">Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="04ce4-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="04ce4-114">`ToString` Yöntemi aşağıdaki kod örneğinde gösterildiği gibi test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="04ce4-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="04ce4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04ce4-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="04ce4-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04ce4-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04ce4-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="04ce4-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="04ce4-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="04ce4-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="04ce4-119">string</span><span class="sxs-lookup"><span data-stu-id="04ce4-119">string</span></span>](../../language-reference/keywords/string.md)
- [<span data-ttu-id="04ce4-120">override</span><span class="sxs-lookup"><span data-stu-id="04ce4-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="04ce4-121">virtual</span><span class="sxs-lookup"><span data-stu-id="04ce4-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="04ce4-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="04ce4-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
