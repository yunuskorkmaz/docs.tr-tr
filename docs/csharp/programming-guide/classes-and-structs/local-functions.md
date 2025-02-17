---
title: Yerel işlevler-C# Programlama Kılavuzu
description: C# ' deki yerel işlevler, başka bir üyede iç içe yerleştirilmiş ve kendi kapsayıcı üyelerinden çağrılabilecek özel yöntemlerdir.
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 1c0cd1b8122f9069e5d6385d698f0ff8278912dd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103250"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# Programlama Kılavuzu)

C# 7,0 ' den başlayarak, c# *Yerel Işlevleri* destekler. Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir. Yalnızca kendi kapsayıcı üyelerinden çağrılabilir. Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:

- Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler
- Oluşturucular
- Özellik erişimcileri
- Olay erişimcileri
- Anonim Yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz. Bir karşılaştırma için bkz [. yerel işlevler ve lambda ifadeleri](#local-functions-vs-lambda-expressions).

Yerel işlevler, kodunuzun amacını açık hale getirir. Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir. Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.

## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır. Tanımı aşağıdaki sözdizimine sahiptir:

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

Aşağıdaki değiştiricileri yerel bir işlevle kullanabilirsiniz:

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) (C# 8,0 ve üzeri sürümlerde). Statik bir yerel işlev yerel değişkenler veya örnek durumu yakalayamaz.
- [`extern`](../../language-reference/keywords/extern.md) (C# 9,0 ve üzeri sürümlerde). Dış yerel işlev olmalıdır `static` .

Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlere statik olmayan bir yerel işlevde erişilebilir.

Bir yöntem tanımının aksine, yerel bir işlev tanımı üye erişim değiştiricisini içeremez. Tüm yerel işlevler özel olduğundan, anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, `private` "özel ' değiştiricisi Bu öğe için geçerli değil."

Aşağıdaki örnek adlı bir yerel işlevi tanımlar `AppendPathSeparator` `GetText` :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

C# 9,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, bir yerel işleve, parametreleri ve tür parametrelerine öznitelikler uygulayabilirsiniz:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

Önceki örnek, null olabilen bir bağlamda statik çözümlemede derleyiciye yardım etmek için [özel bir öznitelik](../../language-reference/attributes/nullable-analysis.md) kullanır.

## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir. Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak. Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir.

Aşağıdaki örnek, `OddSequence` belirtilen aralıktaki tek sayıları numaralandırır bir yöntemi tanımlar. Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden `OddSequence` , yöntemi bir oluşturur <xref:System.ArgumentOutOfRangeException> . Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

Yineleyici mantığını yerel bir işleve yerleştirirseniz, aşağıdaki örnekte gösterildiği gibi, Numaralandırıcı aldığınızda bağımsız değişken doğrulama özel durumları atılır.

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a>Yerel işlevler ve lambda ifadeleri karşılaştırması

İlk bakışta, yerel işlevler ve [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md) çok benzerdir. Birçok durumda, lambda ifadeleri ve yerel işlevler kullanma arasında seçim stili ve kişisel tercihlerden bağımsız olur. Ancak, dikkat etmeniz gereken bir veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.

Bu, yerel işlev ve çarpınımı algoritmasının lambda ifadesi uygulamaları arasındaki farkları inceleyelim. Yerel bir işlev kullanan sürümü aşağıda verilmiştir:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

Bu sürüm lambda ifadeleri kullanır:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a>Adlandırma

Yerel işlevler, yöntemler gibi açıkça adlandırılır. Lambda ifadeleri anonim yöntemlerdir ve `delegate` genellikle veya türler türünde bir türün değişkenlerine atanması gerekir `Action` `Func` . Yerel bir işlev bildirdiğinizde, işlem normal bir yöntem yazmak gibidir; bir dönüş türü ve bir işlev imzası bildirirsiniz.

### <a name="function-signatures-and-lambda-expression-types"></a>İşlev imzaları ve lambda ifadesi türleri

Lambda ifadeleri, `Action` / `Func` bağımsız değişkenini ve dönüş türlerini belirlemekte atanan değişkenin türüne bağlıdır. Yerel işlevlerde, söz dizimi normal bir yöntemi yazarken çok benzer olduğundan, bağımsız değişken türleri ve dönüş türü zaten işlev bildiriminin bir parçasıdır.

### <a name="definite-assignment"></a>Kesin atama

Lambda ifadeleri, çalışma zamanında bildirildiği ve atanan nesnelerdir. Bir lambda ifadesinin kullanılabilmesi için, kesinlikle atanması gerekir: kendisine `Action` / `Func` atanacak olan değişken bildirilmelidir ve kendisine atanmış lambda ifadesi. `LambdaFactorial`Tanımlanmadan önce lambda ifadesini bildirmelidir ve başlatmalıdır `nthFactorial` . Bu nedenle, atamadan önce başvurmak için derleme zamanı hatasına neden `nthFactorial` olur.

Yerel işlevler, derleme zamanında tanımlanır. Değişkenlere atanmadığından, bunlara **kapsamda olduğu** herhangi bir kod konumundan başvurulabilirler; ilk örneğimizde `LocalFunctionFactorial` , deyimin üzerinde veya altında `return` olan ve herhangi bir derleyici hatası tetiklemeyen yerel işlevimizi bildirebiliriz.

Bu farklılıklar özyinelemeli algoritmaların yerel işlevler kullanılarak oluşturulması daha kolay hale gelir. Kendisini çağıran bir yerel işlev tanımlayabilir ve tanımlayabilirsiniz. Lambda ifadeleri, aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için bildirilmelidir ve varsayılan bir değer atanmalıdır.

### <a name="implementation-as-a-delegate"></a>Temsilci olarak uygulama

Lambda ifadeleri, bildirildiği zaman temsilcilere dönüştürülür. Yerel işlevler geleneksel bir yöntem *veya* temsilci olarak yazabildiği için daha esnektir. Yerel işlevler yalnızca temsilci olarak ***kullanıldığında*** temsilcilere dönüştürülür.

Yerel bir işlev bildirirseniz ve yalnızca bir yöntem gibi çağırarak buna başvurmanız durumunda, bir temsilciye dönüştürülmez.

### <a name="variable-capture"></a>Değişken yakalama

[Kesin atamanın](../../../../_csharplang/spec/variables.md#definite-assignment) kuralları, yerel işlev veya lambda ifadesi tarafından yakalanan tüm değişkenleri de etkiler. Derleyici, yerel işlevlerin kapsayan kapsamda kesin olarak yakalanan değişkenleri atamasını sağlayan statik analizler gerçekleştirebilir. Bu örneği ele alalım:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici, `LocalFunction` çağrıldığında kesinlikle atayıp atamayacağını tespit edebilir `y` . , `LocalFunction` Deyimden önce çağrıldığı için `return` , `y` ifadeye kesin olarak atanır `return` .

Yerel bir işlev kapsayan kapsamdaki değişkenleri yakaladığında, yerel işlevin temsilci türü olarak uygulandığını unutmayın.

### <a name="heap-allocations"></a>Yığın ayırmaları

Yerel işlevler, kullanım amaçlarına bağlı olarak, lambda ifadeleri için her zaman gerekli olan yığın ayırmalara engel olabilir. Yerel bir işlev hiçbir şekilde bir temsilciye dönüştürülürse ve yerel işlev tarafından yakalanan değişkenlerden hiçbiri, başka Lambdalar veya temsilcilere dönüştürülen yerel işlevler tarafından yakalanmazsa, derleyici yığın ayırmalara engel olabilir.

Bu zaman uyumsuz örneği göz önünde bulundurun:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

Bu lambda ifadesinin kapanışı `address` , `index` ve `name` değişkenlerini içerir. Yerel işlevler söz konusu olduğunda, kapanışı uygulayan nesne bir `struct` tür olabilir. Bu yapı türü yerel işleve başvuruya göre geçirilir. Uygulamadaki bu fark bir ayırmaya kaydedilir.

Lambda ifadeleri için gereken örnek oluşturma, zaman açısından kritik kod yollarındaki bir performans faktörü olabilecek fazladan bellek ayırmaları anlamına gelir. Yerel işlevler bu ek yüke neden olmaz. Yukarıdaki örnekte, yerel işlevlerin sürümünde lambda ifadesi sürümünden daha az sayıda ayırma vardır.

Yerel işlevinizin bir temsilciye dönüştürülemediğini ve tarafından yakalanan değişkenlerden hiçbirinin, temsilcilere dönüştürülen başka Lambdalar veya yerel işlevler tarafından yakalanıp yakalanmayacağını biliyorsanız, yerel işlevinizin yığın üzerinde yerel bir işlev olarak bildirerek ayrılmasının önleneceğini garanti edebilirsiniz `static` . Bu özelliğin C# 8,0 ve daha yeni sürümlerde kullanılabilir olduğunu unutmayın.

> [!NOTE]
> Bu yöntemin yerel işlev eşdeğeri, kapanış için bir sınıf de kullanır. Yerel bir işlev için Kapanışın bir veya olarak uygulanıp uygulanmadığı bir `class` `struct` uygulama ayrıntısı. Yerel bir işlev bir kullanabilir, `struct` ancak bir lambda her zaman bir kullanır `class` .

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a>`yield`Anahtar sözcüğünün kullanımı

Bu örnekte gösterilmeyen bir son avantaj, yerel işlevlerin yineleyiciler olarak uygulanabilmesinin yanı `yield return` sıra bir değer dizisi oluşturmak için söz dizimini kullanmaktır.

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

`yield return`Lambda ifadelerinde ifadeye izin verilmiyor, bkz. [DERLEYICI hatası CS1621](../../misc/cs1621.md).

Yerel işlevler Lambda ifadelerinde gereksiz gibi görünse de, bu işlemler aslında farklı amaçlara hizmet eder ve farklı kullanımlar sağlar. Yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde yerel işlevler bu durum için daha etkilidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
