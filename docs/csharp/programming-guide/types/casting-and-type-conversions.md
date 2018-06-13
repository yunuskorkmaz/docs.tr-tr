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
ms.openlocfilehash: 0c17fc89d93bdbb01bdef7935e72f8a7d96b0a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336563"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Atama ve Tür Dönüşümleri (C# Programlama Kılavuzu)
Bir değişken bildirildikten sonra C# statik olarak derleme zamanında belirtilmiş olduğundan, yeniden bildirilen veya bu türü değişkenin türüne dönüştürülemez olmadığı sürece başka bir tür değerleri depolamak için kullanılır. Örneğin, bir tamsayı dönüştürme yok herhangi bir rastgele dizeye yoktur. Bu nedenle, sonra bildirdiğiniz `i` bir tamsayı olarak, dize "Hello", aşağıdaki kodda gösterildiği gibi atayamazsınız.  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 Ancak, bazen bir değeri başka bir tür bir değişken veya yöntem parametresi kopyalamak gerekebilir. Örneğin, bir yöntem parametresi olarak yazıldığında geçirmek için gereken bir tamsayı değişken olabilir `double`. Veya bir arabirim türünde bir değişken için bir sınıf değişkeni atamanız gerekebilir. Bu tür işlemler adlı *tür dönüştürmeleri*. C# ' ta, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:  
  
-   **Örtük dönüşümler**: özel bir sözdizimi dönüştürme türü güvenli olduğundan ve hiçbir veri kaybı olmaz gereklidir. Örnek daha büyük tam sayı türleri küçük gelen dönüştürme ve türetilmiş sınıflardan sınıflar temel dönüşümleri verilebilir.  
  
-   **Açık Dönüşümler (atamaları)**: açık dönüşümler atama işleci gerektirir. Atama dönüştürmede kayıp bilgisi veya diğer nedenlerle dönüştürme başarılı olmayabilir gereklidir.  Tipik örnek daha az duyarlılık veya daha küçük bir aralık olan bir türü sayısal dönüştürme ve türetilmiş bir sınıf bir temel sınıf örneği dönüştürülmesi verilebilir.  
  
-   **Kullanıcı tanımlı dönüşümler**: kullanıcı tanımlı dönüşümler bir temel sınıf – türetilmiş sınıf ilişkisi olmayan özel türler arasında açık ve kapalı dönüşümler etkinleştirmek tanımladığınız özel yöntemler tarafından gerçekleştirilir. Daha fazla bilgi için bkz: [dönüştürme işleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Yardımcı sınıfları dönüşümleri**: tamsayılar gibi uyumlu olmayan türler arasında dönüştürme yapma ve <xref:System.DateTime?displayProperty=nameWithType> nesneleri ya da onaltılık dizeler ve bayt dizileri kullanabilirsiniz <xref:System.BitConverter?displayProperty=nameWithType> sınıfı, <xref:System.Convert?displayProperty=nameWithType> sınıfı ve `Parse`gibi yerleşik sayısal yöntemlerinin türleri <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Daha fazla bilgi için bkz: [nasıl yapılır: byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [nasıl yapılır: bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), ve [nasıl yapılır: Dönüştür arasında onaltılık dizeler ve sayısal türler](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Örtük dönüşümler  
 Değerin depolanması kesildi veya yuvarlanmış olmadan değişkenine uygun olduğunda yerleşik sayısal türler için örtük bir dönüştürme yapılabilir. Örneğin, bir değişken türü [uzun](../../../csharp/language-reference/keywords/long.md) (8 bayt tamsayı) saklayabilir değerine herhangi bir [int](../../../csharp/language-reference/keywords/int.md) (32-bit bilgisayarda 4 bayt) depolayabilir. Aşağıdaki örnekte, derleyici örtük olarak bir türe sağdaki değeri dönüştürür `long` atanarak önce `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Tüm örtük sayısal dönüşümler tam bir listesi için bkz: [örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Referans türleri için her zaman örtük bir dönüştürme öğesinden bir sınıf herhangi biri doğrudan veya dolaylı olarak temel sınıflar veya arabirimler için bulunmaktadır. Özel bir sözdizimi, türetilmiş bir sınıf bir taban sınıfın tüm üyeleri her zaman içerdiği için gereklidir.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Açık dönüşümler  
 Dönüştürme bilgileri kaybetme riskini yapılamazsa, derleyici adlandırılır açık bir dönüştürme gerçekleştirmek gerektirir ancak bir *cast*. Bir cast derleyici dönüştürme yapmak istediğiniz ve veri kaybı oluşabilir kullanan açıkça bildiren bir yoludur. Bir dönüştürme gerçekleştirmek için dönüştürülecek değer veya değişken önünde parantez içinde için atama türü belirtin. Aşağıdaki program atamaları bir [çift](../../../csharp/language-reference/keywords/double.md) için bir [int](../../../csharp/language-reference/keywords/int.md). Program dönüştürme olmadan derlenmez.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 İzin verilen açık sayısal dönüşümler listesi için bkz: [açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Referans türleri için temel bir türden türetilmiş bir tür dönüştürmek istiyorsanız bir açık atama gereklidir:  
  
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
  
 Başvuru türleri arasında dönüştürme işlemi, temel alınan nesnenin çalışma zamanı tür değiştirmez; yalnızca bu nesne için bir başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için bkz: [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Çalışma zamanında tür dönüştürme özel durumlar  
 Bazı başvuru türü dönüşümleri derleyici bir cast geçerli olup olmayacağını belirleyemiyor. Çalışma zamanında işleminin başarısız olmasına, doğru derlenen bir cast mümkündür. Aşağıdaki örnekte gösterildiği gibi bir çalışma zamanında başarısız olmasına neden olacak türe bir <xref:System.InvalidCastException> oluşturulmasına.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# sağlar [olan](../../../csharp/language-reference/keywords/is.md) ve [olarak](../../../csharp/language-reference/keywords/as.md) bir cast gerçekleştirmeden önce uyumluluk için test sağlamak için işleçler. Daha fazla bilgi için bkz: [nasıl yapılır: olarak kullanarak güvenli bir şekilde atama ve is işleçlerini](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [() İşleci](../../../csharp/language-reference/operators/invocation-operator.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [Dönüştürme İşleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [Genelleştirilmiş tür dönüştürmeleri](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [Dışarı aktarılan tür dönüştürmeleri](http://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [Nasıl yapılır: Bir Dizeyi Sayıya Dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
