---
title: Atama ve Tür Dönüşümleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 778fcd8932dfa37bc5d4487f3ec6597425cf9fb8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529361"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Atama ve Tür Dönüşümleri (C# Programlama Kılavuzu)

Bir değişken bildirildikten sonra C# türü statik belirlenmiştir derleme zamanında olduğundan, yeniden bildirilen veya bu tür değişkenin türüne örtük olarak dönüştürülebilir olmadığı sürece başka bir türde bir değer atanır. Örneğin, `string` için örtük olarak dönüştürülemez `int`. Bu nedenle, sonra bildirdiğiniz `i` olarak bir `int`, ", aşağıdaki kodun gösterdiği gibi Hello" dizesi atanamaz:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Ancak, bazen bir değişken veya yöntem türünden parametreye başka bir değeri kopyalama gerekebilir. Örneğin, bir yöntem parametresi olarak yazıldığında geçirmek için gereken tamsayı değişkenini olabilir `double`. Veya bir sınıf değişkeni bir arabirim türü bir değişkene atayın gerekebilir. Bu tür işlemler adlı *tür dönüştürmeleri*. C# ' ta, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:  
  
-   **Örtük dönüştürmeleri**: dönüştürme tür bakımından güvenli olduğundan ve hiçbir veri kaybı olmayacağını hiçbir özel sözdizimi gereklidir. Daha küçük Dönüştürmelere daha büyük bir tam sayı türleri için ve temel sınıf için türetilmiş sınıflardan dönüştürmeler verilebilir.  
  
-   **Açık dönüştürmeler (yayınları)**: açık dönüştürmeler bir atama işleci gerektirir. Atama, bilgi dönüştürme sırasında kaybedilen veya diğer nedenlerle dönüştürme başarılı olmayabilir gereklidir.  Daha az duyarlılık ya da daha küçük bir aralığı olan bir türü sayısal dönüştürme ve türetilmiş bir sınıf bir taban sınıfı örneğini dönüştürme Bunun tipik örneklerindendir.  
  
-   **Kullanıcı tanımlı dönüşümler**: türetilmiş sınıf – temel sınıf ilişkisi olmayan özel türler arasında açık ve örtük dönüştürme etkinleştirmek için tanımlayabileceğiniz özel yöntemler kullanıcı tanımlı dönüştürmeler gerçekleştirilir. Daha fazla bilgi için [dönüştürme işleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Yardımcı sınıfları dönüştürmeler**: tamsayı gibi uyumlu olmayan türleri arasında dönüştürme yapma ve <xref:System.DateTime?displayProperty=nameWithType> nesneleri veya onaltılık dizeler ve bayt dizileri kullanabilirsiniz <xref:System.BitConverter?displayProperty=nameWithType> sınıfı <xref:System.Convert?displayProperty=nameWithType> sınıfı ve `Parse`gibi yerleşik sayısal yöntemlerinin türleri <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Daha fazla bilgi için [nasıl yapılır: byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [nasıl yapılır: bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), ve [nasıl yapılır: dönüştürme arasında onaltılık dizeler ve sayısal türler](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Örtük dönüşümler  
 Depolanacak değer kısaltılır veya yuvarlanır olmadan değişkene uygun olduğunda yerleşik sayısal türler için örtük bir dönüştürme yapılabilir. Örneğin, bir değişken türü [uzun](../../../csharp/language-reference/keywords/long.md) (64-bit tamsayı) depolayabileceğiniz değerine herhangi bir [int](../../../csharp/language-reference/keywords/int.md) (32-bit tamsayı) depolayabilir. Aşağıdaki örnekte, derleyici değeri örtük olarak dönüştürür `num` türüne sağ taraftaki `long` giderek önce `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Tüm örtük sayısal dönüşümler tam bir listesi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Başvuru türleri için örtük bir dönüştürme her zaman bir sınıftan herhangi biri, doğrudan veya dolaylı temel sınıfların veya arabirimleri bulunmaktadır. Hiçbir özel sözdizimi, türetilmiş bir sınıf her zaman temel sınıfın tüm üyeleri içerdiği için gereklidir.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Açık dönüştürmeler  
 Dönüştürme bilgileri kaybetme riski yapılamazsa, ancak derleyici çağrılır açık bir dönüştürme gerçekleştirmek gerektirir bir *atama*. Bir yayın derleyici, dönüştürme yapmak istediğiniz ve veri kaybı oluşabilir haberdar olduğunuzu açıkça bildiren bir yoludur. Bir dönüştürme gerçekleştirmek için değişkeni ve değer dönüştürülecek önünde parantez içinde için atama türünü belirtin. Aşağıdaki program yayınları bir [çift](../../../csharp/language-reference/keywords/double.md) için bir [int](../../../csharp/language-reference/keywords/int.md). Program yayın olmadan derlemeyecektir.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 İzin verilen açık sayısal dönüşümler listesi için bkz. [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Başvuru türleri için açık bir tür dönüştürme temel türünden türetilmiş bir tür dönüştürmek istiyorsanız gereklidir:  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Başvuru türleri arasındaki bir tür dönüştürme işlemi, temel alınan nesnenin çalışma zamanı türünü değiştirmez. yalnızca bu nesneye bir başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Tür dönüştürme özel durumlar çalışma zamanında  
 Bazı başvuru türü dönüşümleri, derleyici bir tür dönüştürme geçerli olup olmayacağını belirlenemiyor. Çalışma zamanında başarısız için doğru derleyen bir dönüştürme işlemi mümkündür. Aşağıdaki örnekte gösterildiği gibi çalışma zamanında başarısız neden olacak bir tür cast bir <xref:System.InvalidCastException> oluşturulması için.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# sağlar [olduğu](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) işleçleri, atama gerçekleştirmeden önce uyumluluğu test etmek sağlamak için. Daha fazla bilgi için [nasıl yapılır: güvenli bir şekilde kullanarak AS ve is işleçlerini](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Türler](../../../csharp/programming-guide/types/index.md)  
- [() İşleci](../../../csharp/language-reference/operators/invocation-operator.md)  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
- [Dönüştürme İşleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [Genelleşmiş tür dönüştürme](https://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
- [Dışarı aktarılan tür dönüştürme](https://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
- [Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
