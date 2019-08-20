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
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl yapılır: ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)

İçindeki C# her sınıf veya yapı, <xref:System.Object> sınıfı örtük olarak devralır. Bu nedenle, içindeki C# her nesne, <xref:System.Object.ToString%2A> bu nesnenin dize gösterimini döndüren yöntemini alır. Örneğin, türündeki `int` tüm değişkenlerin bir `ToString` yöntemi vardır ve bu, içeriklerinin bir dize olarak döndürülmesini sağlar:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, istemci koduna yazmanız hakkında bilgi sağlamak <xref:System.Object.ToString%2A> için yöntemini geçersiz kılmanız gerekir.  
  
 Biçim dizelerini ve `ToString` yöntemi ile diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.  
  
Sınıfınıza veya `ToString` yapısına yöntemi geçersiz kılmak için:
  
1. Aşağıdaki Değiştiricilere ve dönüş türüne sahip bir `ToString` Yöntem bildirin:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Yöntemini bir dize döndürmesi için uygulayın.  
  
     Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     `ToString` Yöntemi aşağıdaki kod örneğinde gösterildiği gibi test edebilirsiniz:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Dizeler](../strings/index.md)
- [string](../../language-reference/keywords/string.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
