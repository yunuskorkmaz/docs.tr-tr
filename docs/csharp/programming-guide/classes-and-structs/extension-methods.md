---
title: Uzantı yöntemleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: ce35ef4d4286310aa6c8b6e40c3a448b0d91ea7d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937518"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)
Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri özel bir statik yöntem türüdür, ancak bunlar genişletilmiş türdeki örnek yöntemler ise çağrılır. F# Ve Visual Basic yazılmış C#istemci kodu için, bir uzantı yöntemi çağırma ile gerçekte bir tür içinde tanımlanan Yöntemler arasında görünür bir fark yoktur.  
  
 En yaygın genişletme yöntemleri, var olan <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türlerine sorgu işlevselliği ekleyen LINQ standart sorgu işleçleridir. Standart sorgu işleçlerini kullanmak için, önce bunları bir `using System.Linq` yönergesi ile kapsama taşıyın. Ardından <xref:System.Collections.Generic.IEnumerable%601> uygulayan herhangi bir tür <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>gibi örnek yöntemlere sahip olacak şekilde görünür. <xref:System.Collections.Generic.List%601> veya <xref:System.Array>gibi bir <xref:System.Collections.Generic.IEnumerable%601> türünün örneğinden sonra "Dot" yazdığınızda bu ek yöntemleri IntelliSense bildiri tamamlanmasında görebilirsiniz.  
  
 Aşağıdaki örnek, bir tamsayı dizisinde standart sorgu işleci `OrderBy` yönteminin nasıl çağrılacağını gösterir. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleçleri, lambda ifadeleri parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametresi, yöntemin hangi tür üzerinde çalıştığını belirtir ve parametresi [bundan önce bu](../../language-reference/keywords/this.md) değiştiriciden gelir. Uzantı yöntemleri yalnızca ad alanını kaynak kodunuza bir `using` yönergesi ile açıkça içeri aktardığınızda kapsamdadır.  
  
 Aşağıdaki örnek, <xref:System.String?displayProperty=nameWithType> sınıfı için tanımlanmış bir uzantı yöntemini gösterir. Bunun iç içe ve genel olmayan bir statik sınıf içinde tanımlandığına dikkat edin:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 `WordCount` uzantısı yöntemi bu `using` yönergesi ile kapsama getirilebilir:  
  
```csharp  
using ExtensionMethods;  
```  
  
 Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Kodunuzda örnek yöntemi sözdizimini ile genişletme yöntemi çağırırsınız. Ancak derleyici tarafından üretilen ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Bu nedenle, kapsülleme ilkesi gerçekten ihlal edilmez. Aslında genişletme yöntemleri, genişletildikleri türde özel değişkenlere erişemez.  
  
 Daha fazla bilgi için bkz. [özel bir genişletme yöntemi uygulama ve çağırma](./how-to-implement-and-call-a-custom-extension-method.md).
  
 Genel olarak, büyük olasılıkla kendinizinkileri uygulamayla kıyaslandığında genişletme yöntemlerini çok daha arayacaksınız. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için uzantı yöntemlerini etkinleştirmek için, yöntemlerin tanımlandığı ad alanı için bir `using` yönergesi eklemeniz yeterlidir. Örneğin, standart sorgu işleçlerini kullanmak için bu `using` yönergesini kodunuza ekleyin:  
  
```csharp  
using System.Linq;  
```  
  
 (System. Core. dll dosyasına da bir başvuru eklemeniz gerekebilir.) Standart sorgu işleçlerinin artık <xref:System.Collections.Generic.IEnumerable%601> türleri için ek yöntemler olarak IntelliSense 'de göründüğünü fark edeceksiniz.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama  
 Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Diğer bir deyişle, bir türün `Process(int i)`adlı bir yöntemi varsa ve aynı imzaya sahip bir uzantı yönteminiz varsa, derleyici her zaman örnek yöntemine bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf `Extensions`, `IMyInterface`uygulayan her tür için tanımlanmış genişletme yöntemleri içerir. `A`, `B`ve `C` tüm sınıfları arabirimini uygular.  
  
 Ad ve imza, sınıflar tarafından zaten uygulanmış yöntemlerle tam olarak eşleştiğinden `MethodB` uzantısı yöntemi hiçbir şekilde çağrılmaz.  
  
 Derleyici eşleştirilen imzayla bir oluşum yöntemi bulamadığında, varsa, eşleşen bir uzantı yöntemini bağlayın.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 Genel olarak, genişletme yöntemlerini tutumlu ve yalnızca gerektiğinde uygulamanızı öneririz. Mümkün olduğunda, varolan türü genişletmesi gereken istemci kodu, bunu varolan türden türetilmiş yeni bir tür oluşturarak yapmalıdır. Daha fazla bilgi için bkz. [Devralma](./inheritance.md).  
  
 Kaynak kodunu değiştiremediğiniz bir türü genişletmek üzere genişletme yöntemini kullanırsanız, türün uygulanmasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olabileceği riskini göze alırsınız.  
  
 Belirli bir tür için uzantı yöntemleri uygularsanız, aşağıdaki noktaları hatırlayın:  
  
- Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.  
  
- Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, `Extensions`adlı tek bir ad alanında uzantı yöntemlerini içeren birden fazla statik sınıfınız varsa, bunların hepsi `using Extensions;` yönergesi tarafından kapsama alınır.  
  
 Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Paralel programlama örnekleri (bunlar birçok örnek genişletme yöntemi içerir)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda İfadeleri](../statements-expressions-operators/lambda-expressions.md)
- [Standart Sorgu İşleçlerine Genel Bakış](../concepts/linq/standard-query-operators-overview.md)
- [Örnek parametreleri ve bunların etkileri için dönüştürme kuralları](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Diller arasında uzantı yöntemleri birlikte çalışabilirliği](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Uzantı yöntemleri ve curried temsilciler](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Uzantı yöntemi bağlama ve hata raporlama](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
