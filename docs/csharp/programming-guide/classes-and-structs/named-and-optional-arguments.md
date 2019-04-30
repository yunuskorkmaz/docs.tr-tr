---
title: Adlandırılmış ve isteğe bağlı bağımsız değişkenler - C# Programlama Kılavuzu
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
ms.openlocfilehash: 751f8a0745322e7e8573d392a504ea02cb18572e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646298"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] adlandırılmış ve isteğe bağlı bağımsız değişkenler tanıtır. *Adlandırılmış bağımsız değişkenler* bağımsız değişken parametre adı yerine parametre listesinde parametrenin konumu ile ilişkilendirerek belirli bir parametre için bir bağımsız değişken belirtmenize olanak verir. *İsteğe bağlı bağımsız değişkenlere* bazı parametrelerin bağımsız değişkenleri atlamak sağlar. Her iki tekniği, yöntemleri, Dizinleyicileri, Oluşturucular ve temsilciler ile kullanılabilir.  
  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişken, parametre listesi bağımsız değişken listesinde göründükleri sırayla değerlendirilir.  
  
 Adlandırılmış ve isteğe bağlı parametreler birlikte kullanıldığında, yalnızca birkaç parametreleri isteğe bağlı parametreler için bağımsız değişkenleri sağlar. Bu özellik, Microsoft Office Otomasyon API'leri gibi COM arabirimleri çağrıları büyük ölçüde kolaylaştırır.  
  
## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler  
 Adlandırılmış bağımsız değişkenler unutmayın veya çağrılan yöntemlerin parametre listeleri parametrelerinde sırasını aramak için gereken gelen boş. Parametresi her bağımsız değişkeni için parametre adı belirtilebilir. Örneğin, sipariş ayrıntılarını yazdırır bir işlev (gibi satıcı adı, sipariş numarası & ürün adı) işlev tarafından tanımlanan sırayla konuma göre bağımsız değişken göndererek standart yolla çağrılabilir.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Parametreler sırası hatırlıyor musunuz, ancak adlarını bilmeniz, bağımsız değişkenler herhangi bir sırada gönderebilirsiniz.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Adlandırılmış bağımsız değişkenler de ne her bağımsız değişken temsil eden belirleyerek kodunuzu okunabilirliğini geliştirmek. Aşağıdaki örnek yöntemi içinde `sellerName` null veya boşluk olamaz. Her ikisi de olarak `sellerName` ve `productName` dize türleri, bağımsız değişkenleri konuma göre göndermek yerine, iki belirsizliğinin ortadan kaldırılmasını ve Karışıklığın kodu okuyan herkese adlandırılmış bağımsız değişkenler kullanan mantıklıdır.
  
 Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler, geçerli olduğu sürece 

- hiçbir konumsal bağımsız değişkeni tarafından ardından veya

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _C# 7.2 ile başlayan_, doğru konumda hazırsınız demektir. Parametresi aşağıdaki örnekte `orderNum` doğru konumda olmakla birlikte açıkça adlandırılmış değil.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Ancak, sırası adlandırılmış bağımsız değişkenler konumsal bağımsız değişkenler ardından varsa geçersizdir.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bazı bulunmakla birlikte, bu bölümdeki örnekler uygular.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler  
 Yöntemi, oluşturucu, dizin oluşturucu veya temsilci tanımı parametreleri gerekli veya isteğe bağlı belirtebilirsiniz. Tüm çağrıların tüm gerekli parametrelerin bağımsız değişkenleri belirtmeniz gerekir, ancak isteğe bağlı parametrelerin bağımsız değişkenleri atlayabilirsiniz.  
  
 Her isteğe bağlı parametre bir varsayılan değeri kendi tanımının bir parçası olarak bulunur. Bu parametre için hiçbir bağımsız değişken gönderirse, varsayılan değer kullanılır. Varsayılan değer ifadelerin aşağıdaki türlerden biri olmalıdır:  
  
