---
title: sbyte (C# Başvurusu)
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: 4a2d13463348c2f0c32aec076623f59040d1d81f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sbyte-c-reference"></a>sbyte (C# Başvurusu)

`sbyte` Aşağıdaki tabloda gösterilen aralığı ve boyutu göre değerleri depolayan tamsayı türü gösterir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 ile 127|İşaretli 8 bit tam sayı|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirme ve başlatma bir `sbyte` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# ile 7.0 için değişmez değer bir ikili başlayarak). 

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil-102 tamsayılar eşit ve ikili değişmez değerleri, gelen dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `sbyte` değerleri.    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7.0 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

 Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Değişmez değer tamsayı aralığı dışında ise `sbyte` (diğer bir deyişle, bu ise değerinden <xref:System.SByte.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.SByte.MaxValue?displayProperty=nameWithType>, derleme hatası oluşur. Değişmez değer bir tamsayı sonek olduğunda, kendi içinde değerini temsil bu tür ilk türüdür: [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md). Bu, bu örnekte, sayısal değişmez değerleri anlamına `0x9A` ve `0b10011010` 32 bit imzalı tamsayılar aşıyor 156, değerini olarak yorumlanır <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Bu nedenle atama işleci gerekli değildir ve atama oluşması gereken bir [denetlenmeyen](unchecked.md) bağlamı. 

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümü

 Arama aşırı yüklenmiş yöntemler bir cast kullanılması gerekir. Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `sbyte` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Kullanarak `sbyte` cast garanti doğru türde, örneğin çağrıldığından emin:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Dönüşümler  
 Önceden tanımlanmış bir örtük dönüştürme `sbyte` için [kısa](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift ](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Daha büyük depolama boyutu nonliteral sayısal türlerini örtük olarak dönüştürülemiyor `sbyte` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için). Örneğin, aşağıdaki iki göz önünde bulundurun `sbyte` değişkenleri `x` ve `y`:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 Atama işlecinin sağ tarafında aritmetik ifade değerlendiren çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Bu sorunu gidermek için aşağıdaki örnekteki gibi ifade atayın:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Ancak hedef değişkeni depolama boyutu ile aynı veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak için mümkündür:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ayrıca kayan nokta türleri için örtük dönüştürme yok fark `sbyte`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.SByte>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
