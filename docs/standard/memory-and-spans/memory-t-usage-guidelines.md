---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121968"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Memory\<T > ve Span\<T > kullanım yönergeleri

.NET Core, rasgele bitişik bellek bölgesini temsil eden bir dizi tür içerir. .NET Core 2.0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601>tanıtıldı ve yönetilen veya yönetilmeyen bellek tarafından desteklenen hafif bellek arabellekleri vardır. Bu türler yalnızca yığında depolanabildiği için, eşzamanlı yöntem çağrıları da dahil olmak üzere bir dizi senaryo için uygun değildir. .NET Core 2.1 , <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601>, ve <xref:System.Buffers.MemoryPool%601>. Gibi <xref:System.Span%601> <xref:System.Memory%601> , ve ilgili türleri hem yönetilen ve yönetilmeyen bellek tarafından desteklenebilir. <xref:System.Span%601>Aksine, <xref:System.Memory%601> yönetilen yığın üzerinde saklanabilir.

Her <xref:System.Span%601> <xref:System.Memory%601> ikisi de ve ardışık hatlar kullanılabilir yapılandırılmış veri arabellekleri vardır. Diğer bir deyişle, verilerin bir kısmının veya tamamının ardışık olarak aktarılabilen, bunları işleyen ve isteğe bağlı olarak arabelleği değiştirebilen parçalara aktarılabilen şekilde tasarlanmıştır. <xref:System.Memory%601> Ve ilgili türleri birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiği için, geliştiricilerin sağlam kod lar üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.

## <a name="owners-consumers-and-lifetime-management"></a>Sahipleri, tüketiciler ve ömür boyu yönetim

Arabellekler API'ler arasında geçirilebildiği ve arabelleklere bazen birden çok iş parçacığından erişilebildiği için, yaşam boyu yönetimi göz önünde bulundurmak önemlidir. Üç temel kavram vardır:

- **Sahiplik**. Arabellek örneğinin sahibi, artık kullanılmadığında arabelleği yok etmek de dahil olmak üzere yaşam boyu yönetimden sorumludur. Tüm arabelleklerin tek bir sahibi var. Genellikle sahibi arabellek oluşturulan veya bir fabrikadan arabellek aldı bileşenidir. Mülkiyet de devredilebilir; **Bileşen-A** arabellek denetimini **Bileşen-B'ye**verebilir, bu noktada **Bileşen-A** arabelleği artık kullanamayabilir ve **Bileşen-B** artık kullanılmadığında arabelleği yok etmekten sorumlu olur.

- **Tüketim**. Arabellek örneğinin tüketicisi, arabellek örneğini ondan okuyarak ve muhtemelen ona yazarak kullanabilir. Bazı dış eşitleme mekanizması sağlanmadıkça arabellekler aynı anda bir tüketiciye sahip olabilir. Arabellek etkin tüketici mutlaka arabellek sahibi olmadığını unutmayın.

- **Kira .** Kiralama, belirli bir bileşenin arabelleğe tüketici sayılsa izin verdiği süredir.

Aşağıdaki sözde kod örneği bu üç kavramı göstermektedir. Bu tür `Main` <xref:System.Memory%601> <xref:System.Char>bir arabellek instantiates bir yöntem `WriteInt32ToBuffer` içerir, arabellek için bir tamsa dize gösterimi `DisplayBufferToConsole` yazmak için yöntemi çağırır ve sonra arabellek değerini görüntülemek için yöntemi çağırır.

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

Yöntem `Main` arabellek oluşturur (bu durumda <xref:System.Span%601> bir örnek) ve böylece sahibi. Bu `Main` nedenle, artık kullanılmadığında arabelleği yok etmekten sorumludur. Bunu arabellek <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemini arayarak yapar. (Buradaki <xref:System.Span%601.Clear> yöntem aslında arabelleğin belleği <xref:System.Span%601> temizler; yapıaslında arabelleği yok eden bir yöntem yok.)

