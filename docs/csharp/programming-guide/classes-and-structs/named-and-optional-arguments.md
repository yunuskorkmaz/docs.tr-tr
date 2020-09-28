---
title: Adlandırılmış ve Isteğe bağlı bağımsız değişkenler-C# Programlama Kılavuzu
description: C# ' de adlandırılmış bağımsız değişkenler, konum değil, ada göre bağımsız değişkenleri belirtir. İsteğe bağlı bağımsız değişkenler atlanabilir.
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
ms.openlocfilehash: 4c9c932e3df4035024c90e92e4d80309fffe3ce3
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406238"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler (C# Programlama Kılavuzu)

C# 4 adlandırılmış ve isteğe bağlı bağımsız değişkenleri tanıtır. *Adlandırılmış bağımsız değişkenler* , bağımsız değişkenini parametre listesindeki konumuyla değil, adıyla eşleştirerek bir parametre için bir bağımsız değişken belirtmenizi sağlar. *Isteğe bağlı bağımsız değişkenler* bazı parametrelerin bağımsız değişkenlerini atlamanızı sağlar. Her iki yöntem de Yöntemler, Dizin oluşturucular, oluşturucular ve temsilcilerle birlikte kullanılabilir.

Adlandırılmış ve isteğe bağlı bağımsız değişkenler kullandığınızda, bağımsız değişkenler parametre listesinde değil, bağımsız değişken listesinde göründükleri sırada değerlendirilir.

Adlandırılmış ve isteğe bağlı parametreler, seçili parametreler için bağımsız değişkenler vermenizi sağlar. Bu özellik, Microsoft Office Automation API 'Leri gibi COM arabirimlerine yapılan çağrıları büyük ölçüde kolaylaştırır.

## <a name="named-arguments"></a>Adlandırılmış bağımsız değişkenler

Adlandırılmış bağımsız değişkenler, çağrılan yöntemlerin parametre listelerindeki parametrelerin sırasını eşleştirmeden size ücretsizdir. Her bağımsız değişkenin parametresi parametre adı ile belirtilebilir. Örneğin, sipariş ayrıntılarını (örneğin, satıcı adı, sipariş numarası & ürün adı) yazdıran bir işlev, işlev tarafından tanımlanan sırada konuma göre bağımsız değişkenler gönderilerek çağrılabilir.

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

Parametrelerin sırasını hatırlamıyorsanız ancak adlarını biliyorsanız, bağımsız değişkenleri istediğiniz sırada gönderebilirsiniz.

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

Adlandırılmış bağımsız değişkenler, her bir bağımsız değişkenin ne temsil ettiğini tanımlayarak kodunuzun okunabilirliğini de artırır. Aşağıdaki örnek yöntemde `sellerName` null veya boşluk olamaz. Hem hem `sellerName` de `productName` dize türlerdir, konumlarına göre bağımsız değişken göndermek yerine, iki bağımsız değişkeni de kullanarak kodu okuyan kişilerin karışmasını azaltır.
  
Konumsal bağımsız değişkenlerle birlikte kullanıldığında adlandırılmış bağımsız değişkenler şu kadar geçerlidir

- Bunlar, herhangi bir Konumsal bağımsız değişkenle izlenmez veya

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- _C# 7,2 ile başlayarak_, doğru konumda kullanılırlar. Aşağıdaki örnekte, parametresi `orderNum` doğru konumda, ancak açıkça adlandırılmıyor.

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

Herhangi bir sıra dışı adlandırılmış bağımsız değişkeni izleyen Konumsal bağımsız değişkenler geçersiz.

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a>Örnek

Aşağıdaki kod, bu bölümdeki örnekleri bazı ek kişilerle birlikte uygular.  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a>İsteğe bağlı bağımsız değişkenler

Bir yöntem, Oluşturucu, Dizin Oluşturucu ya da temsilcinin tanımı, parametrelerinin gerekli veya isteğe bağlı olarak belirtilebilir. Herhangi bir çağrı gerekli tüm parametrelerin bağımsız değişkenlerini sağlamalıdır, ancak isteğe bağlı parametrelerin bağımsız değişkenlerini atlayabilir.

