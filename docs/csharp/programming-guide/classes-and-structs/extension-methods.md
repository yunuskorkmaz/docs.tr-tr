---
title: Uzantı Metotları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: bf25ddda2c7e381f0b43798b28179b18338d71cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="extension-methods-c-programming-guide"></a>Uzantı Metotları (C# Programlama Kılavuzu)
Uzantı yöntemleri, yeni türetilmiş bir tür oluşturmadan, yeniden derlemeden ya da özgün türü değiştirmeden yöntemler "eklemenizi" sağlar. Uzantı yöntemleri özel bir statik yöntem türüdür, ancak bunlar genişletilmiş türdeki örnek yöntemler ise çağrılır. C#, F # ve Visual Basic'te yazılmış istemci kodu için bir genişletme yöntemi ve gerçekte bir türde tanımlanan yöntemler çağırma arasında görünen fark yoktur.  
  
 En sık kullanılan uzantı yöntemleri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlevselliği, mevcut eklemek standart sorgu işleçleri <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ve <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türleri. Standart sorgu işleçleri kullanmak için önce bunları kapsamıyla duruma getirmek bir `using System.Linq` yönergesi. Uygulayan sonra herhangi bir türü <xref:System.Collections.Generic.IEnumerable%601> örnek yöntemleri gibi görünüyor <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>ve benzeri. "Nokta" yazdığınızda, IntelliSense deyim tamamlama, bu ek yöntemleri örneği sonra görebilirsiniz bir <xref:System.Collections.Generic.IEnumerable%601> gibi yazın <xref:System.Collections.Generic.List%601> veya <xref:System.Array>.  
  
 Aşağıdaki örnek, standart sorgu işleci çağırmak gösterilmiştir `OrderBy` dizisi yöntemi. Parantez içindeki ifade bir lambda ifadesidir. Birçok standart sorgu işleçleri, lambda ifadeleri parametre olarak alır, ancak bu uzantı yöntemleri için bir gereklilik değildir. Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Uzantı yöntemleri statik yöntemler olarak adlandırılır ancak örnek yöntemi söz dizimi kullanılarak çağrılır. Kendi ilk parametre yöntemi tür çalıştırır ve parametre öncesinde belirtir [bu](../../../csharp/language-reference/keywords/this.md) değiştiricisi. Genişletme yöntemleri ile kaynak kodunuzu içine ad alanını açıkça aktarırken yalnızca kapsamında olan bir `using` yönergesi.  
  
 İçin tanımlanmış bir genişletme yöntemi aşağıdaki örnekte <xref:System.String?displayProperty=nameWithType> sınıfı. Bunun iç içe ve genel olmayan bir statik sınıf içinde tanımlandığına dikkat edin:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` Genişletme yöntemi tıkladığında bu kapsam içine `using` yönergesi:  
  
```  
using ExtensionMethods;  
```  
  
 Ve bu sözdizimi kullanılarak bir uygulamadan çağrılabilir:  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Kodunuzda örnek yöntemi sözdizimini ile genişletme yöntemi çağırırsınız. Ancak derleyici tarafından üretilen ara dil (IL), kodunuzu statik yöntemdeki bir çağrıya dönüştürür. Bu nedenle, kapsülleme ilkesi gerçekten ihlal edilmez. Aslında genişletme yöntemleri, genişletildikleri türde özel değişkenlere erişemez.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: uygulama ve özel uzantı metodu çağırma](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Genel olarak, büyük olasılıkla kendinizinkileri uygulamayla kıyaslandığında genişletme yöntemlerini çok daha arayacaksınız. Genişletme yöntemleri örnek yöntem sözdizimi tarafından çağrıldığından istemci kodundan kullanmak için herhangi bir özel bilgi gerekli değildir. Belirli bir tür için genişletme yöntemleri etkinleştirmek için yalnızca Ekle bir `using` yöntemleri tanımlanır ad alanı için yönerge. Örneğin, standart sorgu işleçleri kullanmak için bu ekleyin `using` kodunuza yönerge:  
  
```  
using System.Linq;  
```  
  
 (System.Core.dll öğesine başvuru eklemeniz gerekebilir.) Standart sorgu işleçleri şimdi IntelliSense içinde ek yöntemleri kullanılabilir çoğu için olarak göründüğünü fark edeceksiniz <xref:System.Collections.Generic.IEnumerable%601> türleri.  
  
> [!NOTE]
>  Standart sorgu işleçleri için IntelliSense görünmez rağmen <xref:System.String>, hala kullanılabilir.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Derleme Zamanında Uzantı Yöntemleri Bağlama  
 Bir sınıfı veya arabirimi genişletmek için genişletme yöntemini kullanabilir, ancak bunları geçersiz kılamazsınız. Arabirim veya sınıf yöntemiyle aynı ada ve imzaya sahip genişletme yöntemi asla çağrılmaz. Derleme sırasında genişletme yöntemleri, her zaman türün kendisinde tanımlı örnek yöntemlerden daha düşük önceliğe sahiptir. Diğer bir deyişle, bir tür değilse sahip bir yöntem adlı `Process(int i)`ve bir genişletme yöntemi ile aynı imzaya sahip, derleyicinin her zaman için örnek yöntemi bağlarsınız. Derleyici bir yöntem çağırmayla karşılaştığında, türün örnek yöntemleri önce bir eşleşme arar. Eşleşme bulunmazsa, tür için tanımlanan uzantı yöntemleri aranır ve ilk bulunan uzantı yöntemine bağlanılır. Aşağıdaki örnek, derleyicinin hangi genişletme yöntemine veya örnek yöntemine bağlanılacağını nasıl belirlediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# derleyicisinin bir yöntem çağrısını türde bir örnek yöntemine mi yoksa bir genişletme yöntemine mi bağlayacağını belirlemede izlediği kuralları gösterir. Statik sınıf `Extensions` uygulayan herhangi bir türü için tanımlı genişletme yöntemleri içeren `IMyInterface`. Sınıfları `A`, `B`, ve `C` tüm arabirimini uygular.  
  
 `MethodB` Genişletme yöntemi adını ve imza zaten sınıfları tarafından uygulanan yöntemleri tam olarak aynı olduğundan hiçbir zaman çağrılır.  
  
 Derleyici eşleştirilen imzayla bir oluşum yöntemi bulamadığında, varsa, eşleşen bir uzantı yöntemini bağlayın.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Genel Yönergeler  
 Genel olarak, genişletme yöntemlerini tutumlu ve yalnızca gerektiğinde uygulamanızı öneririz. Mümkün olduğunda, varolan türü genişletmesi gereken istemci kodu, bunu varolan türden türetilmiş yeni bir tür oluşturarak yapmalıdır. Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Kaynak kodunu değiştiremediğiniz bir türü genişletmek üzere genişletme yöntemini kullanırsanız, türün uygulanmasındaki bir değişikliğin genişletme yönteminizin kesilmesine neden olabileceği riskini göze alırsınız.  
  
 Belirtilen tür için genişletme yöntemleri uygularsanız, aşağıdaki hususları unutmayın:  
  
-   Türden tanımlı yöntemle aynı imzaya sahip değilse genişletme yöntemi asla çağrılmaz.  
  
-   Uzantı yöntemleri ad alanı seviyesinde kapsama alınır. Örneğin, adlı tek bir ad alanı uzantı yöntemleri içeren birden çok statik sınıflar varsa `Extensions`, bunlar tüm kapsam tarafından içine gidersiniz `using Extensions;` yönergesi.  
  
 Uygulanan bir sınıf kitaplığı için derleme sürüm numarasının artıyor olmasını önlemek için uzantı yöntemleri kullanmamanız gerekir. Kaynak koduna sahip olduğunuz kitaplığa önemli işlevsellik eklemek isterseniz, derleme sürüm oluşturma için standart .NET Framework yönergelerini izlemeniz gerekir. Daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Paralel Programlama örnekleri (bunlar, birçok örnek genişletme yöntemleri içerir)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
 [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Standart Sorgu İşleçlerine Genel Bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [Dönüştürme örneği için parametreler ve bunların etkisini kuralları](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)  
 [Diller arasında birlikte çalışabilirlik genişletme yöntemleri](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)  
 [Genişletme yöntemleri ve Curried temsilciler](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)  
 [Genişletme yöntemi bağlama ve hata raporlama](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
