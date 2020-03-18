---
title: Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler - C# Programlama Kılavuzu
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399814"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
C# 4 adlı ve isteğe bağlı bağımsız değişkenleri tanır. *Adlandırılmış bağımsız değişkenler,* parametre listesindeki parametrenin konumu yerine bağımsız değişkeni parametrenin adı ile ilişkilendirerek belirli bir parametre için bir bağımsız değişken belirtmenizi sağlar. *İsteğe bağlı bağımsız değişkenler,* bazı parametreler için bağımsız değişkenleri atlayabilmenizi sağlar. Her iki teknik de yöntemler, dizin oluşturucular, oluşturucular ve temsilcilerle kullanılabilir.  
  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.  
  
 Adlandırılmış ve isteğe bağlı parametreler, birlikte kullanıldığında, isteğe bağlı parametreler listesinden yalnızca birkaç parametre için bağımsız değişken ler sağlamanızı sağlar. Bu özellik, Microsoft Office Automation API'leri gibi COM arabirimlerine yapılan çağrıları büyük ölçüde kolaylaştırır.  
  
## <a name="named-arguments"></a>Adlandırılmış Bağımsız Değişkenler  
 Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını hatırlama veya arama gereksiniminden sizi kurtarır. Her bağımsız değişken için parametre parametre adı ile belirtilebilir. Örneğin, sipariş ayrıntılarını yazdıran bir işlev (satıcı adı, sipariş numarası & ürün adı gibi) işlev tarafından tanımlanan sırada, konuma göre bağımsız değişkenler gönderilerek standart şekilde çağrılabilir.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Parametrelerin sırasını hatırlamıyor ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Adlandırılmış bağımsız değişkenler, her bağımsız değişkenin neyi temsil ettiğini belirleyerek kodunuzu okunabilirliğini de artırır. Aşağıdaki örnek yöntemde, `sellerName` null veya beyaz boşluk olamaz. Her `sellerName` ikisi `productName` de ve dize türleri olarak, yerine konuma göre bağımsız değişkenler gönderme, bu iki ayrıştırmak ve kodu okuyan herkes için karışıklığı azaltmak için adlandırılmış bağımsız değişkenleri kullanmak mantıklı.
  
 Adlandırılmış bağımsız değişkenler, konumsal bağımsız değişkenler ile kullanıldığında,

- herhangi bir konumsal argüman tarafından takip edilmez, ya da

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _C# 7.2 ile başlayarak,_ doğru pozisyonda kullanılırlar. Aşağıdaki örnekte, parametre `orderNum` doğru konumdadır, ancak açıkça adlandırılmaz.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Adlandırılmış bağımsız değişkenleri izleyen konum dışı bağımsız değişkenler geçersizdir.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bazı ek leriyle birlikte bu bölümden örnekler uygular.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>İsteğe Bağlı Bağımsız Değişkenler  
 Yöntemin, oluşturucunun, dizinin dizinleyicinin veya temsilcinin tanımı, parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir. Herhangi bir çağrı, gerekli tüm parametreler için bağımsız değişkenler sağlamalıdır, ancak isteğe bağlı parametreler için bağımsız değişkenleri atlayabilir.  
  
 Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan değere sahiptir. Bu parametre için bağımsız değişken gönderilmezse, varsayılan değer kullanılır. Varsayılan değer aşağıdaki ifade türlerinden biri olmalıdır:  
  
- sabit bir ifade;  
  
- formun `new ValType()`bir ifadesi `ValType` , bir değer türü, bir [enum](../../language-reference/builtin-types/enum.md) veya [bir yapı](../../language-reference/builtin-types/struct.md)gibi;  
  
- form [varsayılan (ValType)](../../language-reference/operators/default.md)bir ifade `ValType` , bir değer türü dür.  
  
 İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanır. Arayan, ardışık isteğe bağlı parametrelerden herhangi biri için bir bağımsız değişken sağlarsa, önceki tüm isteğe bağlı parametreler için bağımsız değişkenler sağlaması gerekir. Bağımsız değişken listesindeki virgülden ayrılmış boşluklar desteklenmez. Örneğin, aşağıdaki kodda, örnek `ExampleMethod` yöntemi bir gerekli ve iki isteğe bağlı parametrelerile tanımlanır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Üçüncü parametre `ExampleMethod` için bir bağımsız değişken sağlandığı, ancak ikinci parametre için sağlanmadığından, derleyici hatasına neden olan aşağıdaki çağrı.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bir bağımsız değişken kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense, aşağıdaki resimde gösterildiği gibi isteğe bağlı parametreleri belirtmek için parantez kullanır:  
  
 ![ExampleMethod yöntemi için IntelliSense hızlı bilgi gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> İsteğe bağlı parametreleri .NET <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfını kullanarak da bildirebilirsiniz. `OptionalAttribute`parametreler varsayılan değer gerektirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, kurucunun `ExampleClass` isteğe bağlı bir parametresi vardır. Örnek `ExampleMethod` yönteminin bir gerekli `required`parametresi ve `optionalstr` `optionalint`iki isteğe bağlı parametresi vardır ve . Kod, `Main` oluşturucu ve yöntemin çağrılabileceği farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>COM Arayüzleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler için destekle birlikte, Office Automation API'leri gibi COM API'leri ile birlikte çalışabilirliği büyük ölçüde artırır.  
  
 Örneğin, Microsoft <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır ve bunların tümü isteğe bağlıdır. Bu parametreler aşağıdaki resimde gösterilmiştir:  
  
 ![AutoFormat yöntemi için IntelliSense hızlı bilgi gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 C# 3.0 ve önceki sürümlerde, aşağıdaki örnekte gösterildiği gibi, her parametre için bir bağımsız değişken gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Ancak, C# 4.0'da tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak aramayı `AutoFormat` büyük ölçüde basitleştirebilirsiniz. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız, bağımsız değişkeni isteğe bağlı bir parametre için atabilmenizi sağlar. Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Daha fazla bilgi ve örnek için, [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenlerin nasıl kullanılacağı](./how-to-use-named-and-optional-arguments-in-office-programming.md) ve [C# özelliklerini kullanarak Office interop nesnelerine nasıl](../interop/how-to-access-office-onterop-objects.md)erişilir'e bakın.  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanımı aşırı yük çözümünü aşağıdaki şekillerde etkiler:  
  
- Parametrelerinin her biri isteğe bağlı ysa veya ada veya konuma göre, çağrı deyimindeki tek bir bağımsız değişkene karşılık gelen ve bu bağımsız değişken parametre türüne dönüştürülebiliyorsa, bir yöntem, dizin oluşturucu veya oluşturucu yürütme için adaydır.  
  
- Birden fazla aday bulunursa, tercih edilen dönüşümler için aşırı yükleme çözümleme kuralları açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için atlanan bağımsız değişkenler yoksayılır.  
  
- İki adayın eşit derecede iyi olduğuna karar vereliise, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametrelere sahip olmayan bir adaya gider. Bu, daha az parametreye sahip adaylar için aşırı yük çözümünde genel bir tercihin sonucudur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Oluşturucuları Kullanma](./using-constructors.md)
- [Dizin Oluşturucular Kullanma](../indexers/using-indexers.md)
