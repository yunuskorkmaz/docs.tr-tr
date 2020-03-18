---
title: ToString yöntemi nasıl geçersiz kılınır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705580"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>ToString yöntemi (C# Programlama Kılavuzu) geçersiz kılma

C#'daki her sınıf veya <xref:System.Object> yapı, sınıfı dolaylı olarak devralır. Bu nedenle, C#'daki <xref:System.Object.ToString%2A> her nesne, bu nesnenin dize temsilini döndüren yöntemi alır. Örneğin, tüm tür `int` değişkenlerinin, `ToString` içeriklerini dize olarak döndürmelerini sağlayan bir yöntemi vardır:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Özel bir sınıf veya yapı oluşturduğunuzda, türünüzden istemci koduna ilişkin bilgi sağlamak için <xref:System.Object.ToString%2A> yöntemi geçersiz kılmanız gerekir.  
  
 Biçim dizeleri ve yöntemle diğer özel biçimlendirme türleri nasıl kullanılacağı hakkında bilgi için bkz. [Formatting Types](../../../standard/base-types/formatting-types.md) `ToString`  
  
> [!IMPORTANT]
> Bu yöntemle hangi bilgilerin sağlanacağına karar verdiğinizde, sınıfınızın veya yapınızın güvenilmeyen kod tarafından kullanılıp kullanılmayacağını göz önünde bulundurun. Kötü amaçlı kodtarafından yararlanılabilen herhangi bir bilgi sağlamadığınızdan emin olun.  
  
Sınıfınızdaki veya `ToString` yapınızdaki yöntemi geçersiz kılmak için:
  
1. Aşağıdaki `ToString` değiştiriciler ve iade türü ile bir yöntem bildirin:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Bir dize döndürür şekilde yöntemi uygulayın.  
  
     Aşağıdaki örnek, sınıfın belirli bir örneğine özgü verilere ek olarak sınıfın adını döndürür.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     `ToString` Yöntemi aşağıdaki kod örneğinde gösterildiği gibi sınayabilirsiniz:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Dize](../strings/index.md)
- [Dize](../../language-reference/builtin-types/reference-types.md)
- [Geçersiz kılma](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
