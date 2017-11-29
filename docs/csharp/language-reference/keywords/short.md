---
title: "short (C# Başvurusu)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords: short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca3c5444c4fa7a49b7169be3e2a5b15d1a72207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="short-c-reference"></a>short (C# Başvurusu)

`short`değerleri aşağıdaki tabloda gösterilen aralığı ve boyutu göre depolayan bir tam sayı veri türünü gösterir.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`short`|-32.768 için 32.767|İşaretli 16 bit tam sayı|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  

Bildirme ve başlatma bir `short` değişken ondalık değişmez değer, onaltılık bir hazır değer atama veya (C# 7 için değişmez değer bir ikili başlayarak).  Değişmez değer tamsayı aralığı dışında ise `short` (diğer bir deyişle, bu ise değerinden <xref:System.Int16.MinValue?displayProperty=nameWithType> veya daha büyük <xref:System.Int16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur. 

Aşağıdaki örnekte, ondalık sayı olarak, onaltılık temsil 1,034 tamsayılar eşit ve ikili değişmez değerleri gelen örtük olarak dönüştürülür [int](../../../csharp/language-reference/keywords/int.md) için `short` değerleri.  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Önek kullanması `0x` veya `0X` onaltılık değişmez değeri ve öneki belirtmek için `0b` veya `0B` ikili bir hazır değer belirtmek için. Ondalık değişmez değerler, önek vardır.

C# 7 ile okunabilirliği artırmak birkaç özellik eklenmiştir başlatılıyor. 
 - C# 7.0 sağlar alt çizgi karakteri kullanımını `_`, basamak ayırıcı olarak.
 - C# 7.2 verir `_` önekten sonra bir ikili ya da onaltılık değişmez değeri basamak ayırıcısı olarak kullanılacak. Ondalık bir hazır değer önde gelen bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümü

 Arama aşırı yüklenmiş yöntemler bir cast kullanılması gerekir. Örneğin, aşağıdaki aşırı kullanan yöntemleri düşünün `short` ve [int](../../../csharp/language-reference/keywords/int.md) Parametreler:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Kullanarak `short` cast garanti doğru türde, örneğin çağrıldığından emin:  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>Dönüşümler  

 Önceden tanımlanmış bir örtük dönüştürme `short` için [int](../../../csharp/language-reference/keywords/int.md), [uzun](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ ondalık](../../../csharp/language-reference/keywords/decimal.md).  
  
 Daha büyük depolama boyutu nonliteral sayısal türlerini örtük olarak dönüştürülemiyor `short` (bkz [tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md) depolama boyutları tam sayı türleri için). Örneğin, aşağıdaki iki göz önünde bulundurun `short` değişkenleri `x` ve `y`:  
  
```csharp  
short x = 5, y = 12;  
```  
  
 Atama işlecinin sağ taraftaki aritmetik ifade değerlendiren çünkü aşağıdaki atama deyimi bir derleme hatası üretir [int](../../../csharp/language-reference/keywords/int.md) varsayılan olarak.  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 Bu sorunu gidermek için bir atama kullanın:  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 Hedef değişken depolama boyutu ile aynı veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak da mümkündür:  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 Kayan nokta türlerinden örtük bir dönüştürme yok `short`. Örneğin, bir açık atama kullanılmadığı sürece aşağıdaki ifadeyi derleyici hatası oluşturur:  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Karma kayan nokta türleri ve tam sayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](../../../csharp/language-reference/keywords/float.md) ve [çift](../../../csharp/language-reference/keywords/double.md).  
  
 Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Int16>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
