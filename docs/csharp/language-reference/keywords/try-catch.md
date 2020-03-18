---
title: try-catch - C# Referans
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173477"
---
# <a name="try-catch-c-reference"></a>try-catch (C# Başvurusu)

Try-catch deyimi, farklı `try` özel durumlar için `catch` işleyicileri belirten bir veya daha fazla yan tümcenin izlediği bir bloktan oluşur.

Bir özel durum atıldığında, ortak dil çalışma zamanı `catch` (CLR) bu özel durumu işleyen deyimi arar. Şu anda yürütülen yöntem `catch` böyle bir blok içermiyorsa, CLR geçerli yöntemi denilen yönteme bakar ve böylece çağrı yığınıkadar. Engel `catch` bulunamazsa, CLR kullanıcıya işlenmemiş bir özel durum iletisi görüntüler ve programın yürütülmesini durdurur.

Blok, `try` özel durumlara neden olabilecek korumalı kodu içerir. Bir özel durum atılıncaya veya başarıyla tamamlanana kadar blok yürütülür. Örneğin, bir `null` nesneyi atma girişimi <xref:System.NullReferenceException> özel durumu yükseltir:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

`catch` Yan tümce, herhangi bir özel durum türünü yakalamak için bağımsız değişkenler olmadan kullanılabilse de, bu kullanım önerilmez. Genel olarak, yalnızca nasıl kurtarAcağını bildiğiniz bu özel durumları yakalamanız gerekir. Bu nedenle, her zaman <xref:System.Exception?displayProperty=nameWithType> örneğin türetilen bir nesne bağımsız değişkeni belirtmeniz gerekir:

```csharp
catch (InvalidCastException e)
{
}
```

Aynı try-catch deyiminde `catch` birden fazla belirli yan tümce kullanmak mümkündür. Bu durumda, `catch` `catch` yan tümceler sırayla incelendiğinden, yan tümcelerin sırası önemlidir. Daha az spesifik olanlardan önce daha spesifik özel durumları yakalayın. Derleyici, daha sonraki bir blota asla ulaşılamayacak şekilde yakalama bloklarınızı sipariş ederseniz bir hata üretir.

Bağımsız `catch` değişkenleri kullanmak, işlemek istediğiniz özel durumlara filtre uygulamanın bir yoludur.  Ayrıca, özel durumu işleyip işlememeye karar vermek için daha fazla inceleyen bir özel durum filtresi de kullanabilirsiniz.  Özel durum filtresi yanlış dönerse, işleyici araması devam ediyor.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Özel durum filtreleri, yığından zarar görmeden ayrıldığından, yakalama ve yeniden atma (aşağıda açıklanan) tercih edilir.  Daha sonraki bir işleyici yığını boşaltıyorsa, özel durum aslında nereden geldiğini değil, sadece yeniden atıldığı son yerde görebilirsiniz.  Özel durum filtresi ifadelerinin yaygın kullanımı günlüğe kaydetmedir.  Her zaman bir günlük çıkışları yanlış döndürür bir filtre oluşturabilirsiniz, bunları işlemek ve yeniden atmak zorunda kalmadan gitmek gibi özel durumlar günlüğe kaydedebilirsiniz.

[Bir atma](throw.md) deyimi, deyim `catch` tarafından yakalanan özel durumu yeniden atmak `catch` için bir blokta kullanılabilir. Aşağıdaki örnek, kaynak bilgilerini <xref:System.IO.IOException> bir özel durum ayıklar ve sonra üst yönteme özel durumu atar.

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

Bir özel durum yakalamak ve farklı bir özel durum atabilirsiniz. Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi, iç özel durum olarak yakaladığınız özel durumu belirtin.

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Aşağıdaki örnekte gösterildiği gibi, belirli bir koşul doğru olduğunda da bir özel durum yeniden atabilirsiniz.

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> Benzer bir sonucu genellikle daha temiz bir şekilde elde etmek için bir özel durum filtresi kullanmak da mümkündür (ayrıca, bu belgede daha önce açıklandığı gibi yığını değiştirmeme). Aşağıdaki örnekte, önceki örnekte olduğu gibi arayanlar için benzer bir davranış vardır. İşlev geri `InvalidCastException` yi arayanın `e.Data` geri `null`sini atar.
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

Bir `try` bloğun içinden, yalnızca burada bildirilen değişkenleri başharfe ait hale getiren değişkenler. Aksi takdirde, bloğun yürütülmesi tamamlanmadan önce bir özel durum oluşabilir. Örneğin, aşağıdaki kod örneğinde, `n` değişken bloğun içinde `try` baş harfe doğru başlanır. `Write(n)` İfadedeki `try` bloğun dışında bu değişkeni kullanma girişimi derleyici hatası oluşturur.

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

