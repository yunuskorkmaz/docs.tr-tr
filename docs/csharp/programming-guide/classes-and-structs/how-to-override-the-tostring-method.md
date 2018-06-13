---
title: 'Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 86394f5fed55f57df8928648548fcfca117b00d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330713"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="ee15e-102">Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ee15e-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="ee15e-103">Her sınıf veya yapı C# örtük olarak devralır <xref:System.Object> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ee15e-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="ee15e-104">Bu nedenle, her nesne C# alır <xref:System.Object.ToString%2A> yöntemi nesnenin dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee15e-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="ee15e-105">Örneğin, tüm değişkenler türü `int` sahip bir `ToString` bunları içeriklerini bir dize döndürecek şekilde etkinleştirir yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ee15e-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="ee15e-106">Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalısınız <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ee15e-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="ee15e-107">Biçim dizeleri ve başka ile özel biçimlendirme türleri nasıl kullanılacağı hakkında bilgi için `ToString` yöntemi, bkz: [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ee15e-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee15e-108">Bu yöntemle sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ee15e-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="ee15e-109">Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="ee15e-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="ee15e-110">Sınıf veya yapı ToString yöntemini geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="ee15e-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="ee15e-111">Bildirme bir `ToString` yöntemi aşağıdaki değiştiricileri ve dönüş türüne sahip:</span><span class="sxs-lookup"><span data-stu-id="ee15e-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="ee15e-112">Böylece bir dize döndürür yöntemi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee15e-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="ee15e-113">Aşağıdaki örnek verileri yanı sıra sınıfın adı sınıfın belirli bir örneğine özel döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee15e-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="ee15e-114">Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ee15e-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ee15e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee15e-115">See Also</span></span>  
 <xref:System.IFormattable>  
 [<span data-ttu-id="ee15e-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee15e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ee15e-117">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="ee15e-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ee15e-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="ee15e-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="ee15e-119">string</span><span class="sxs-lookup"><span data-stu-id="ee15e-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
 [<span data-ttu-id="ee15e-120">new</span><span class="sxs-lookup"><span data-stu-id="ee15e-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="ee15e-121">override</span><span class="sxs-lookup"><span data-stu-id="ee15e-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="ee15e-122">virtual</span><span class="sxs-lookup"><span data-stu-id="ee15e-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="ee15e-123">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="ee15e-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
