---
title: Try-Catch- C# Reference
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
ms.openlocfilehash: 5289dbe3aff0a9e1f1024a293ff469df44d34a3b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713033"
---
# <a name="try-catch-c-reference"></a>try-catch (C# Başvurusu)

Try-catch deyimleri, farklı özel durumlar için işleyiciler belirten bir veya daha fazla `catch` yan tümcesi tarafından izlenen bir `try` bloğundan oluşur.

Bir özel durum oluştuğunda, ortak dil çalışma zamanı (CLR) bu özel durumu işleyen `catch` ifadeye bakar. Şu anda yürütülmekte olan yöntem böyle bir `catch` bloğu içermiyorsa, CLR geçerli yöntemi çağıran yönteme bakar ve bu şekilde çağrı yığınını alır. `catch` bloğu bulunmazsa, CLR kullanıcıya işlenmeyen bir özel durum iletisi görüntüler ve programın yürütülmesini engeller.

`try` bloğu, özel duruma neden olabilecek korunan kodu içerir. Bir özel durum oluşturuluncaya veya başarıyla tamamlanana kadar blok yürütülür. Örneğin, bir `null` nesnesi atama denemesi <xref:System.NullReferenceException> özel durumunu başlatır:

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

`catch` yan tümcesi herhangi bir tür özel durum yakalamak için bağımsız değişken olmadan kullanılabilmesine rağmen, bu kullanım önerilmez. Genel olarak, yalnızca kurtarmayı bildiğiniz özel durumları yakamalısınız. Bu nedenle, her zaman <xref:System.Exception?displayProperty=nameWithType> türetilmiş bir nesne bağımsız değişkeni belirtmeniz gerekir, örneğin:

```csharp
catch (InvalidCastException e)
{
}
```

Aynı try-catch deyimi içinde birden fazla özel `catch` yan tümcesi kullanmak mümkündür. Bu durumda, `catch` yan tümceleri sırasıyla inceedildiği için `catch` yan tümcelerinin sırası önemlidir. Daha az özel durumları daha az spesifik olanlardan önce yakalayın. Daha sonraki bir bloba ulaşılmaması için catch bloklarını sıralarsanız derleyici bir hata oluşturur.

`catch` bağımsız değişkenlerin kullanılması, işlemek istediğiniz özel durumları filtrelemek için bir yoldur.  Ayrıca, işleme karar vermek için özel durumu daha ayrıntılı bir şekilde inceleyen bir özel durum filtresi de kullanabilirsiniz.  Özel durum filtresi false döndürürse, işleyici araması devam eder.

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

Özel durum filtreleri yakalamak ve yeniden oluşturmak tercih edilir (aşağıda açıklanmıştır) çünkü filtreler yığından ayrılmaz.  Daha sonraki bir işleyici yığının dökümünü alıyorsa, özel durumun ilk olarak oluşturulduğu son yerde değil, ilk olarak nereden geldiğini görebilirsiniz.  Özel durum filtre ifadelerinin yaygın kullanımı günlüğe kaydedilir.  Her zaman bir günlüğe çıkış yapan yanlış değeri döndüren bir filtre oluşturabilirsiniz, bunları işlemek ve yeniden oluşturmak zorunda kalmadan, özel durumları bu şekilde günlüğe kaydedebilirsiniz.

