---
title: Uzantı Metotları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 7ebd04665d91f599edcb4a5c07680216dfb8925a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47233086"
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)
Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri özel bir statik yöntem türüdür, ancak bunlar genişletilmiş türdeki örnek yöntemler ise çağrılır. C#, F # ve Visual Basic'te yazılmış istemci kodu için bir genişletme yöntemi ve gerçekte bir tür içinde tanımlanan yöntemleri çağırma arasında görünür bir fark yoktur.  
  
 En yaygın genişletme yöntemleri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] varolan sorgu işlevselliği ekleyen standart sorgu işleçleri <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türleri. Standart sorgu işleçleri kullanmak için önce bunları kapsama taşıyın bir `using System.Linq` yönergesi. Ardından uygulayan her tür <xref:System.Collections.Generic.IEnumerable%601> örnek yöntemlerine sahip görünür <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri. "Nokta" yazdığınızda IntelliSense deyim tamamlamada bu ek yöntemleri örneğinden sonra gördüğünüz bir <xref:System.Collections.Generic.IEnumerable%601> gibi yazın <xref:System.Collections.Generic.List%601> veya <xref:System.Array>.  
  
 Aşağıdaki örnek, standart sorgu işleci gösterilmektedir `OrderBy` yönteminde tamsayı dizisi. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleçleri, lambda ifadeleri parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. İlk parametreleri hangi tür yöntemin çalıştığını ve parametrenin öncesinde belirtir [bu](../../../csharp/language-reference/keywords/this.md) değiştiricisi. Genişletme yöntemleri ile kaynak kodunuza ad alanını açıkça aldığınızda kapsam içinde olan bir `using` yönergesi.  
  
 Aşağıdaki örnek için tanımlanmış bir uzantı yöntemini gösterir <xref:System.String?displayProperty=nameWithType> sınıfı. Bunun iç içe ve genel olmayan bir statik sınıf içinde tanımlandığına dikkat edin:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` Genişletme yöntemi, bu kapsama alınabilir `using` yönergesi:  
  
```csharp  
using ExtensionMethods;  
```  
  
 Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Kodunuzda örnek yöntemi sözdizimini ile genişletme yöntemi çağırırsınız. Ancak derleyici tarafından üretilen ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Bu nedenle, kapsülleme ilkesi gerçekten ihlal edilmez. Aslında genişletme yöntemleri, genişletildikleri türde özel değişkenlere erişemez.  
  
 Daha fazla bilgi için [nasıl yapılır: özel bir genişletme yöntemi uygulama ve arama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Genel olarak, büyük olasılıkla kendinizinkileri uygulamayla kıyaslandığında genişletme yöntemlerini çok daha arayacaksınız. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir türe ilişkin olarak genişletme yöntemlerini etkinleştirmek için eklemeniz yeterlidir bir `using` yönergesi yöntemlerin tanımlandığı ad alanı. Örneğin, standart sorgu işleçlerini kullanmak için bu ekleme `using` yönergesini kodunuza:  
  
```csharp  
using System.Linq;  
```  
  
 (System.Core.dll öğesine başvuru eklemeniz gerekebilir.) Standart sorgu işleçlerinizin artık IntelliSense'de çoğu kullanılabilen ek yöntemler olarak gösterildiğini fark edeceksiniz <xref:System.Collections.Generic.IEnumerable%601> türleri.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama  
 Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Diğer bir deyişle, bir türü adlı yöntemi `Process(int i)`ve aynı imzaya sahip genişletme yöntemi olması, derleyici her zaman için örnek yöntemine bağlanır. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf `Extensions` uygulayan her tür için tanımlanmış genişletme yöntemleri içerir `IMyInterface`. Sınıflar `A`, `B`, ve `C` tamamı arabirim uygular.  
  
 `MethodB` Genişletme yöntemi asla çağrılmaz çünkü sınıflar tarafından zaten uygulanmış olan yöntemlerle adı ve imzası tam olarak eşleşmesi.  
  
 Derleyici eşleştirilen imzayla bir oluşum yöntemi bulamadığında, varsa, eşleşen bir uzantı yöntemini bağlayın.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 Genel olarak, genişletme yöntemlerini tutumlu ve yalnızca gerektiğinde uygulamanızı öneririz. Mümkün olduğunda, varolan türü genişletmesi gereken istemci kodu, bunu varolan türden türetilmiş yeni bir tür oluşturarak yapmalıdır. Daha fazla bilgi için [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Kaynak kodunu değiştiremediğiniz bir türü genişletmek üzere genişletme yöntemini kullanırsanız, türün uygulanmasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olabileceği riskini göze alırsınız.  
  
 Verilen tür için uzantı yöntemleri uygularken aşağıdaki noktaları unutmayın:  
  
-   Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.  
  
-   Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlı tek bir ad alanında uzantı yöntemlerini içeren birden fazla statik sınıfınız varsa `Extensions`, bunların tümü kapsama göre kapsama dahil edilecektir `using Extensions;` yönergesi.  
  
 Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için [derleme sürümlendirme](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Paralel Programlama örnekleri (bunlar birçok örnek genişletme yöntemleri içerir)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Standart Sorgu İşleçlerine Genel Bakış](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Parametreler ve bunların etkilerine örneği için dönüştürme kuralları](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)  
- [Uzantı yöntemlerinin diller arasında birlikte çalışabilirlik](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)  
- [Uzantı yöntemleri ve Curried temsilciler](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)  
- [Genişletme yöntemi bağlama ve hata raporlama](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
