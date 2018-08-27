---
title: Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)
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
ms.openlocfilehash: b0963457e22bf0c3fc92d33c5ed0eb699be27cf7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932048"
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
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler  
 Yöntemi, oluşturucu, dizin oluşturucu veya temsilci tanımı parametreleri gerekli veya isteğe bağlı belirtebilirsiniz. Tüm çağrıların tüm gerekli parametrelerin bağımsız değişkenleri belirtmeniz gerekir, ancak isteğe bağlı parametrelerin bağımsız değişkenleri atlayabilirsiniz.  
  
 Her isteğe bağlı parametre bir varsayılan değeri kendi tanımının bir parçası olarak bulunur. Bu parametre için hiçbir bağımsız değişken gönderirse, varsayılan değer kullanılır. Varsayılan değer ifadelerin aşağıdaki türlerden biri olmalıdır:  
  
-   sabit bir ifade;  
  
-   bir ifade formun `new ValType()`burada `ValType` bir değer türü olduğu gibi bir [enum](../../../csharp/language-reference/keywords/enum.md) veya bir [yapı](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   bir ifade formun [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)burada `ValType` bir değer türüdür.  
  
 İsteğe bağlı parametreler tüm gerekli parametrelerden sonra parametre listesinin sonunda tanımlanır. Çağıran, isteğe bağlı parametreler izleyenler herhangi biri için bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenleri sağlamanız gerekir. Bağımsız değişken listesini virgülle ayrılmış boşlukları desteklenmez. Örneğin, aşağıdaki kodda, yöntem örnek `ExampleMethod` bir gerekli ve isteğe bağlı parametrelerden ile tanımlanır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 Aşağıdaki çağrı `ExampleMethod` üçüncü parametresi için kullanılabilir ancak ikinci bağımsız değişken sağlandığından bir derleyici hatasına neden olur.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Üçüncü parametre adını biliyorsanız, bu görevi gerçekleştirmek için bir adlandırılmış bağımsız değişkeni kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense ayraçlar isteğe bağlı parametreleri belirtmek için aşağıdaki çizimde gösterildiği gibi kullanır.  
  
 ![Hızlı bilgi ExampleMethod yöntemi için IntelliSense. ](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
ExampleMethod isteğe bağlı parametreler  
  
> [!NOTE]
>  .NET kullanarak isteğe bağlı parametreler bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfı. `OptionalAttribute` parametre bir varsayılan değer gerektirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Oluşturucusu `ExampleClass` isteğe bağlı olduğu bir parametresi vardır. Örnek yöntemi `ExampleMethod` bir gerekli parametresi `required`ve isteğe bağlı parametrelerden `optionalstr` ve `optionalint`. Kodda `Main` , yöntem ve oluşturucu çağrılacak farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>COM arabirimleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneleri ve diğer geliştirmeler desteği yanı sıra Office Otomasyon API'leri gibi COM API'leri ile birlikte çalışabilirlik büyük ölçüde geliştirebilirsiniz.  
  
 Örneğin, [AutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) Microsoft Office Excel yönteminde [aralığı](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) arabirimi tümü isteğe bağlı olan yedi parametreleri vardır. Bu parametreler aşağıdaki çizimde gösterilmektedir.  
  
 ![AutoFormat yöntemi için hızlı bilgi IntelliSense. ](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
AutoFormat parametreleri  
  
 C# 3.0 ve önceki sürümlerde, bağımsız değişken aşağıdaki örnekte gösterildiği gibi her parametre için gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 Ancak, büyük ölçüde çağrısı basitleştirebilirsiniz `AutoFormat` C# 4.0 sunulan adlandırılmış ve isteğe bağlı bağımsız değişkenler, kullanarak. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değeri değiştirmek istemiyorsanız, isteğe bağlı parametresi için bağımsız değişkeni atlamak etkinleştirin. Aşağıdaki çağrıda yedi parametreleri yalnızca biri için bir değer belirtilirse.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Daha fazla bilgi ve örnekler için bkz [nasıl yapılır: Office programlama isteğe bağlı bağımsız değişkenler adlandırılmış kullanma ve](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) ve [nasıl yapılır: erişim Office birlikte çalışma nesnelerine kullanarak olan Visual C# özellikleri tarafından](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanımını aşırı yükleme çözünürlüğü aşağıdaki şekillerde etkiler:  
  
-   Yöntem, dizin oluşturucu veya Oluşturucu bir aday yürütme için kendi parametrelerinin her biri, isteğe bağlı olduğunu veya karşılık gelen, adına veya konumuna çağrı deyimindeki tek bir bağımsız değişken ve bağımsız değişken, parametre türüne dönüştürülebilen olur.  
  
-   Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözünürlüğü kuralları açıkça belirtilen bağımsız değişkenler için uygulanır. İsteğe bağlı parametreler için atlanmış bağımsız değişkenler yoksayılır.  
  
-   İki adayları eşit derecede iyi olmasını materyali çağrıda atlanıp bağımsız değişkenler için isteğe bağlı parametrelere sahip olmayan bir aday için tercih gider. Bu aşırı yükleme çözünürlüğü içinde genel bir tercih daha az parametrelere sahip adayları için bir sonuç olur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Dizin Oluşturucular Kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)
