---
title: try-catch-C# başvurusu
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
ms.openlocfilehash: 4715a27a94ac86c5e4955c0e8be95c6ee4a28507
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619708"
---
# <a name="try-catch-c-reference"></a>try-catch (C# Başvurusu)

Try-catch deyimleri `try` `catch` , farklı özel durumlar için işleyiciler belirten bir veya daha fazla yan tümce tarafından izlenen bir bloğundan oluşur.

Bir özel durum oluştuğunda, ortak dil çalışma zamanı (CLR) `catch` Bu özel durumu işleyen ifadeye bakar. Şu anda yürütülmekte olan yöntem böyle bir `catch` blok içermiyorsa, clr geçerli yöntemi çağıran yönteme bakar ve bu şekilde çağrı yığınını alır. Hiçbir `catch` blok bulunamazsa, clr kullanıcıya işlenmeyen bir özel durum iletisi görüntüler ve programın yürütülmesini engeller.

`try`Blok, özel duruma neden olabilecek korunan kodu içerir. Bir özel durum oluşturuluncaya veya başarıyla tamamlanana kadar blok yürütülür. Örneğin, bir nesneyi atama girişimi şu `null` <xref:System.NullReferenceException> özel durumu oluşturur:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

`catch`Yan tümcesi herhangi bir tür özel durum yakalamak için bağımsız değişken olmadan kullanılabilmesine rağmen, bu kullanım önerilmez. Genel olarak, yalnızca kurtarmayı bildiğiniz özel durumları yakamalısınız. Bu nedenle, her zaman ' dan türetilmiş bir nesne bağımsız değişkeni belirtmeniz gerekir <xref:System.Exception?displayProperty=nameWithType> :

```csharp
catch (InvalidCastException e)
{
}
```

`catch`Aynı try-catch deyimi içinde birden çok özel yan tümce kullanmak mümkündür. Bu durumda, yan tümceler sırasıyla `catch` incelenmediği için yan tümcelerinin sırası önemlidir `catch` . Daha az özel durumları daha az spesifik olanlardan önce yakalayın. Daha sonraki bir bloba ulaşılmaması için catch bloklarını sıralarsanız derleyici bir hata oluşturur.

`catch`Bağımsız değişkenlerin kullanılması, işlemek istediğiniz özel durumları filtrelemek için bir yoldur.  Ayrıca, işleme karar vermek için özel durumu daha ayrıntılı bir şekilde inceleyen bir özel durum filtresi de kullanabilirsiniz.  Özel durum filtresi false döndürürse, işleyici araması devam eder.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Özel durum filtreleri yakalamak ve yeniden oluşturmak tercih edilir (aşağıda açıklanmıştır) çünkü filtreler yığından ayrılmaz.  Daha sonraki bir işleyici yığının dökümünü alıyorsa, özel durumun ilk olarak oluşturulduğu son yerde değil, ilk olarak nereden geldiğini görebilirsiniz.  Özel durum filtre ifadelerinin yaygın kullanımı günlüğe kaydedilir.  Her zaman bir günlüğe çıkış yapan yanlış değeri döndüren bir filtre oluşturabilirsiniz, bunları işlemek ve yeniden oluşturmak zorunda kalmadan, özel durumları bu şekilde günlüğe kaydedebilirsiniz.

[Throw](throw.md) deyimleri `catch` , ifadesiyle yakalanan özel durumu yeniden oluşturmak için bir blokta kullanılabilir `catch` . Aşağıdaki örnek, bir özel durumdan kaynak bilgilerini ayıklar <xref:System.IO.IOException> ve ardından ana yöntemin özel durumunu oluşturur.

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

Bir özel durumu yakalayabilir ve farklı bir özel durum oluşturabilirsiniz. Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi, iç özel durum olarak yakalandığı özel durumu belirtin.

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

Ayrıca, aşağıdaki örnekte gösterildiği gibi, belirli bir koşul true olduğunda bir özel durumu yeniden oluşturabilirsiniz.

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
> Benzer bir sonucu genellikle temizleyici bir şekilde (Bu belgede daha önce açıklandığı gibi, yığın değiştirilmeyen) almak için bir özel durum filtresi kullanmak da mümkündür. Aşağıdaki örnekte, bir önceki örnek olarak çağıranlar için benzer bir davranış vardır. İşlevi, `InvalidCastException` olduğunda çağırana geri dönerek atar `e.Data` `null` .
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

Bir bloğun içinden `try` yalnızca içinde belirtilen değişkenleri başlatın. Aksi takdirde, bloğun yürütülmesi tamamlanmadan önce bir özel durum ortaya çıkabilir. Örneğin, aşağıdaki kod örneğinde değişken `n` blok içinde başlatılır `try` . Bu değişkeni ifadesinde bloğunun dışında kullanma girişimi `try` `Write(n)` bir derleyici hatası oluşturur.

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

