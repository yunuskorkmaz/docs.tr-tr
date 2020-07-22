---
title: ToString yöntemini geçersiz kılma-C# Programlama Kılavuzu
description: C# ' de ToString metodunu geçersiz kılmayı öğrenin. Her sınıf veya yapı nesnesini devralır ve bu nesnenin dize gösterimini döndüren ToString öğesini alır.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 65b34b485d4b90173a4c956dd0ebaaa590a0c7c9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865014"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="533dc-104">ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="533dc-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="533dc-105">C# içindeki her sınıf veya yapı, sınıfı dolaylı olarak devralır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="533dc-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="533dc-106">Bu nedenle, C# içindeki her nesne <xref:System.Object.ToString%2A> , bu nesnenin dize gösterimini döndüren yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="533dc-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="533dc-107">Örneğin, türündeki tüm değişkenlerin `int` bir `ToString` yöntemi vardır ve bu, içeriklerinin bir dize olarak döndürülmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="533dc-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="533dc-108">Özel bir sınıf veya yapı oluşturduğunuzda, <xref:System.Object.ToString%2A> istemci koduna yazmanız hakkında bilgi sağlamak için yöntemini geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="533dc-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="533dc-109">Biçim dizelerini ve yöntemi ile diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için `ToString` bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="533dc-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="533dc-110">Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="533dc-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="533dc-111">Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="533dc-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="533dc-112">`ToString`Sınıfınıza veya yapısına yöntemi geçersiz kılmak için:</span><span class="sxs-lookup"><span data-stu-id="533dc-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="533dc-113">`ToString`Aşağıdaki Değiştiricilere ve dönüş türüne sahip bir yöntem bildirin:</span><span class="sxs-lookup"><span data-stu-id="533dc-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="533dc-114">Yöntemini bir dize döndürmesi için uygulayın.</span><span class="sxs-lookup"><span data-stu-id="533dc-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="533dc-115">Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="533dc-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="533dc-116">`ToString`Yöntemi aşağıdaki kod örneğinde gösterildiği gibi test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="533dc-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="533dc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="533dc-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="533dc-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="533dc-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="533dc-119">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="533dc-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="533dc-120">Dizeler</span><span class="sxs-lookup"><span data-stu-id="533dc-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="533dc-121">dizisinde</span><span class="sxs-lookup"><span data-stu-id="533dc-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="533dc-122">override</span><span class="sxs-lookup"><span data-stu-id="533dc-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="533dc-123">sanal</span><span class="sxs-lookup"><span data-stu-id="533dc-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="533dc-124">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="533dc-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
