---
title: try-catch - C# başvurusu
ms.custom: seodec18
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
ms.openlocfilehash: 28bf939cb7da760400486c52bb07649826628c1c
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422594"
---
# <a name="try-catch-c-reference"></a>try-catch (C# Başvurusu)

Try-catch deyiminin oluşan bir `try` blok izlenen bir veya daha fazla tarafından `catch` farklı özel durumlar için işleyiciler belirten yan tümceleri.

## <a name="remarks"></a>Açıklamalar

Ortak dil çalışma zamanı (CLR) bir özel durum oluştuğunda arar `catch` bu özel durumu işleyen bir ifade. Şu anda yürütülen yöntemi gibi içermiyorsa bir `catch` engelleme, vb. çağrı yığınında yukarı geçerli bir yöntemi çağıran yönteme CLR bakar. Hayır ise `catch` bloğu bulundu ve ardından CLR kullanıcıya bir işlenmeyen özel durum iletisi görüntüler ve programın yürütülmesini durdurur.

`try` Bloğu özel durumuna neden olabilir korunan kodu içerir. Blok, bir özel durum veya başarıyla tamamlanana kadar yürütülür. Aşağıdaki örnek, atama yapmayı bir `null` nesne harekete geçirirse <xref:System.NullReferenceException> özel durum:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

Ancak `catch` yan tümcesi bağımsız değişkenler herhangi bir türde özel durum yakalamak için kullanılabilir, bu kullanım önerilmez. Genel olarak, yalnızca, kurtarılır biliyorsunuz özel durumları yakalamalısınız. Bu nedenle, her zaman türetilen bir nesne bağımsız değişkeni belirtmeniz gerekir <xref:System.Exception?displayProperty=nameWithType> örneğin:

```csharp
catch (InvalidCastException e)
{
}
```

Birden fazla özel kullanmak da mümkündür `catch` aynı try-catch deyiminin yan tümcesi. Bu durumda, sırası `catch` yan tümceleri önemlidir çünkü `catch` yan tümceleri sırayla incelenir. Less yazımına özgü olanlardan önce daha özel istisnaları yakalayın. Böylece bir sonraki bloğuna hiç ulaşılmadı, catch engeller sipariş, derleyici bir hata oluşturur.

Kullanarak `catch` bağımsız değişkenler, işlemek istediğiniz özel durumları filtrelemek için bir yoludur.  Daha fazla uygulayacağınıza karar vermek için özel durum inceleyen bir özel durum filtresi de kullanabilirsiniz.  Ardından, özel durum filtresi false döndürürse, işleyici için arama devam eder.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Özel durum filtreleri yakalama ve filtreleri yaralanmadığı türde yığın bıraktığınızdan (aşağıda anlatıldığı) yeniden atma tercih edilir.  Bir sonraki işleyici yığın dökümleri, nereden özel durumun ilk olarak, bunu döndükten hemen son yer yerine geldiğini görebilirsiniz.  Özel durum filtre ifadeleri yaygın kullanımı günlüğe kaydetme.  Her zaman yeniden oluşturma ve bunları işlemek zorunda kalmadan ilerledikçe özel durumları günlüğe kaydetmek bir günlük için de çıkarır false döndüren bir filtre oluşturabilirsiniz.

A [throw](throw.md) deyimi kullanılabilir bir `catch` blok tarafından yakalanan özel durumu yeniden harekete geçirileceğini `catch` deyimi. Aşağıdaki örnekte kaynak bilgileri ayıklayan bir <xref:System.IO.IOException> özel durum ve ardından üst yöntemi özel durum oluşturur.

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

Bir özel durumu yakalar ve farklı bir özel durum. Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi iç özel durum Yakalanan özel durum belirtin.

