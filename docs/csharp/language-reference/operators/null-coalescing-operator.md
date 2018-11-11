---
title: ?? İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: fbcfda07cc55628aeed82eb7561516f7012bc4fe
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980680"
---
# <a name="-operator-c-reference"></a>?? İşleci (C# Başvurusu)
`??` İşleci, null birleşim işleci çağrılır.  İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur). Kullanabileceğiniz `??` söz dizimsel anlamlılık (sağ el işlenenini) uygun bir değer döndürmek için işlecin sol işlenen null yapılabilir bir tür değeri null olduğunda. Null bir değer türü kullanmadan bir NULL olmayan değer türüne atamayı denerseniz, `??` işleci, bir derleme zamanı hatası oluşturacağını. Bir yayın kullanırsanız ve null yapılabilir değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durumu oluşturulur.  
  
 Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Sonucu bir?? işleci, hem bağımsız değişkenlerinden sabitleri olsa bile, bir sabit değer için dikkate alınmaz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
- [Hangi tam olarak 'Yükseltilmiş' anlamına mu?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