[Throw](throw.md) deyimleri, `catch` ifadesiyle yakalanan özel durumu yeniden oluşturmak için `catch` bloğunda kullanılabilir. Aşağıdaki örnek, <xref:System.IO.IOException> bir özel durumdan kaynak bilgilerini ayıklar ve ardından ana yöntemin özel durumunu oluşturur.

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
> Benzer bir sonucu genellikle temizleyici bir şekilde (Bu belgede daha önce açıklandığı gibi, yığın değiştirilmeyen) almak için bir özel durum filtresi kullanmak da mümkündür. Aşağıdaki örnekte, bir önceki örnek olarak çağıranlar için benzer bir davranış vardır. İşlevi, `e.Data` `null`olduğunda `InvalidCastException` çağırana geri gönderir.
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null) 
> {
>     // Take some action.
> }
> ``` 

`try` bloğunun içinden yalnızca içinde belirtilen değişkenleri başlatın. Aksi takdirde, bloğun yürütülmesi tamamlanmadan önce bir özel durum ortaya çıkabilir. Örneğin, aşağıdaki kod örneğinde `n` değişkeni `try` bloğunun içinde başlatılır. Bu değişkeni `Write(n)` deyimindeki `try` bloğunun dışında kullanma girişimi, bir derleyici hatası oluşturur.

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

Zaman uyumsuz bir yöntem, [zaman uyumsuz](async.md) bir değiştirici tarafından işaretlenir ve genellikle bir veya daha fazla await ifadesi ya da deyimi içerir. Await ifadesi bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>[await](../operators/await.md) işlecini uygular.

Denetim zaman uyumsuz yöntemde bir `await` ulaştığında, beklenen görev tamamlanana kadar yöntemindeki ilerleme askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir. Daha fazla bilgi için bkz. Async [ve await ile](../../programming-guide/concepts/async/index.md) zaman uyumsuz programlama ve [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

`await` uygulandığı tamamlanmış görev, görevi döndüren yöntemdeki işlenmeyen bir özel durum nedeniyle hatalı durumda olabilir. Görevin bekleniyor bir özel durum oluşturur. Aynı zamanda, döndüren zaman uyumsuz işlem iptal edilirse, bir görev iptal edilmiş durumda da bitebilirler. İptal edilen bir görevin bekleniyor bir `OperationCanceledException`oluşturur. Zaman uyumsuz bir işlemi iptal etme hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).

Özel durumu yakalamak için, görevi bir `try` bloğunda bekledi ve özel durumu ilişkili `catch` bloğunda yakalar. Örneğin, [zaman uyumsuz yöntem örneği](#async-method-example) bölümüne bakın.

Beklenen zaman uyumsuz yöntemde birden çok özel durum oluştuğundan, görev hatalı durumda olabilir. Örneğin, görev bir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>çağrısının sonucu olabilir. Böyle bir görevi bekleyettiğinizde, özel durumların yalnızca biri yakalanacaktır ve hangi özel durumun yakalanıp yakalanmayacak olduğunu tahmin edemeyecektir. Bir örnek için, [Task. WhenAll örnek](#taskwhenall-example) bölümüne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `try` bloğu, bir özel duruma neden olabilecek `ProcessString` yöntemine bir çağrı içerir. `catch` yan tümcesi yalnızca ekranda bir ileti görüntüleyen özel durum işleyicisini içerir. `throw` ifade `MyMethod`içinden çağrıldığında, sistem `catch` bildirimine bakar ve iletiyi `Exception caught`görüntüler.

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a>İki catch bloğu örneği

Aşağıdaki örnekte, iki catch bloğu kullanılır ve ilk olarak gelen en özel durum yakalanmalıdır.

En az özel durumu yakalamak için `ProcessString` throw ifadesini aşağıdaki deyimle değiştirebilirsiniz: `throw new Exception()`.

Örneğe en az özel catch bloğunu yerleştirirseniz, aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a>Async yöntemi örneği

Aşağıdaki örnek, zaman uyumsuz metotlar için özel durum işlemeyi gösterir. Zaman uyumsuz bir görevin aldığı bir özel durumu yakalamak için `await` ifadesini bir `try` bloğuna yerleştirin ve özel durumu bir `catch` bloğunda yakalayın.

Özel durum işlemeyi göstermek için örnekteki `throw new Exception` satırının açıklamasını kaldırın. Görevin `IsFaulted` özelliği `True`olarak ayarlanır, görevin `Exception.InnerException` özelliği özel duruma ayarlanır ve özel durum `catch` bloğunda yakalanır.

Zaman uyumsuz bir işlemi iptal ettiğinizde ne olacağını göstermek için `throw new OperationCanceledException` çizginin açıklamasını kaldırın. Görevin `IsCanceled` özelliği `true`olarak ayarlanır ve özel durum `catch` bloğunda yakalanır. Bu örnek için geçerli olmayan bazı koşullar altında, görevin `IsFaulted` özelliği `true` olarak ayarlanır ve `IsCanceled` `false`olarak ayarlanır.

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a>Task. WhenAll örneği

Aşağıdaki örnekte, birden çok görevin birden çok özel durum ile sonuçlanbildiği özel durum işleme gösterilmektedir. `try` bloğu, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>çağrısıyla döndürülen görevi bekler. Bu görev, WhenAll 'un uygulandığı üç görev tamamlandığında tamamlanmıştır.

Üç görevin her biri özel duruma neden olur. `catch` bloğu, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>tarafından döndürülen görevin `Exception.InnerExceptions` özelliğinde bulunan özel durumlar boyunca yinelenir.

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-finally](try-finally.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