- sabit bir ifade;  
  
- bir ifade formun `new ValType()`burada `ValType` bir değer türü olduğu gibi bir [enum](../../../csharp/language-reference/keywords/enum.md) veya bir [yapı](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
- bir ifade formun [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)burada `ValType` bir değer türüdür.  
  
 İsteğe bağlı parametreler tüm gerekli parametrelerden sonra parametre listesinin sonunda tanımlanır. Çağıran, isteğe bağlı parametreler izleyenler herhangi biri için bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenleri sağlamanız gerekir. Bağımsız değişken listesini virgülle ayrılmış boşlukları desteklenmez. Örneğin, aşağıdaki kodda, yöntem örnek `ExampleMethod` bir gerekli ve isteğe bağlı parametrelerden ile tanımlanır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Aşağıdaki çağrı `ExampleMethod` üçüncü parametresi için kullanılabilir ancak ikinci bağımsız değişken sağlandığından bir derleyici hatasına neden olur.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Üçüncü parametre adını biliyorsanız, bu görevi gerçekleştirmek için bir adlandırılmış bağımsız değişkeni kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense ayraçlar isteğe bağlı parametreleri belirtmek için aşağıdaki çizimde gösterildiği gibi kullanır:  
  
 ![ExampleMethod yöntemi için hızlı bilgi IntelliSense gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  .NET kullanarak isteğe bağlı parametreler bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfı. `OptionalAttribute` parametre bir varsayılan değer gerektirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Oluşturucusu `ExampleClass` isteğe bağlı olduğu bir parametresi vardır. Örnek yöntemi `ExampleMethod` bir gerekli parametresi `required`ve isteğe bağlı parametrelerden `optionalstr` ve `optionalint`. Kodda `Main` , yöntem ve oluşturucu çağrılacak farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>COM arabirimleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneleri ve diğer geliştirmeler desteği yanı sıra Office Otomasyon API'leri gibi COM API'leri ile birlikte çalışabilirlik büyük ölçüde geliştirebilirsiniz.  
  
 Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel yönteminde <xref:Microsoft.Office.Interop.Excel.Range> arabirimi tümü isteğe bağlı olan yedi parametreleri vardır. Bu parametreler, aşağıdaki çizimde gösterilmiştir:  
  
 ![AutoFormat yöntemi için hızlı bilgi IntelliSense gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 C# 3.0 ve önceki sürümlerde, bağımsız değişken aşağıdaki örnekte gösterildiği gibi her parametre için gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Ancak, büyük ölçüde çağrısı basitleştirebilirsiniz `AutoFormat` C# 4.0 sunulan adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanarak. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değeri değiştirmek istemiyorsanız, isteğe bağlı parametresi için bağımsız değişkeni atlamak etkinleştirin. Aşağıdaki çağrıda yedi parametreleri yalnızca biri için bir değer belirtilirse.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Daha fazla bilgi ve örnekler için bkz. [nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanımını aşırı yükleme çözünürlüğü aşağıdaki şekillerde etkiler:  
  
- Yöntem, dizin oluşturucu veya Oluşturucu bir aday yürütme için kendi parametrelerinin her biri, isteğe bağlı olduğunu veya karşılık gelen, adına veya konumuna çağrı deyimindeki tek bir bağımsız değişken ve bağımsız değişken, parametre türüne dönüştürülebilen olur.  
  
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözünürlüğü kuralları açıkça belirtilen bağımsız değişkenler için uygulanır. İsteğe bağlı parametreler için atlanmış bağımsız değişkenler yoksayılır.  
  
- İki adayları eşit derecede iyi olmasını materyali çağrıda atlanıp bağımsız değişkenler için isteğe bağlı parametrelere sahip olmayan bir aday için tercih gider. Bu aşırı yükleme çözünürlüğü içinde genel bir tercih daha az parametrelere sahip adayları için bir sonuç olur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [Dizin Oluşturucular Kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)