Arabellekte iki tüketici `WriteInt32ToBuffer` `DisplayBufferToConsole`vardır ve. Aynı anda yalnızca bir tüketici `WriteInt32ToBuffer`vardır `DisplayBufferToConsole`(önce, sonra), ve tüketicilerin hiçbiri tampona sahip değildir. Bu bağlamda "tüketici"nin arabelleğe salt okunur görünümü anlamına olmadığını da unutmayın; tüketiciler, arabelleğe bir okuma/yazma görünümü verilirse, `WriteInt32ToBuffer` bu arabellek içeriğini değiştirebilirsiniz.

Yöntem, `WriteInt32ToBuffer` yöntem çağrısının başlangıcı ile yöntemin döndüğü zaman arasında arabellek üzerinde bir kiraya sahiptir (tüketebilir). Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kira vardır ve yöntem gerdiğinde kira serbest bırakılır. (Kira yönetimi için API yoktur; "kira" kavramsal bir konudur.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Bellek\<T> ve sahibi/ tüketici modeli

[Sahipleri, tüketiciler ve ömür boyu yönetim](#owners-consumers-and-lifetime-management) bölümü notları gibi, bir arabellek her zaman bir sahibi vardır. .NET Core iki sahiplik modelini destekler:

- Tek sahipliği destekleyen bir model. Bir arabellek tüm ömrü boyunca tek bir sahibi vardır.

- Sahiplik aktarımına destek veren bir model. Arabelleğe sahipolmak, asıl sahibinden (yaratıcısı) başka bir bileşene aktarılabilir ve bu da arabellbellin yaşam boyu yönetiminden sorumlu hale gelir. Bu sahip, sahipliği başka bir bileşene aktarabilir ve böyle devam eder.

Arabelleği <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> açıkça yönetmek için arabirimi kullanırsınız. <xref:System.Buffers.IMemoryOwner%601>her iki sahiplik modelini de destekler. <xref:System.Buffers.IMemoryOwner%601> Başvuru sahibi bileşen arabelleğe sahiptir. Aşağıdaki örnek, <xref:System.Buffers.IMemoryOwner%601?> arabelleğin sahipliğini <xref:System.Memory%601> yansıtmak için bir örnek kullanır.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Biz de bu örneği [`using`](../../csharp/language-reference/keywords/using-statement.md)yazabilirsiniz:

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Bu kodda:

- Yöntem `Main` <xref:System.Buffers.IMemoryOwner%601> örneğine başvuru tutar, bu `Main` nedenle yöntem arabellek sahibidir.

- Ve `WriteInt32ToBuffer` `DisplayBufferToConsole` yöntemler <xref:System.Memory%601> genel API olarak kabul edilir. Bu nedenle, arabellek tüketicilerdir. Ve her seferinde sadece birer tüketirler.

Yöntem `WriteInt32ToBuffer` arabellek için bir değer yazmak için `DisplayBufferToConsole` tasarlanmış olsa da, yöntem değildir. Bunu yansıtmak için, tür <xref:System.ReadOnlyMemory%601>bir argüman kabul olabilir. Daha fazla <xref:System.ReadOnlyMemory%601>bilgi için , [Bkz.\<Kural #2: Arabellek salt okunacaksa ReadOnlySpan T> veya ReadOnlyMemory\<T>'ı kullanın.](#rule-2)

### <a name="ownerless-memoryt-instances"></a>"Sahipsiz"\<Bellek T örnekleri>

Bir <xref:System.Memory%601> örneği kullanmadan <xref:System.Buffers.IMemoryOwner%601>oluşturabilirsiniz. Bu durumda, arabellek sahipliği açık yerine örtülü ve yalnızca tek sahibi modeli desteklenir. Bunu şu şekilde yapabilirsiniz:

- <xref:System.Memory%601> Aşağıdaki örnekte olduğu `T[]`gibi, doğrudan yapıcılardan birini çağırmak.

- Bir `ReadOnlyMemory<char>` örnek oluşturmak için [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) uzantı yöntemini çağırma.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Başlangıçta <xref:System.Memory%601> örneği oluşturan yöntem arabellek örtülü sahibidir. Devriyi kolaylaştıracak bir örnek olmadığından, <xref:System.Buffers.IMemoryOwner%601> sahiplik başka bir bileşene aktarılamaz. (Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiğini de tahmin edebilirsiniz.)

## <a name="usage-guidelines"></a>Kullanım yönergeleri

Bir bellek bloğu sahibi olduğundan ancak bazıları belirli bir bellek bloğu üzerinde aynı anda çalışabilir birden çok bileşene <xref:System.Memory%601> geçirilmesi <xref:System.Span%601>amaçlanmıştır, hem ve .  Yönergeler gereklidir, çünkü:

- Bir bileşenin, sahibi yayımladıktan sonra bellek bloğuna başvuruda bulunmasını sağlamak mümkündür.

- Bir bileşenin, arabellekteki verileri bozma işleminde, başka bir bileşenin üzerinde çalıştığı anda bir arabellek üzerinde çalışması mümkündür.

- Yığına ayrılan yapı performansı <xref:System.Span%601> en iyi <xref:System.Span%601> duruma getirir ve bellek bloğunda çalışmak için <xref:System.Span%601> tercih edilen türü yapar, ancak bazı önemli kısıtlamalara da tabi dir. Ne zaman <xref:System.Span%601> ve ne zaman kullanılacağını <xref:System.Memory%601>bilmek önemlidir.

Aşağıda başarıyla kullanmak <xref:System.Memory%601> ve ilgili türleri için önerilerimiz verilmiştir. Aksini <xref:System.Memory%601> açıkça belirtmediğimiz <xref:System.Span%601> sürece, <xref:System.ReadOnlyMemory%601> bu <xref:System.ReadOnlySpan%601> kılavuz için de geçerli olduğunu ve bu kılavuz için de geçerli olduğunu unutmayın.

**Kural #1: Senkron API için,\<bellek\<T> yerine Span T>'ı mümkünse parametre olarak kullanın.**

<xref:System.Span%601>daha çok <xref:System.Memory%601> yönlüdür ve bitişik bellek arabelleklerinin daha geniş bir yelpazesini temsil edebilir. <xref:System.Span%601>ayrıca <xref:System.Memory%601>daha iyi performans sunar. Son olarak, Span <xref:System.Memory%601.Span?displayProperty=nameWithType> <xref:System.Memory%601> \<T>-to-Memory\<T> dönüştürme mümkün olmasa da, bir örneği bir <xref:System.Span%601>, bir ,> dönüştürmek dönüştürmek için özelliği kullanabilirsiniz. Bu nedenle, arayanların bir <xref:System.Memory%601> örneği varsa, yine de parametrelerle <xref:System.Span%601> yöntemlerinizi arayabilirler.

Tür <xref:System.Span%601> <xref:System.Memory%601> yerine bir tür parametresi kullanmak da doğru bir tüketme yöntemi uygulaması yazmanıza yardımcı olur. Yönteminizin kiralanmasının ötesinde arabelleğe erişmeye çalışmadığınızdan emin olmak için otomatik olarak derleme zamanı denetimleri alırsınız (daha sonra bu konuda daha fazla bilgi).

Bazen, tam eşzamanlı olsanız <xref:System.Memory%601> bile <xref:System.Span%601> parametre yerine parametre kullanmanız gerekir. Belki de bağlı olduğunuz bir <xref:System.Memory%601> API yalnızca bağımsız değişkenleri kabul eder. Bu iyi, ancak eşzamanlı kullanırken <xref:System.Memory%601> ilgili tradeoffs farkında olun.

<a name="rule-2" />

**Kural #2: Arabellek\<salt okunacaksa ReadOnlySpan T> veya ReadOnlyMemory\<T> kullanın.**

Önceki örneklerde, `DisplayBufferToConsole` yöntem yalnızca arabellekten okur; arabelleğe ilişkin içeriğini değiştirmez. Yöntem imzası aşağıdaki şekilde değiştirilmelidir.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Aslında, bu kural ve kural #1 birleştirirseniz, daha da iyisini yapabilir ve yöntem imzasını aşağıdaki gibi yeniden yazabiliriz:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

Yöntem `DisplayBufferToConsole` şimdi akla gelebilecek hemen hemen her `T[]`tampon türü ile çalışır: , [depolama stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile tahsis , ve benzeri. Hatta doğrudan içine <xref:System.String> bir geçebilir!

**Kural #3: Yönteminiz\<Bellek T `void`>'u kabul edip\<döndürürse, yönteminiz döndükten sonra Bellek T> örneğini kullanmamalısınız.**

Bu daha önce bahsedilen "kira" kavramı ile ilgilidir. Bir void-returning yöntemin <xref:System.Memory%601> örnek üzerinde kira yöntemi girildiğinde başlar ve yöntem çıktığında sona erer. Konsoldan gelen girişe `Log` göre bir döngü içinde çağıran aşağıdaki örneği göz önünde bulundurun.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Tam `Log` eşzamanlı bir yöntemse, bu kod beklendiği gibi çalışır, çünkü herhangi bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi vardır.
Ama bunun `Log` yerine bu uygulama olduğunu düşünün.

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

Bu uygulamada, `Log` özgün yöntem döndükten sonra <xref:System.Memory%601> arka planda örneği kullanmaya çalıştığı için kira sözleşmesini ihlal eder. Yöntem, `Main` arabelleği okuma `Log` girişimleri sırasında mutasyona uğrayabilir ve bu da veri bozulmasına neden olabilir.

Bunu çözmenin birkaç yolu vardır:

- Yöntem, `Log` <xref:System.Threading.Tasks.Task> `Log` yöntemin aşağıdaki `void`uygulama yaptığı gibi yerine bir döndürebilir.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`bunun yerine aşağıdaki gibi uygulanabilir:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Kural #4: Yönteminiz bellek\<T> kabul ediyor ve bir\<Görevi döndürüyorsa, Görev terminal durumuna geçtikten sonra Bellek T> örneğini kullanmamalısınız.**

Bu, Kural #3'nin yalnızca async varyantıdır. Önceki `Log` örnekteki yöntem, bu kurala uymak için aşağıdaki gibi yazılabilir:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Burada, "terminal durumu" görevin tamamlanmış, hatalı veya iptal edilmiş bir duruma geçiş yaptığı anlamına gelir. Başka bir deyişle, "terminal durumu" "atmayı veya yürütmeye devam etmeyi bekleyen her şey" anlamına gelir.

Bu kılavuz, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>döndüren yöntemler için de geçerlidir.

**Kural #5: Oluşturucunuz Bellek\<T>'ı bir parametre olarak kabul ederse, yapılandırılan\<nesnedeki örnek yöntemlerin Bellek T> örneğinin tüketicileri olduğu varsayılır.**

Aşağıdaki örneği inceleyin:

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

Burada, `OddValueExtractor` oluşturucu bir `ReadOnlyMemory<int>` oluşturucu parametre olarak kabul eder, bu nedenle `ReadOnlyMemory<int>` yapıcının kendisi örneğin tüketicisi dir ve döndürülen değerdeki tüm örnek yöntemleri de özgün `ReadOnlyMemory<int>` örneğin tüketicileridir. Bu, `TryReadNextOddValue` örnek doğrudan `ReadOnlyMemory<int>` `TryReadNextOddValue` yönteme geçirilemese bile örneği tükettiği anlamına gelir.

**Kural #6: Türünüzde>\<türünde ayarlanabilir bir Bellek T özelliği (veya eşdeğer bir örnek yöntemi) varsa, bu\<nesnedeki örnek yöntemleri bellek T> örneğinin tüketicisi olarak kabul edilir.**

Bu gerçekten kural #5 sadece bir çeşididir. Özellik ayarlayıcıları veya eşdeğer yöntemlerin girişlerini yakalayıp devam ettirmeleri varsayıldığından, aynı nesnedeki örnek yöntemleri yakalanan durumu kullanabilir.

Aşağıdaki örnek bu kuralı tetikler:

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

**Kural #7: Bir IMemoryOwner\<T> referans varsa, bir noktada onu elden veya sahipliğini aktarmak gerekir (ama her ikisi de değil).**

Bir <xref:System.Memory%601> örnek yönetilen veya yönetilmeyen bellek tarafından desteklenen olabilir, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> <xref:System.Memory%601> örnek üzerinde gerçekleştirilen çalışma tamamlandığında sahibi aramak gerekir. Alternatif olarak, sahibi örneğin sahipliğini <xref:System.Buffers.IMemoryOwner%601> farklı bir bileşene aktarabilir ve bu noktada <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> satın alma bileşeni uygun zamanda çağrıda bulunan (daha sonra bu konuda daha fazla bilgi) sorumlu olur.

Yöntemin <xref:System.Buffers.MemoryPool%601.Dispose%2A> çağrılmaması, yönetilmeyen bellek sızıntılarına veya diğer performans bozulmasına neden olabilir.

Bu kural, fabrika yöntemlerini çağıran <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>kod için de geçerlidir. Arayan döndürülenin <xref:System.Buffers.IMemoryOwner%601> sahibi olur ve tamamlandığında örneğin atılmasından sorumludur.

**Kural #8: API>\<yüzeyinde bir IMemoryOwner T parametresi varsa, bu örneğin sahipliğini kabul etmiş siniz.**

Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı planladığını bildirir. Bileşeniniz Kural #7'na göre uygun şekilde imha edilmesiiçin sorumlu olur.

Örneğin sahipliğini <xref:System.Buffers.IMemoryOwner%601> farklı bir bileşene aktaran herhangi bir bileşen, yöntem çağrısı tamamlandıktan sonra bu örneği artık kullanmamalıdır.

> [!IMPORTANT]
> Oluşturucunuz bir <xref:System.Buffers.IMemoryOwner%601> parametre olarak kabul ederse, <xref:System.IDisposable>türü <xref:System.IDisposable.Dispose%2A> uygulanmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>ve yönteminiz .

**Kural #9: Eşzamanlı bir p/invoke yöntemini sarıyorsanız, API'niz Span\<T>'yi parametre olarak kabul etmelidir.**

Kural #1 göre, <xref:System.Span%601> genellikle senkron API'ler için kullanılacak doğru türüdür. Aşağıdaki örnekte olduğu [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) gibi, örnekleri anahtar kelime aracılığıyla sabitleyebilirsiniz. <xref:System.Span%601>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

Önceki örnekte, `pbData` örneğin giriş açıklığı boşsa null olabilir. Dışa aktarılan yöntem `pbData` innull olmayan olmasını `cbData` gerektiriyorsa, 0 olsa bile, yöntem aşağıdaki gibi uygulanabilir:

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

**Kural #10: Bir eşzamanlı p/invoke yöntemini sarıyorsanız, API'niz Bellek\<T>'yi parametre olarak kabul etmelidir.**

Anahtar kelimeyi [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) eşzamanlı işlemlerde kullanamayacağınız için, <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> örneğin temsil <xref:System.Memory%601> ettiği bitişik bellek türünden bağımsız olarak örnekleri sabitleme yöntemini kullanırsınız. Aşağıdaki örnek, eşzamanlı bir p/invoke çağrısı gerçekleştirmek için bu API'nin nasıl kullanılacağını gösterir.

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
