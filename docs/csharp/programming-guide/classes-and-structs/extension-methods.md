---
title: Uzantı yöntemleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 2b5bacfc453f16f9c484eebfddf92c6464f8cb78
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597082"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)
Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri özel bir statik yöntem türüdür, ancak bunlar genişletilmiş türdeki örnek yöntemler ise çağrılır. F# Ve Visual Basic yazılmış C#istemci kodu için, bir uzantı yöntemi çağırma ile gerçekte bir tür içinde tanımlanan Yöntemler arasında görünür bir fark yoktur.  
  
 En yaygın genişletme yöntemleri, var [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <xref:System.Collections.IEnumerable?displayProperty=nameWithType> olan ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türlerine sorgu işlevselliği ekleyen standart sorgu işleçleridir. Standart sorgu işleçlerini kullanmak için, önce bunları bir `using System.Linq` yönergeyle kapsama taşıyın. Ardından <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.Enumerable.GroupBy%2A>, uygulayan herhangi bir tür, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>,, vb. gibi örnek yöntemlere sahip olacak şekilde görünür. <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IEnumerable%601> Ya<xref:System.Array>da gibi bir türün örneğinden sonra "nokta" yazdığınızda, bu ek yöntemleri IntelliSense deyimin tamamlanmasına bakabilirsiniz.  
  
 Aşağıdaki örnek, bir tamsayı dizisinde standart sorgu işleci `OrderBy` yönteminin nasıl çağrılacağını gösterir. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleçleri, lambda ifadeleri parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametresi, yöntemin hangi tür üzerinde çalıştığını belirtir ve parametresi [bundan önce bu](../../language-reference/keywords/this.md) değiştiriciden gelir. Uzantı yöntemleri yalnızca bir `using` yönergeyle ad alanını kaynak kodunuza açıkça aktardığınızda kapsam içinde bulunur.  
  
 Aşağıdaki örnek, <xref:System.String?displayProperty=nameWithType> sınıfı için tanımlanmış bir uzantı yöntemini gösterir. Bunun iç içe ve genel olmayan bir statik sınıf içinde tanımlandığına dikkat edin:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Genişletme yöntemi bu `using` yönergeyle kapsama getirilebilir: `WordCount`  
  
```csharp  
using ExtensionMethods;  
```  
  
 Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Kodunuzda örnek yöntemi sözdizimini ile genişletme yöntemi çağırırsınız. Ancak derleyici tarafından üretilen ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Bu nedenle, kapsülleme ilkesi gerçekten ihlal edilmez. Aslında genişletme yöntemleri, genişletildikleri türde özel değişkenlere erişemez.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel bir genişletme yöntemi](./how-to-implement-and-call-a-custom-extension-method.md)uygulayın ve çağırın.  
  
 Genel olarak, büyük olasılıkla kendinizinkileri uygulamayla kıyaslandığında genişletme yöntemlerini çok daha arayacaksınız. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için uzantı yöntemlerini etkinleştirmek için, yöntemlerin tanımlandığı ad `using` alanı için bir yönerge eklemeniz yeterlidir. Örneğin, standart sorgu işleçlerini kullanmak için bu `using` yönergeyi kodunuza ekleyin:  
  
```csharp  
using System.Linq;  
```  
  
 (System.Core.dll öğesine başvuru eklemeniz gerekebilir.) Standart sorgu işleçlerinin artık, çoğu <xref:System.Collections.Generic.IEnumerable%601> tür için kullanılabilen ek yöntemler olarak IntelliSense 'de göründüğünü fark edeceksiniz.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama  
 Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Diğer bir deyişle, bir türün adlı `Process(int i)`bir yöntemi varsa ve aynı imzaya sahip bir uzantı yönteminiz varsa, derleyici her zaman örnek yöntemine bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf `Extensions` , uygulayan `IMyInterface`her tür için tanımlanmış genişletme yöntemleri içerir. Sınıfları `A`, `B` ve`C` All arabirimini uygular.  
  
 Ad ve imza, sınıflar tarafından zaten uygulanmış yöntemlerle tam olarak eşleştiğinden, genişletmeyöntemihiçbirşekildeçağrılmaz.`MethodB`  
  
 Derleyici eşleştirilen imzayla bir oluşum yöntemi bulamadığında, varsa, eşleşen bir uzantı yöntemini bağlayın.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 Genel olarak, genişletme yöntemlerini tutumlu ve yalnızca gerektiğinde uygulamanızı öneririz. Mümkün olduğunda, varolan türü genişletmesi gereken istemci kodu, bunu varolan türden türetilmiş yeni bir tür oluşturarak yapmalıdır. Daha fazla bilgi için bkz. [Devralma](./inheritance.md).  
  
 Kaynak kodunu değiştiremediğiniz bir türü genişletmek üzere genişletme yöntemini kullanırsanız, türün uygulanmasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olabileceği riskini göze alırsınız.  
  
 Belirli bir tür için uzantı yöntemleri uygularsanız, aşağıdaki noktaları hatırlayın:  
  
- Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.  
  
- Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlı `Extensions`tek bir ad alanında uzantı yöntemlerini içeren birden fazla statik sınıfınız varsa, bunların hepsi `using Extensions;` yönergeyle kapsam haline getirilir.  
  
 Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../framework/app-domains/assembly-versioning.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Paralel programlama örnekleri (bunlar birçok örnek genişletme yöntemi içerir)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Lambda İfadeleri](../statements-expressions-operators/lambda-expressions.md)
- [Standart Sorgu İşleçlerine Genel Bakış](../concepts/linq/standard-query-operators-overview.md)
- [Örnek parametreleri ve bunların etkileri için dönüştürme kuralları](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)
- [Diller arasında uzantı yöntemleri birlikte çalışabilirliği](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)
- [Uzantı yöntemleri ve curried temsilciler](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)
- [Uzantı yöntemi bağlama ve hata raporlama](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
