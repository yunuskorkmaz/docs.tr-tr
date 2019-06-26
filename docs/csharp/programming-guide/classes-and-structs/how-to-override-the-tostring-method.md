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
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl yapılır: ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)

Her sınıf veya yapı C# örtük olarak devraldığı <xref:System.Object> sınıfı. Bu nedenle, C# ' de her bir nesne alır <xref:System.Object.ToString%2A> yöntemi o nesnenin dize gösterimini döndürür. Örneğin, tüm değişkenlerin türü `int` sahip bir `ToString` içeriklerini dize olarak döndürülecek sağlayan yöntemi:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, geçersiz kılmalıdır <xref:System.Object.ToString%2A> türünüz için istemci kodu hakkında bilgi sağlamak için yöntemi.  
  
 Biçim dizeleri ve diğer tür ile özel biçimlendirme kullanma hakkında daha fazla bilgi için `ToString` yöntemi bkz [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Bu yöntem kullanılarak sağlamak için hangi bilgilerin karar verdiğinizde, sınıf veya yapı hiç olmadığı kadar güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilir herhangi bir bilgi sağlamaz emin olmak dikkatli olun.  
  
Geçersiz kılınacak `ToString` sınıf veya yapı birimi yöntemi:
  
1. Bildirme bir `ToString` yöntemi aşağıdaki değiştiriciler ve dönüş türü:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Yöntemi uygulamak, böylece bir dize döndürür.  
  
     Aşağıdaki örnek verilerin yanı sıra sınıfının adı sınıfın belirli bir örneğine özel döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Test edebilirsiniz `ToString` yöntemini aşağıdaki kod örneğinde gösterildiği gibi:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Dizeler](../../../csharp/programming-guide/strings/index.md)
- [string](../../../csharp/language-reference/keywords/string.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
