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
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>ToString yöntemini geçersiz kılma (C# Programlama Kılavuzu)

C# içindeki her sınıf veya yapı, sınıfı dolaylı olarak devralır <xref:System.Object> . Bu nedenle, C# içindeki her nesne <xref:System.Object.ToString%2A> , bu nesnenin dize gösterimini döndüren yöntemini alır. Örneğin, türündeki tüm değişkenlerin `int` bir `ToString` yöntemi vardır ve bu, içeriklerinin bir dize olarak döndürülmesini sağlar:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, <xref:System.Object.ToString%2A> istemci koduna yazmanız hakkında bilgi sağlamak için yöntemini geçersiz kılmanız gerekir.  
  
 Biçim dizelerini ve yöntemi ile diğer özel biçimlendirme türlerini kullanma hakkında daha fazla bilgi için `ToString` bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Bu yöntem aracılığıyla sağlanacak bilgilere karar verirken, sınıfınızın veya yapının güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kod tarafından yararlanılabilen herhangi bir bilgi sağlamadiğinizden emin olun.  
  
`ToString`Sınıfınıza veya yapısına yöntemi geçersiz kılmak için:
  
1. `ToString`Aşağıdaki Değiştiricilere ve dönüş türüne sahip bir yöntem bildirin:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Yöntemini bir dize döndürmesi için uygulayın.  
  
     Aşağıdaki örnek, sınıfının belirli bir örneğine özgü verilere ek olarak sınıfının adını döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     `ToString`Yöntemi aşağıdaki kod örneğinde gösterildiği gibi test edebilirsiniz:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Dizeler](../strings/index.md)
- [dizisinde](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [sanal](../../language-reference/keywords/virtual.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
