---
title: enum (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 72feb6ee25070a6930b01b69e0a726041d34b0c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="enum-c-reference"></a>enum (C# Başvurusu)
`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi adlı adlandırılmış sabitler kümesinden oluşur farklı bir tür bildirmek için kullanılır.  
  
 Genellikle ad alanındaki tüm sınıflar, ile eşit kolaylık erişebilmesi için doğrudan bir ad alanı içinde bir enum tanımlamak en iyisidir. Ancak, bir enum da bir sınıf veya yapı içinde iç içe.  
  
 Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahip ve art arda gelen her Numaralandırıcı değerinin 1 ile artar. Örneğin, aşağıdaki numaralandırma içinde `Sat` olan `0`, `Sun` olan `1`, `Mon` olan `2`, vb.  
  
```  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Numaralandırmalar başlatıcıları varsayılan değerleri geçersiz kılmak için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.  
  
```  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Bu numaralandırma, öğelerin sırasını başlangıç zorlanır `1` yerine `0`. Ancak, değeri 0 olan bir sabit dahil olmak üzere önerilir. Daha fazla bilgi için bkz: [Numaralandırma türleri](../../../csharp/programming-guide/enumeration-types.md).  
  
 Her numaralandırma türü, herhangi bir tam sayı türü olabilecek bir temel türünde dışında [char](../../../csharp/language-reference/keywords/char.md). Temel alınan tür numaralandırma öğelerinin varsayılan [int](../../../csharp/language-reference/keywords/int.md). Başka bir tam sayı türü, bir numaralandırma gibi bildirmek için [bayt](../../../csharp/language-reference/keywords/byte.md), aşağıdaki örnekte gösterildiği gibi türü, izlemelidir tanımlayıcı sonra iki nokta kullanın.  
  
```  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Bir numaralandırma için onaylanan türleri [bayt](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Türünde bir değişken `Day` temel alınan tür; aralığındaki hiçbir değer atanabilir değerlerin adlandırılmış sabitler sınırlı değildir.  
  
 Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.  
  
> [!NOTE]
>  Bir numaralandırıcı adında boşluk içeremez.  
  
 Temel alınan tür, ne kadar depolama alanı için her Numaralandırıcı ayrılan belirtir. Ancak, bir açık atama dönüştürmek gerekli olan `enum` türü olarak bir tam sayı tür. Örneğin, aşağıdaki deyim Numaralandırıcı atar `Sun` türünde bir değişken için [int](../../../csharp/language-reference/keywords/int.md) dönüştürmek için bir atama kullanarak `enum` için `int`.  
  
```  
int x = (int)Day.Sun;  
```  
  
 Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçları ile kullanıldığında. Araçları gibi kullandığınızda bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi. (Üçüncü örneğe bakın.)  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Herhangi bir sabit olduğu gibi yalnızca ile tek tek enum değerlerinin tüm başvurularını derleme zamanında sayısal değişmez değerleri dönüştürülür. Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 Numaralandırmalar yeni sürümleri için ek değerler atama veya yeni bir sürümünde enum üyelerinin değerlerini değiştirme bağımlı kaynak kodu için sorunlara neden olabilir. Enum değerleri sıklıkla kullanıldığı [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimleri. Ek öğeler için eklenip eklenmediğini `enum` türü, varsayılan bölümünü switch deyimi, beklenmedik biçimde seçilebilir.  
  
 Diğer geliştiriciler kodunuzu kullanırsanız, yeni öğeler hiçbirine eklenirse, kodu nasıl tepki vermelidir hakkında yönergeler sağlamalıdır `enum` türleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilmedi. İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenlere atanır.  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, temel türü seçeneği bildirmek için kullanılan bir `enum` üyeleri olan türü `long`. Numaralandırma temel alınan türü olsa bile dikkat `long`, numaralandırma üyeleri hala açıkça yazın dönüştürülmelidir `long` bir cast kullanarak.  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Sabit Listesi Türleri](../../../csharp/programming-guide/enumeration-types.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Enum adlandırma kuralları](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)
