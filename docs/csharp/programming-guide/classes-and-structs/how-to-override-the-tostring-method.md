---
title: "Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b0f7bf35e5bd565e0bfa46fe91cf86aedcd2d8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)
Her sınıf veya yapı C# örtük olarak devralır <xref:System.Object> sınıfı. Bu nedenle, her nesne C# alır <xref:System.Object.ToString%2A> yöntemi nesnenin dize gösterimini döndürür. Örneğin, tüm değişkenler türü `int` sahip bir `ToString` bunları içeriklerini bir dize döndürecek şekilde etkinleştirir yöntemi:  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalısınız <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntem.  
  
 Biçim dizeleri ve başka ile özel biçimlendirme türleri nasıl kullanılacağı hakkında bilgi için `ToString` yöntemi, bkz: [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Bu yöntemle sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Sınıf veya yapı ToString yöntemini geçersiz kılmak için  
  
1.  Bildirme bir `ToString` yöntemi aşağıdaki değiştiricileri ve dönüş türüne sahip:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Böylece bir dize döndürür yöntemi uygulayabilirsiniz.  
  
     Aşağıdaki örnek verileri yanı sıra sınıfın adı sınıfın belirli bir örneğine özel döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi değiştirin:  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)  
 [dize](../../../csharp/language-reference/keywords/string.md)  
 [Yeni](../../../csharp/language-reference/keywords/new.md)  
 [geçersiz kılma](../../../csharp/language-reference/keywords/override.md)  
 [sanal](../../../csharp/language-reference/keywords/virtual.md)  
 [Biçimlendirme türleri](../../../standard/base-types/formatting-types.md)
