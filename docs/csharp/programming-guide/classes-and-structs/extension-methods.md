---
title: Uzatma Yöntemleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: ce35ef4d4286310aa6c8b6e40c3a448b0d91ea7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937518"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)
Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri özel bir statik yöntem türüdür, ancak bunlar genişletilmiş türdeki örnek yöntemler ise çağrılır. C#, F# ve Visual Basic ile yazılmış istemci kodu için, uzantı yöntemini çağırmakla bir türde gerçekte tanımlanan yöntemler arasında belirgin bir fark yoktur.  
  
 En yaygın uzantı yöntemleri, varolan <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türleri sorgu işlevselliği eklemek LINQ standart sorgu işleçleridir. Standart sorgu işleçlerini kullanmak için, önce `using System.Linq` bunları bir yönergeyle kapsama getirin. <xref:System.Collections.Generic.IEnumerable%601> Sonra uygular herhangi bir tür <xref:System.Linq.Enumerable.GroupBy%2A>gibi örnek yöntemleri <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>var gibi görünür , , , ve benzeri. Bu ek yöntemleri IntelliSense deyiminin tamamlanmasında <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.List%601> <xref:System.Array>görebilirsiniz.  
  
 Aşağıdaki örnek, bir arasyağı `OrderBy` dizisinde standart sorgu işleci yönteminin nasıl çağrılmasını gösterir. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleçleri, lambda ifadeleri parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için [Lambda İfadeleri'ne](../statements-expressions-operators/lambda-expressions.md)bakın.  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametre, yöntemin hangi türde çalıştığını belirtir ve parametre [bu](../../language-reference/keywords/this.md) değiştiriciden önce gelir. Uzantı yöntemleri yalnızca bir `using` yönergeyle ad alanını kaynak kodunuza açıkça aktardığınızda kapsam içindedir.  
  
 Aşağıdaki örnek, sınıf için tanımlanan <xref:System.String?displayProperty=nameWithType> bir uzantı yöntemini gösterir. Bunun iç içe ve genel olmayan bir statik sınıf içinde tanımlandığına dikkat edin:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Uzatma `WordCount` yöntemi bu `using` yönerge ile kapsamına getirilebilir:  
  
```csharp  
using ExtensionMethods;  
```  
  
 Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Kodunuzda örnek yöntemi sözdizimini ile genişletme yöntemi çağırırsınız. Ancak derleyici tarafından üretilen ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Bu nedenle, kapsülleme ilkesi gerçekten ihlal edilmez. Aslında genişletme yöntemleri, genişletildikleri türde özel değişkenlere erişemez.  
  
 Daha fazla bilgi için, [özel bir uzantı yöntemini nasıl uygulayacağı ve çağıracağı hakkında](./how-to-implement-and-call-a-custom-extension-method.md)bilgi.
  
 Genel olarak, büyük olasılıkla kendinizinkileri uygulamayla kıyaslandığında genişletme yöntemlerini çok daha arayacaksınız. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için uzantı yöntemlerini etkinleştirmek için, yöntemlerin tanımlandığı ad alanı için bir `using` yönerge eklemeniz gereken bir yönerge eklemeniz gerek. Örneğin, standart sorgu işleçlerini kullanmak `using` için bu yönergeyi kodunuza ekleyin:  
  
```csharp  
using System.Linq;  
```  
  
 (System.Core.dll adresine de bir başvuru eklemeniz gerekebilir.) Standart sorgu operatörlerinin artık IntelliSense'de çoğu <xref:System.Collections.Generic.IEnumerable%601> tür için kullanılabilir ek yöntemler olarak göründüğünü fark edeceksiniz.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama  
 Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Başka bir deyişle, bir tür `Process(int i)`de adlı bir yöntem varsa ve aynı imzaile bir uzantı yönteminiz varsa, derleyici her zaman örnek yönteme bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf, `Extensions` uygulayan herhangi bir tür `IMyInterface`için tanımlanan uzantı yöntemleri içerir. Sınıflar `A` `B`ve `C` tüm arabirimi uygulayın.  
  
 Ad `MethodB` ve imzası sınıflar tarafından zaten uygulanan yöntemlerle eşleştin, çünkü uzantı yöntemi asla çağrılmaz.  
  
 Derleyici eşleştirilen imzayla bir oluşum yöntemi bulamadığında, varsa, eşleşen bir uzantı yöntemini bağlayın.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 Genel olarak, genişletme yöntemlerini tutumlu ve yalnızca gerektiğinde uygulamanızı öneririz. Mümkün olduğunda, varolan türü genişletmesi gereken istemci kodu, bunu varolan türden türetilmiş yeni bir tür oluşturarak yapmalıdır. Daha fazla bilgi için [Bkz. Kalıtım.](./inheritance.md)  
  
 Kaynak kodunu değiştiremediğiniz bir türü genişletmek üzere genişletme yöntemini kullanırsanız, türün uygulanmasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olabileceği riskini göze alırsınız.  
  
 Belirli bir tür için uzantı yöntemleri uygularsanız, aşağıdaki noktaları unutmayın:  
  
- Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.  
  
- Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlandırılmış `Extensions`tek bir ad alanında uzantı yöntemleri içeren birden çok statik sınıfınvarsa, bunların tümü `using Extensions;` yönerge tarafından kapsamına getirilir.  
  
 Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için [Montaj Sürümü'ne](../../../standard/assembly/versioning.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Paralel Programlama Örnekleri (bunlar birçok örnek uzantı yöntemi içerir)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda İfadeler](../statements-expressions-operators/lambda-expressions.md)
- [Standart Sorgu İşleçlerine Genel Bakış](../concepts/linq/standard-query-operators-overview.md)
- [Örnek parametreleri ve etkileri için dönüşüm kuralları](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Uzantı yöntemleri Diller arasında birlikte çalışabilirlik](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Uzatma yöntemleri ve Curried Delegeler](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Uzatma yöntemi Bağlama ve Hata raporlama](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