```csharp
catch (InvalidCastException e) 
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Belirtilen bir koşul true olduğunda aşağıdaki örnekte gösterildiği gibi ayrıca bir özel durum yeniden oluşturabilecek.

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
> Genellikle daha net bir şekilde (aynı zamanda bu belgede daha önce açıklandığı gibi yığını değiştirme değil) benzer bir sonuç almak için bir özel durum filtresi kullanmak da mümkündür. Aşağıdaki örnek, önceki örnek olarak arayanlar için benzer bir davranış sahiptir. İşlevin `InvalidCastException` çağırana geri olduğunda `e.Data` olduğu `null`.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

Gelen içinde bir `try` sıralamadaki bildirilen değişkenlerini başlatmak, engelleyin. Aksi takdirde, bloğun yürütülmesini tamamlanmadan önce bir özel durum ortaya çıkabilir. Örneğin, aşağıdaki kod örneği, değişken içinde `n` içinde başlatılan `try` blok. Bu değişken dışında kullanma girişimi `try` engelleyin `Write(n)` deyimi bir derleyici hatası üretir.

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

Yakalama hakkında daha fazla bilgi için bkz: [try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Zaman uyumsuz yöntemlerde özel durumları
Zaman uyumsuz bir yöntem tarafından işaretlenen bir [zaman uyumsuz](async.md) değiştiricisi ve genellikle bir içeriyor ya da daha fazla await ifadeler veya deyimler. Await ifadesi geçerli [await](await.md) işleci bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.

Ulaştığında denetlemek bir `await` awaited görevi tamamlanıncaya kadar zaman uyumsuz yöntemin yöntem ediyor askıya alındı. Görev tamamlandığında, yürütme yönteminde devam edebilir. Daha fazla bilgi için [Asynchronous Programming with async ve await](../../programming-guide/concepts/async/index.md) ve [zaman uyumsuz programlarda akış kontrolü](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Tamamlanan görev `await` uygulanan hatalı bir durumda, görev döndüren yöntem içinde işlenmeyen bir özel durum nedeniyle olabilir. Bekleyen görev özel durum oluşturur. Bunu döndüren zaman uyumsuz işlem iptal edilirse bir görev bir iptal edildi durumunda da kalabilirsiniz. Bekleyen iptal edilen bir görev oluşturur bir `OperationCanceledException`. Zaman uyumsuz bir işlem iptal etme hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Özel durum yakalamak için görev await bir `try` engelleyin ve özel durum ilişkili catch `catch` blok. Örneğin, "Örnek" bölümüne bakın.

Beklenen zaman uyumsuz yöntemin birden çok özel durum oluştuğu için bir görev hatalı bir durumda olabilir. Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Böyle bir görevi beklerken, yakalanan özel durumlardan yalnızca birini ve özel durum yakalandı tahmin edemezsiniz. Örneğin, "Örnek" bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `try` bloğu içeren bir çağrı `ProcessString` yönteminin bir özel durumuna neden olabilir. `catch` Yan tümcesi içeren özel durum işleyici, yalnızca ekranda bir ileti görüntüler. Zaman `throw` deyimi çağrılır içindeki `MyMethod`, sistem arar `catch` deyimi ve iletisini görüntüler `Exception caught`.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, iki catch blokları kullanılır ve ilk birlikte gelen en özel durum yakalandı.

En az spesifiğe istisna yakalamak için throw deyiminde değiştirebilirsiniz `ProcessString` şu ifadeyle: `throw new Exception()`.

En az Özel catch bloğu ilk örnekte yerleştirirseniz aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, özel durum işleme için zaman uyumsuz yöntemler gösterilmektedir. Zaman uyumsuz bir görev oluşturan bir özel durum yakalamak için yerleştirin `await` ifadesinde bir `try` blok ve özel durumu bir `catch` blok.

Açıklamadan çıkarın `throw new Exception` özel durum işleme göstermek için örnek satır. Görevin `IsFaulted` özelliği `True`, görevin `Exception.InnerException` özelliği, özel duruma ayarlanır ve özel durum yakalandı `catch` blok.

Açıklamadan çıkarın `throw new OperationCanceledException` zaman uyumsuz bir işlem iptal ettiğinizde ne göstermek için satır. Görevin `IsCanceled` özelliği `true`, ve özel durum yakalandı `catch` blok. Bu örnek için görev ait uygulama bazı koşullar altında `IsFaulted` özelliği `true` ve `IsCanceled` ayarlanır `false`.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel durum işleme birden çok görev içinde birden çok özel durum burada sonuçlanabilir gösterir. `try` Bloğu için bir çağrı tarafından döndürülen görev bekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. WhenAll uygulandığı üç görev tamamlandığında, görev tamamlandıysa.

Her biri üç görev, bir özel durum neden olur. `catch` Blok yinelenir bulunan özel durumlar üzerinden `Exception.InnerExceptions` özelliği tarafından döndürülen görevin <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Nasıl yapılır: Açıkça özel durumlar oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
