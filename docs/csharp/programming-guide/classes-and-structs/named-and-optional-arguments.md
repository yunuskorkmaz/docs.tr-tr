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
ms.openlocfilehash: b43c692c8fd54ef1cbfac334b4986d8332462848
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596483"
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
  
 Adlandırılmış bağımsız değişkenler, her bir bağımsız değişkenin ne temsil ettiğini tanımlayarak kodunuzun okunabilirliğini de artırır. Aşağıdaki `sellerName` örnek yöntemde null veya boşluk olamaz. Hem hem `sellerName` de `productName` dize türlerdir, konumlarına göre bağımsız değişken göndermek yerine, iki bağımsız değişkeni de kullanarak kodu okuyan kişilerin karışmasını azaltır.
  
 Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler şu kadar geçerlidir 

- Bunlar, herhangi bir Konumsal bağımsız değişkenle izlenmez veya

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _7,2 ile C# başlayarak_, doğru konumda kullanılırlar. Aşağıdaki örnekte, parametresi `orderNum` doğru konumda, ancak açıkça adlandırılmıyor.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Ancak, daha sonra Konumsal bağımsız değişkenler tarafından izleniyorlarsa, sıra dışı adlandırılmış bağımsız değişkenler geçersizdir.

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
  
- formun `new ValType()`bir ifadesi, burada `ValType` [enum](../../language-reference/keywords/enum.md) veya [struct](./structs.md)gibi bir değer türüdür;  
  
- bir değer türü `ValType` olan [varsayılan form (ValType)](../../language-reference/operators/default.md)ifadesi.  
  
 İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanmıştır. Çağıran isteğe bağlı parametrelerin her biri için bir bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenlerini sağlamalıdır. Bağımsız değişken listesindeki virgülle ayrılmış boşluklar desteklenmez. Örneğin, aşağıdaki kodda, örnek yöntemi `ExampleMethod` bir gerekli ve iki isteğe bağlı parametre ile tanımlanmıştır.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Aşağıdaki çağrı `ExampleMethod` , bir derleyici hatasına neden olur, çünkü üçüncü parametre için bir bağımsız değişken sağlanır, ikincisi için değil.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bağımsız değişkeni kullanabilirsiniz.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri göstermek için köşeli ayraçları kullanır:  
  
 ![ExampleMethod yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  .Net <xref:System.Runtime.InteropServices.OptionalAttribute> sınıfını kullanarak isteğe bağlı parametreler de bildirebilirsiniz. `OptionalAttribute`parametreler varsayılan değer gerektirmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, için `ExampleClass` oluşturucusunun bir parametresi vardır, bu isteğe bağlıdır. Örnek yönteminde `ExampleMethod` bir gerekli parametre `optionalstr` , `required`ve `optionalint`iki isteğe bağlı iki parametre vardır. İçindeki `Main` kod, oluşturucunun ve yönteminin çağrılabileceği farklı yolları gösterir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>COM arabirimleri  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler ve diğer geliştirmeler desteğiyle birlikte, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışabilirliği büyük ölçüde geliştirir.  
  
 Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır, hepsi isteğe bağlıdır. Bu parametreler aşağıdaki çizimde gösterilmiştir:  
  
 ![Otomatik biçim yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 C# 3,0 ve önceki sürümlerde, aşağıdaki örnekte gösterildiği gibi her bir parametre için bir bağımsız değişken gereklidir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Ancak, 4,0 ' de `AutoFormat` C# tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak çağrısını büyük ölçüde kolaylaştırabilirsiniz. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız isteğe bağlı bir parametre için bağımsız değişkenini atlamanızı sağlar. Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Daha fazla bilgi ve örnek için bkz [. nasıl yapılır: Office Programlamada](./how-to-use-named-and-optional-arguments-in-office-programming.md) adlandırılmış ve isteğe bağlı bağımsız değişkenleri ve [nasıl yapılacağını kullanın: Visual C# özelliklerini](../interop/how-to-access-office-onterop-objects.md)kullanarak Office birlikte çalışma nesnelerine erişin.  
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü  
 Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanılması, aşırı yükleme çözünürlüğünü aşağıdaki yollarla etkiler:  
  
- Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.  
  
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.  
  
- İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider. Bu, daha az parametreye sahip adaylar için aşırı yükleme çözünürlüğünde genel bir tercihin sonucudur.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Oluşturucuları Kullanma](./using-constructors.md)
- [Dizin Oluşturucular Kullanma](../indexers/using-indexers.md)
