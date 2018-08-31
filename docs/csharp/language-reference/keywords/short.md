---
title: short (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: f402b9d2d62bcc3ba265755d59a657b88c197482
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331702"
---
# <a name="short-c-reference"></a>short (C# Başvurusu)

`short` boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tam sayı veri türü belirtir.  
  
|Tür|Aralık|Boyut|.NET türü|  
|----------|-----------|----------|-------------------------|  
|`short`|-32.768 için 32.767|İşaretli 16 bit tam sayı|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirmek ve başlatmak bir `short` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).  Tamsayı sabit değeri aralığının dışında ise `short` (diğer bir deyişle, bu ise kısa <xref:System.Int16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.Int16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur. 

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 1,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `short` değerleri.  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
 - C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi

 Çağırma yöntemleri aşırı yüklendiğinde bir yayın kullanılmalıdır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `short` ve [int](../../../csharp/language-reference/keywords/int.md) parametreleri:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Kullanarak `short` atama doğru tür, örneğin çağrıldığını güvence altına alır:  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>Dönüşümler  

 Önceden tanımlanmış bir örtük dönüştürme vardır `short` için [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Daha büyük depolama boyutu için sabit değerli olmayan sayısal türleri örtülü olarak dönüştürülemiyor `short` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için). Örneğin, aşağıdaki iki göz önünde bulundurun `short` değişkenleri `x` ve `y`:  
  
```csharp  
short x = 5, y = 12;  
```  
  
 Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 Bu sorunu gidermek için bir tür dönüştürme kullanın:  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 Ayrıca, hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak da mümkündür:  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 Kayan nokta türlerinden hiç örtük dönüştürme `short`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Int16>  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
