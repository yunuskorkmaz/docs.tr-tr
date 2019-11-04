---
title: 'Nasıl yapılır: ToString yöntemini geçersiz kılma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 9dd567e537768ceb8b9f61ce58dccd443db38ec7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419349"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Nasıl yapılır: ToString Yöntemini Geçersiz Kılma (C# Programlama Kılavuzu)

İçindeki C# her sınıf veya yapı, <xref:System.Object> sınıfını örtülü olarak devralır. Bu nedenle, içindeki C# her nesne, bu nesnenin dize gösterimini döndüren <xref:System.Object.ToString%2A> yöntemini alır. Örneğin, `int` türündeki tüm değişkenler bir `ToString` yöntemine sahiptir ve bu da bunların içeriğini bir dize olarak döndürmesini sağlar:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, istemci koduna yazmanız hakkında bilgi sağlamak için <xref:System.Object.ToString%2A> yöntemini geçersiz kılmanız gerekir.  
  
 Biçim dizelerini ve `ToString` yöntemiyle diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.  
  
Sınıfınıza veya yapıda `ToString` yöntemi geçersiz kılmak için:
  
1. Aşağıdaki değiştiriciler ve dönüş türü ile bir `ToString` yöntemi bildirin:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Yöntemini bir dize döndürmesi için uygulayın.  
  
     Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Aşağıdaki kod örneğinde gösterildiği gibi `ToString` yöntemini test edebilirsiniz:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Dizeler](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
