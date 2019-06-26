---
title: 'Nasıl yapılır: -ToString yöntemini geçersiz kılma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: b12aeaeb5414d911abea4dfda654183ffa02b3e6
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398463"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="d345e-102">Nasıl yapılır: ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d345e-102">How to: Override the ToString Method (C# Programming Guide)</span></span>

<span data-ttu-id="d345e-103">Her sınıf veya yapı C# örtük olarak devraldığı <xref:System.Object> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d345e-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="d345e-104">Bu nedenle, C# ' de her bir nesne alır <xref:System.Object.ToString%2A> yöntemi o nesnenin dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d345e-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="d345e-105">Örneğin, tüm değişkenlerin türü `int` sahip bir `ToString` içeriklerini dize olarak döndürülecek sağlayan yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d345e-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="d345e-106">Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalıdır <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d345e-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="d345e-107">Biçim dizeleri ve diğer tür ile özel biçimlendirme kullanma hakkında daha fazla bilgi için `ToString` yöntemi bkz [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d345e-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d345e-108">Bu yöntem kullanılarak sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç olmadığı kadar güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d345e-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="d345e-109">Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="d345e-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="d345e-110">Geçersiz kılınacak `ToString` sınıf veya yapı birimi yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d345e-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="d345e-111">Bildirme bir `ToString` yöntemi aşağıdaki değiştiriciler ve dönüş türü:</span><span class="sxs-lookup"><span data-stu-id="d345e-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="d345e-112">Yöntemi uygulamak, böylece bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="d345e-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="d345e-113">Aşağıdaki örnek verilerin yanı sıra sınıfının adı sınıfın belirli bir örneğine özel döndürür.</span><span class="sxs-lookup"><span data-stu-id="d345e-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="d345e-114">Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d345e-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d345e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d345e-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="d345e-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d345e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d345e-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="d345e-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="d345e-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d345e-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="d345e-119">string</span><span class="sxs-lookup"><span data-stu-id="d345e-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)
- [<span data-ttu-id="d345e-120">override</span><span class="sxs-lookup"><span data-stu-id="d345e-120">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="d345e-121">virtual</span><span class="sxs-lookup"><span data-stu-id="d345e-121">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="d345e-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="d345e-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
