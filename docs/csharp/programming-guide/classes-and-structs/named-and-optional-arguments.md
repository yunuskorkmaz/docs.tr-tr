---
title: Adlandırılmış ve Isteğe bağlı bağımsız C# değişkenler-Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: 30475b637202d3b614ac968897e467956bc78646
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970515"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
C#4 adlandırılmış ve isteğe bağlı bağımsız değişkenleri tanıtır. *Adlandırılmış bağımsız değişkenler* , bağımsız değişkenini parametrenin adıyla ilişkilendirerek parametre listesindeki konumuyla değil, belirli bir parametre için bir bağımsız değişken belirtmenizi sağlar. *Isteğe bağlı bağımsız değişkenler* bazı parametrelerin bağımsız değişkenlerini atlamanızı sağlar. Her iki yöntem de Yöntemler, Dizin oluşturucular, oluşturucular ve temsilcilerle birlikte kullanılabilir.  
  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.  
  
 Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, isteğe bağlı parametrelerin bir listesinden yalnızca birkaç parametre için bağımsız değişkenler vermenizi sağlar. Bu yetenek, Microsoft Office Automation API 'Leri gibi COM arabirimlerine yönelik çağrıları büyük ölçüde kolaylaştırır.  
  
## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler  
 Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını aramak ya da sağlamak için sizi hatırlamanız ya da aramanız gereksiniminizden muaf değildir. Her bağımsız değişkenin parametresi parametre adı ile belirtilebilir. Örneğin, sipariş ayrıntılarını (örneğin, satıcı adı, sipariş numarası & ürün adı) yazdıran bir işlev, işlev tarafından tanımlanan sırada konuma göre bağımsız değişkenler gönderilerek standart şekilde çağrılabilir.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Parametrelerin sırasını hatırlamıyorsanız ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Adlandırılmış bağımsız değişkenler, her bir bağımsız değişkenin ne temsil ettiğini tanımlayarak kodunuzun okunabilirliğini de artırır. Aşağıdaki örnek yöntemde `sellerName` null veya boşluk olamaz. Hem `sellerName` hem de `productName` dize türlerdir, bu da konuma göre bağımsız değişken göndermek yerine adlandırılmış bağımsız değişkenlerin kullanımını ortadan kaldırmak ve kodu okuyan kişilerin karışmasını azaltmak için anlamlı bir değer sunar.
  
 Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler şu kadar geçerlidir 

- Bunlar, herhangi bir Konumsal bağımsız değişkenle izlenmez veya

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _7,2 ile C# başlayarak_, doğru konumda kullanılırlar. Aşağıdaki örnekte, `orderNum` parametresi doğru konumda, ancak açıkça adlandırılmıyor.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Herhangi bir sıra dışı adlandırılmış bağımsız değişkeni izleyen Konumsal bağımsız değişkenler geçersiz.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bu bölümdeki örnekleri bazı ek kişilerle birlikte uygular.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler  
 Bir yöntem, Oluşturucu, Dizin Oluşturucu veya temsilci tanımı, parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir. Herhangi bir çağrı gerekli tüm parametrelerin bağımsız değişkenlerini sağlamalıdır, ancak isteğe bağlı parametrelerin bağımsız değişkenlerini atlayabilir.  
  
 Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan bir değer içerir. Bu parametre için bir bağımsız değişken gönderilmezse, varsayılan değer kullanılır. Varsayılan değer, aşağıdaki ifade türlerinden biri olmalıdır:  
  
- sabit bir ifade;  
  
- `new ValType()`, `ValType` bir [numaralandırma](../../language-reference/keywords/enum.md) ya da [Yapı](./structs.md)gibi bir değer türü olduğunda formun bir ifadesi;  
  
- [varsayılan form (ValType)](../../language-reference/operators/default.md)bir ifade, burada `ValType` bir değer türüdür.  
  
 İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanmıştır. Çağıran isteğe bağlı parametrelerin her biri için bir bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenlerini sağlamalıdır. Bağımsız değişken listesindeki virgülle ayrılmış boşluklar desteklenmez. Örneğin, aşağıdaki kodda, örnek yöntemi `ExampleMethod` bir zorunlu ve iki isteğe bağlı parametre ile tanımlanmıştır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Aşağıdaki `ExampleMethod` çağrısı bir derleyici hatasına neden olur, çünkü üçüncü parametre için bir bağımsız değişken sağlanır, ikincisi için değil.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bağımsız değişkeni kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri göstermek için köşeli ayraçları kullanır:  
  
 ![ExampleMethod yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> .NET <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfını kullanarak isteğe bağlı parametreler de bildirebilirsiniz. `OptionalAttribute` parametreler için varsayılan değer gerekmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `ExampleClass` oluşturucusunun bir parametresi vardır, bu isteğe bağlıdır. Örnek metodu `ExampleMethod`, bir gerekli parametreye, `required`ve iki isteğe bağlı parametreye sahiptir `optionalstr` ve `optionalint`. `Main` kod, oluşturucunun ve yöntemin çağrılabileceği farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>COM arabirimleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler desteğiyle birlikte, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışabilirliği büyük ölçüde geliştirir.  
  
 Örneğin, Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> yöntemi yedi parametreye sahiptir ve bunların tümü isteğe bağlıdır. Bu parametreler aşağıdaki çizimde gösterilmiştir:  
  
 ![Otomatik biçim yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 C# 3,0 ve önceki sürümlerde, aşağıdaki örnekte gösterildiği gibi her bir parametre için bir bağımsız değişken gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Ancak, 4,0 ' de C# tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak `AutoFormat` çağrısını büyük ölçüde kolaylaştırabilirsiniz. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız isteğe bağlı bir parametre için bağımsız değişkenini atlamanızı sağlar. Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Daha fazla bilgi ve örnek için bkz. [Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: görsel C# özellikler kullanarak Office birlikte çalışma nesnelerine erişme](../interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanılması, aşırı yükleme çözünürlüğünü aşağıdaki yollarla etkiler:  
  
- Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.  
  
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.  
  
- İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider. Bu, daha az parametreye sahip adaylar için aşırı yükleme çözünürlüğünde genel bir tercihin sonucudur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Oluşturucuları Kullanma](./using-constructors.md)
- [Dizin Oluşturucular Kullanma](../indexers/using-indexers.md)
