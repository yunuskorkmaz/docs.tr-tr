---
title: 'Nasıl Yapılır: -ToString yöntemini geçersiz kılma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 0be35b64e9df3ec2a78c62735b1b7072e092f073
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240747"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl Yapılır: ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)
Her sınıf veya yapı C# örtük olarak devraldığı <xref:System.Object> sınıfı. Bu nedenle, C# ' de her bir nesne alır <xref:System.Object.ToString%2A> yöntemi o nesnenin dize gösterimini döndürür. Örneğin, tüm değişkenlerin türü `int` sahip bir `ToString` içeriklerini dize olarak döndürülecek sağlayan yöntemi:  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalıdır <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntemi.  
  
 Biçim dizeleri ve diğer tür ile özel biçimlendirme kullanma hakkında daha fazla bilgi için `ToString` yöntemi bkz [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Bu yöntem kullanılarak sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç olmadığı kadar güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Sınıf veya yapı içinde ToString yöntemini geçersiz kılmak için  
  
1.  Bildirme bir `ToString` yöntemi aşağıdaki değiştiriciler ve dönüş türü:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Yöntemi uygulamak, böylece bir dize döndürür.  
  
     Aşağıdaki örnek verilerin yanı sıra sınıfının adı sınıfın belirli bir örneğine özel döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi:  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.IFormattable>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Dizeler](../../../csharp/programming-guide/strings/index.md)  
- [string](../../../csharp/language-reference/keywords/string.md)  
- [new](../../../csharp/language-reference/keywords/new.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [virtual](../../../csharp/language-reference/keywords/virtual.md)  
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