Catch hakkında daha fazla bilgi için, [try-catch-finally](try-catch-finally.md)bakın.

## <a name="exceptions-in-async-methods"></a>Async yöntemlerindeki özel durumlar

Bir async yöntemi bir [async](async.md) değiştirici tarafından işaretlenir ve genellikle bir veya daha fazla bekleyen ifadeler veya ifadeler içerir. Bekleyen bir ifade, [bekleme](../operators/await.md) işlecini bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.

Denetim async `await` yönteminde bir ulaştığında, yöntemdeki ilerleme beklenen görev tamamlanana kadar askıya alınır. Görev tamamlandığında, yürütme yöntemde devam edebilir. Daha fazla bilgi için, [Async programları ile Asynchronous Programming](../../programming-guide/concepts/async/index.md) bakın ve bekliyor ve [Async Programları Kontrol Akışı.](../../programming-guide/concepts/async/control-flow-in-async-programs.md)

Görev döndüren `await` yöntemde işlenmemiş bir özel durum nedeniyle uygulanan tamamlanmış görev hatalı durumda olabilir. Görevi beklemek bir özel durum oluşturur. Bir görev, iptal edilen eşsenkronize işlem iptal edilirse, iptal edilmiş durumda da sona erebilir. İptal edilmiş bir görevin `OperationCanceledException`bekleyerek bir . Bir eşzamanlı işlemi nasıl iptal edin, [async Uygulamanızı İyi Ayarla](../../programming-guide/concepts/async/fine-tuning-your-async-application.md)hakkında daha fazla bilgi için bkz.

Özel durumu yakalamak için, görevi `try` bir blokta bekleyin ve `catch` ilişkili bloktaki özel durumu yakalayın. Örneğin, [Async yöntemi örnek](#async-method-example) bölümüne bakın.

Beklenen async yönteminde birden çok özel durum oluştuğundan, görev hatalı durumda olabilir. Örneğin, görev <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Böyle bir görevi beklerken, istisnalardan yalnızca biri yakalanır ve hangi özel durum yakalanacak tahmin edemezsiniz. Örneğin, [Task.WhenAll örnek](#taskwhenall-example) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `try` blok bir özel `ProcessString` durum neden olabilir yöntemi için bir çağrı içerir. Yan `catch` tümce, ekranda yalnızca bir ileti görüntüleyen özel durum işleyicisini içerir. `throw` İfade içeriden `MyMethod`çağrıldığında, sistem `catch` deyimi arar ve iletiyi `Exception caught`görüntüler.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>İki catch blokları örnek

Aşağıdaki örnekte, iki catch bloğu kullanılır ve önce gelen en özel özel durum yakalanır.

En az özel özel durumu yakalamak için, `ProcessString` atma deyimini `throw new Exception()`aşağıdaki deyimle değiştirebilirsiniz: .

Örnekte önce en az özel catch bloğunu yerletirseniz, `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`aşağıdaki hata iletisi görüntülenir: .

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Async yöntemi örneği

Aşağıdaki örnekte, async yöntemleri için özel durum işleme gösteriş. Bir async görev atar bir özel durum `await` yakalamak `try` için, bir blok ifade `catch` sini yerleştirin ve bir blokta özel durum yakalamak.

Özel durum `throw new Exception` işlemegöstermek için örnekteki satırı açıklamayı bırakın. Görevin `IsFaulted` özelliği, görevin `True` `Exception.InnerException` özelliği özel durum olarak ayarlanır ve özel durum `catch` blokta yakalanır.

Eşzamanlı bir `throw new OperationCanceledException` işlemi iptal ettiğinizde ne olduğunu göstermek için satırı açıklamayı bırakın. Görevin `IsCanceled` özelliği ayarlanır `true`ve özel durum `catch` blokta yakalanır. Bu örnek için geçerli olmayan bazı koşullar altında, `IsFaulted` görevin `true` özelliği `IsCanceled` ' `false`ne ayarlanır ve .

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task.WhenAll örneği

Aşağıdaki örnekte, birden çok görevin birden çok özel durumla sonuçlandığı özel durum işleme gösterilebilir. Blok, `try` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>'' için yapılan bir çağrıyla döndürülen görevi bekliyor WhenAll'ın uygulandığı üç görev tamamlandığında görev tamamlanır.

Üç görevin her biri bir özel durum neden olur. Blok, `catch` iade `Exception.InnerExceptions` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>edilen görevin özelliğinde bulunan özel durumlar aracılığıyla yinelenir.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [try deyimi](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