Her isteğe bağlı parametre, tanımının bir parçası olarak varsayılan bir değer içerir. Bu parametre için bir bağımsız değişken gönderilmezse, varsayılan değer kullanılır. Varsayılan değer, aşağıdaki ifade türlerinden biri olmalıdır:
  
- sabit bir ifade;  
- formun bir ifadesi, `new ValType()` burada `ValType` [enum](../../language-reference/builtin-types/enum.md) veya [struct](../../language-reference/builtin-types/struct.md)gibi bir değer türüdür;
- bir değer türü olan [varsayılan form (ValType)](../../language-reference/operators/default.md)ifadesi `ValType` .

İsteğe bağlı parametreler, gerekli parametrelerden sonra parametre listesinin sonunda tanımlanmıştır. Çağıran isteğe bağlı parametrelerin her biri için bir bağımsız değişken sağlıyorsa, önceki tüm isteğe bağlı parametrelerin bağımsız değişkenlerini sağlamalıdır. Bağımsız değişken listesindeki virgülle ayrılmış boşluklar desteklenmez. Örneğin, aşağıdaki kodda, örnek yöntemi `ExampleMethod` bir gerekli ve iki isteğe bağlı parametre ile tanımlanmıştır.

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

Aşağıdaki çağrı, `ExampleMethod` bir derleyici hatasına neden olur, çünkü üçüncü parametre için bir bağımsız değişken sağlanır, ikincisi için değil.

```csharp
//anExample.ExampleMethod(3, ,4);
```

Ancak, üçüncü parametrenin adını biliyorsanız, görevi gerçekleştirmek için adlandırılmış bağımsız değişkeni kullanabilirsiniz.

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri göstermek için köşeli ayraçları kullanır:

![ExampleMethod yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> .NET sınıfını kullanarak isteğe bağlı parametreler de bildirebilirsiniz <xref:System.Runtime.InteropServices.OptionalAttribute> . `OptionalAttribute` parametreler varsayılan değer gerektirmez.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, için oluşturucusunun `ExampleClass` bir parametresi vardır, bu isteğe bağlıdır. Örnek yönteminde `ExampleMethod` bir gerekli parametre, `required` ve iki isteğe bağlı iki parametre vardır `optionalstr` `optionalint` . İçindeki kod, `Main` oluşturucunun ve yönteminin çağrılabileceği farklı yolları gösterir.

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

Yukarıdaki kod, isteğe bağlı parametrelerin doğru uygulanmadığı bir dizi örnek gösterir. İlki, gereken ilk parametre için bir bağımsız değişkenin sağlanması gerektiğini gösterir.
  
## <a name="com-interfaces"></a>COM arabirimleri

Adlandırılmış ve isteğe bağlı bağımsız değişkenler, dinamik nesneler desteğiyle birlikte, Office Otomasyonu API 'leri gibi COM API 'Leri ile birlikte çalışabilirliği büyük ölçüde geliştirir.

Örneğin, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> arabirimindeki yöntemin yedi parametresi vardır, hepsi isteğe bağlıdır. Bu parametreler aşağıdaki çizimde gösterilmiştir:

![Otomatik biçim yöntemi için IntelliSense hızlı bilgilerini gösteren ekran görüntüsü.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

C# 3,0 ve önceki sürümlerinde, aşağıdaki örnekte gösterildiği gibi her bir parametre için bir bağımsız değişken gereklidir.

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

Ancak, `AutoFormat` C# 4,0 ' de tanıtılan adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanarak çağrısı büyük ölçüde basitleşebilir. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, parametrenin varsayılan değerini değiştirmek istemiyorsanız isteğe bağlı bir parametre için bağımsız değişkenini atlamanızı sağlar. Aşağıdaki çağrıda, yedi parametreden yalnızca biri için bir değer belirtilir.

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

Daha fazla bilgi ve örnek için bkz. [Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](./how-to-use-named-and-optional-arguments-in-office-programming.md) ve [C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](../interop/how-to-access-office-onterop-objects.md).
  
## <a name="overload-resolution"></a>Aşırı Yükleme Çözümü

Adlandırılmış ve isteğe bağlı bağımsız değişkenlerin kullanılması, aşırı yükleme çözünürlüğünü aşağıdaki yollarla etkiler:

- Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.  
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.
- İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider. Aşırı yükleme çözümlemesi genellikle daha az parametreye sahip adayları tercih eder.
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