Catch hakkında daha fazla bilgi için bkz. [try-catch-finally](try-catch-finally.md).

## <a name="exceptions-in-async-methods"></a>Zaman uyumsuz yöntemlerde özel durumlar

Zaman uyumsuz bir yöntem, [zaman uyumsuz](async.md) bir değiştirici tarafından işaretlenir ve genellikle bir veya daha fazla await ifadesi ya da deyimi içerir. Await ifadesi bir veya ' a [await](../operators/await.md) işlecini uygular <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .

Denetim `await` zaman uyumsuz yöntemde bir ulaştığında, beklenen görev tamamlanana kadar yöntemindeki ilerleme askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir. Daha fazla bilgi için bkz. Async [ve await ile](../../programming-guide/concepts/async/index.md) zaman uyumsuz programlama ve [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Uygulanan tamamlanan görev, `await` görevi döndüren yöntemdeki işlenmeyen bir özel durum nedeniyle hatalı bir durumda olabilir. Görevin bekleniyor bir özel durum oluşturur. Aynı zamanda, döndüren zaman uyumsuz işlem iptal edilirse, bir görev iptal edilmiş durumda da bitebilirler. İptal edilen bir görevin bekleniyor bir oluşturur `OperationCanceledException` . Zaman uyumsuz bir işlemi iptal etme hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Özel durumu yakalamak için, görevi bir `try` blokta bekleve özel durumu ilişkili blokta yakalayacak `catch` . Örneğin, [zaman uyumsuz yöntem örneği](#async-method-example) bölümüne bakın.

Beklenen zaman uyumsuz yöntemde birden çok özel durum oluştuğundan, görev hatalı durumda olabilir. Örneğin, görev bir çağrısının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Böyle bir görevi bekleyettiğinizde, özel durumların yalnızca biri yakalanacaktır ve hangi özel durumun yakalanıp yakalanmayacak olduğunu tahmin edemeyecektir. Bir örnek için, [Task. WhenAll örnek](#taskwhenall-example) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `try` blok bir `ProcessString` özel duruma neden olabilecek metoda bir çağrı içerir. `catch`Yan tümcesi yalnızca ekranda bir ileti görüntüleyen özel durum işleyicisini içerir. `throw`İfade içinden çağrıldığında `ProcessString` , sistem, `catch` ifadeyi arar ve iletiyi görüntüler `Exception caught` .

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>İki catch bloğu örneği

Aşağıdaki örnekte, iki catch bloğu kullanılır ve ilk olarak gelen en özel durum yakalanmalıdır.

En az özel durumu yakalamak için, içindeki throw ifadesini `ProcessString` aşağıdaki deyimle değiştirebilirsiniz: `throw new Exception()` .

Örneğe en az özel catch bloğunu yerleştirirseniz, aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')` .

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Async yöntemi örneği

Aşağıdaki örnek, zaman uyumsuz metotlar için özel durum işlemeyi gösterir. Zaman uyumsuz bir görevin aldığı bir özel durumu yakalamak için, `await` ifadeyi bir blok içine yerleştirin `try` ve özel durumu bir `catch` blokta yakalayın.

`throw new Exception`Özel durum işlemeyi göstermek için örnekteki satırın açıklamasını kaldırın. Görevin `IsFaulted` özelliği olarak ayarlanır `True` , görevin `Exception.InnerException` özelliği özel duruma ayarlanır ve özel durum `catch` bloğunda yakalanır.

`throw new OperationCanceledException`Zaman uyumsuz bir işlemi iptal ettiğinizde ne olacağını göstermek için çizginin açıklamasını kaldırın. Görevin `IsCanceled` özelliği olarak ayarlanır `true` ve özel durum `catch` bloğunda yakalanır. Bu örnek için geçerli olmayan bazı koşullar altında, görevin `IsFaulted` özelliği olarak ayarlanır `true` ve `IsCanceled` olarak ayarlanır `false` .

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task. WhenAll örneği

Aşağıdaki örnekte, birden çok görevin birden çok özel durum ile sonuçlanbildiği özel durum işleme gösterilmektedir. `try`Blok, çağrısı tarafından döndürülen görevi bekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Bu görev, WhenAll 'un uygulandığı üç görev tamamlandığında tamamlanmıştır.

Üç görevin her biri özel duruma neden olur. `catch`Blok, `Exception.InnerExceptions` tarafından döndürülen görevin özelliğinde bulunan özel durumlar boyunca yinelenir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
