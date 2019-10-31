---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121968"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Bellek\<T > ve yayma\<T > Kullanım yönergeleri

.NET Core, belleğin rastgele bir bitişik bölgesini temsil eden bir dizi tür içerir. .NET Core 2,0, yönetilen veya yönetilmeyen bellekle desteklenen basit bellek arabellekleri olan <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601>sunmuştur. Bu türler yalnızca yığında depolanabileceğinden, zaman uyumsuz yöntem çağrıları dahil olmak üzere çok sayıda senaryo için uygun değildir. .NET Core 2,1 <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>ve <xref:System.Buffers.MemoryPool%601>dahil olmak üzere çeşitli ek türler ekler. <xref:System.Span%601>gibi <xref:System.Memory%601> ve ilgili türleri hem yönetilen hem de yönetilmeyen bellekle desteklenir. <xref:System.Span%601>farklı olarak, <xref:System.Memory%601> yönetilen yığında depolanabilir.

Hem <xref:System.Span%601> hem de <xref:System.Memory%601>, işlem hatlarında kullanılabilecek yapılandırılmış verilerin arabelleklerdir. Diğer bir deyişle, verilerin bazılarının veya tümünün işlem hattındaki bileşenlere etkin bir şekilde geçirilmesi için tasarlanmaları ve isteğe bağlı olarak arabelleği değiştirebilmeleri için tasarlanmıştır. <xref:System.Memory%601> ve ilgili türlerine birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiğinden, geliştiricilerin sağlam kod üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.

## <a name="owners-consumers-and-lifetime-management"></a>Sahipler, tüketiciler ve ömür yönetimi

Arabellekler API 'Ler arasında geçirilebileceği ve arabelleklerin bazen birden fazla iş parçacığından erişilebilir olduğundan, ömür yönetimini göz önünde bulundurmanız önemlidir. Üç temel kavram vardır:

- **Sahiplik**. Arabellek örneğinin sahibi, artık kullanımda olmadığında arabelleği yok etme da dahil olmak üzere ömür yönetiminden sorumludur. Tüm arabelleklerin tek bir sahibi vardır. Genellikle sahip, arabelleği oluşturan veya bir fabrikadan arabelleği alan bileşendir. Sahiplik da aktarılabilir; **Bileşen-a** arabellek denetimini **bileşen-b**' y e yeniden denetleyebilir ve bu noktada, o nokta **bileşeni-A** artık arabellek kullanamaz ve **bileşen-b** artık kullanımda olmadığında arabelleği yok etmeden sorumlu olur.

- **Tüketim**. Bir arabellek örneğinin tüketicisi, onu okuyarak ve muhtemelen ona yazarak arabellek örneğini kullanmasına izin verilir. Bazı dış eşitleme mekanizması sağlanmadığı takdirde arabellekler tek seferde bir tüketiciye sahip olabilir. Bir arabelleğin etkin tüketicisinin, arabelleğin sahibi olması gerekmediğini unutmayın.

- **Kira**. Kira, belirli bir bileşenin arabelleğin tüketicisi olmasına izin verilen süredir.

Aşağıdaki sözde kod örneğinde bu üç kavram gösterilmektedir. Bu, <xref:System.Char>türünde bir <xref:System.Memory%601> arabelleğini örnekleyen `Main` yöntemi içerir, arabelleğe bir tamsayının dize gösterimini yazmak için `WriteInt32ToBuffer` yöntemini çağırır ve ardından arabelleğin değerini göstermek için `DisplayBufferToConsole` yöntemini çağırır.

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

`Main` yöntemi, arabelleği oluşturur (Bu durumda bir <xref:System.Span%601> örneği) ve bu nedenle sahibidir. Bu nedenle, `Main` artık kullanımda olmadığında arabelleği yok etmek sorumludur. Bu, arabelleğin <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemini çağırarak yapar. (<xref:System.Span%601.Clear> yöntemi aslında arabelleğin belleğini temizler; <xref:System.Span%601> yapısı aslında arabelleği yok eden bir yönteme sahip değildir.)

Arabellekte iki tüketici vardır, `WriteInt32ToBuffer` ve `DisplayBufferToConsole`. Tek seferde yalnızca bir tüketici vardır (ilk `WriteInt32ToBuffer`, sonra `DisplayBufferToConsole`) ve hiçbir tüketicisinin arabelleğin sahibi yoktur. Ayrıca, bu bağlamda "Consumer" öğesinin, arabelleğin salt okunurdur görünümünü göstermez; müşteriler, arabelleğin okuma/yazma görünümü verildiyse `WriteInt32ToBuffer` olduğu gibi arabelleğin içeriğini değiştirebilir.

`WriteInt32ToBuffer` yöntemi, yöntem çağrısının başlangıcı ile yöntemin döndürdüğü süre arasındaki arabelleği (tüketebileceği) kullanır. Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kiralama vardır ve kira yöntemi zaman içinde serbest bırakılır. (Kiralama Yönetimi için bir API yoktur; "Kira" kavramsal bir kavramdır.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Bellek\<T > ve sahip/tüketici modeli

[Sahipler, tüketiciler ve ömür yönetimi](#owners-consumers-and-lifetime-management) bölümünde, bir arabelleğin her zaman bir sahibi vardır. .NET Core iki sahiplik modelini destekler:

- Tek sahipliği destekleyen bir model. Bir arabelleğin tüm ömrü için tek bir sahibi vardır.

- Sahiplik aktarımını destekleyen bir model. Bir arabelleğin sahipliği, özgün sahibinden (Oluşturucu) başka bir bileşene aktarılabilir ve bu da arabelleğin yaşam süresi yönetiminden sorumludur. Bu sahip, sahipliği başka bir bileşene aktarabilir ve bu şekilde devam eder.

Bir arabelleğin sahipliğini açıkça yönetmek için <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> arabirimini kullanırsınız. <xref:System.Buffers.IMemoryOwner%601> hem sahiplik modellerini destekler. <xref:System.Buffers.IMemoryOwner%601> başvurusuna sahip olan bileşen arabelleğe aittir. Aşağıdaki örnek, bir <xref:System.Memory%601> arabelleğinin sahipliğini yansıtmak için bir <xref:System.Buffers.IMemoryOwner%601?> örneği kullanır.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Ayrıca, bu örneği [`using`](../../csharp/language-reference/keywords/using-statement.md)de yazalım:

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Bu kodda:

- `Main` yöntemi <xref:System.Buffers.IMemoryOwner%601> örneğine başvuruyu barındırır, bu nedenle `Main` yöntemi arabelleğin sahibidir.

- `WriteInt32ToBuffer` ve `DisplayBufferToConsole` yöntemleri ortak bir API olarak <xref:System.Memory%601> kabul eder. Bu nedenle, arabelleğin tüketicilerinden oluşur. Ve tek seferde yalnızca bir tane tüketir.

`WriteInt32ToBuffer` yöntemi arabelleğe bir değer yazmaya yönelik olarak olsa da, `DisplayBufferToConsole` yöntemi değildir. Bunu yansıtmak için <xref:System.ReadOnlyMemory%601>türünde bir bağımsız değişkeni kabul etmiş olabilir. <xref:System.ReadOnlyMemory%601>hakkında daha fazla bilgi için bkz. [Rule #2: ReadOnlySpan\<t > veya ReadOnlyMemory\<t > arabellek salt okunurdur](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"OwnerLeSs" bellek\<T > örnekleri

<xref:System.Buffers.IMemoryOwner%601>kullanmadan bir <xref:System.Memory%601> örneği oluşturabilirsiniz. Bu durumda, arabelleğin sahipliği açık yerine örtük olur ve yalnızca tek sahip modeli desteklenir. Bunu şu şekilde yapabilirsiniz:

- Aşağıdaki örnekte olduğu gibi, `T[]`geçirerek <xref:System.Memory%601> oluşturuculardan birini doğrudan çağırma.

- Bir `ReadOnlyMemory<char>` örneği üretmek için [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) genişletme yöntemi çağrılıyor.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Başlangıçta <xref:System.Memory%601> örneğini oluşturan Yöntem, arabelleğin örtük sahibidir. Aktarımı kolaylaştırmak için <xref:System.Buffers.IMemoryOwner%601> bir örnek bulunmadığından, sahiplik başka bir bileşene aktarılamaz. (Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiği da hayal edebilirsiniz.)

## <a name="usage-guidelines"></a>Kullanım yönergeleri

Bir bellek bloğunun sahibi olduğu, ancak bazıları aynı anda belirli bir bellek bloğunun üzerinde çalışabilen birden çok bileşene geçirilmesi amaçlanan için, hem <xref:System.Memory%601> hem de <xref:System.Span%601>kullanımı için kılavuz oluşturulması önemlidir.  Şu nedenle yönergeler gereklidir:

- Bir bileşenin sahibi serbest bırakıldıktan sonra bir bellek bloğunun başvurusunu bekletmek mümkündür.

- Bir bileşenin, başka bir bileşenin üzerinde çalıştığı aynı anda bir arabellekte çalışması, işlemin arabellekteki verileri bozuyor olması mümkündür.

- Yığın tarafından ayrılan <xref:System.Span%601> yapısı performansı iyileştirirken ve bir bellek bloğunda çalışan için tercih edilen türü <xref:System.Span%601> hale getirirken, bazı önemli kısıtlamalara <xref:System.Span%601> de konu alır. Ne zaman <xref:System.Span%601> kullanacağınızı ve ne zaman <xref:System.Memory%601>kullanacağınızı bilmemiz önemlidir.

<xref:System.Memory%601> ve ilgili türlerini kullanarak başarıyla önerdiğimiz önerilerden bazıları aşağıda verilmiştir. <xref:System.Memory%601> ve <xref:System.Span%601> için geçerli olan yönergelerin, açıkça aksi belirtilmedikçe <xref:System.ReadOnlyMemory%601> ve <xref:System.ReadOnlySpan%601> için de geçerli olduğunu unutmayın.

**Kural #1: zaman uyumlu bir API Için, mümkünse bir parametre olarak >\<T >, bellek\<T yerine kullanın.**

<xref:System.Span%601>, <xref:System.Memory%601> daha çok daha hızlıdır ve çok sayıda bitişik bellek arabelleğini temsil edebilir. <xref:System.Span%601> Ayrıca <xref:System.Memory%601>daha iyi performans sunar. Son olarak, bir <xref:System.Memory%601> örneğini <xref:System.Span%601>dönüştürmek için <xref:System.Memory%601.Span?displayProperty=nameWithType> özelliğini kullanabilirsiniz,\<ancak > bellek\<T > dönüştürme mümkün değildir. Bu nedenle, arayanların bir <xref:System.Memory%601> örneğine sahip olması durumunda, yöntemlerinizi <xref:System.Span%601> parametreleri ile çağırabilirler.

<xref:System.Memory%601> türü yerine <xref:System.Span%601> türünde bir parametre kullanılması, doğru bir tüketen Yöntem uygulamasını yazmanıza de yardımcı olur. Metodun kira süresinin ötesinde (daha sonra bu konuda daha fazla) arabelleğe erişmeye girişdiğinizden emin olmak için otomatik olarak derleme zamanı denetimleri alacaksınız.

Bazen, tam olarak zaman uyumlu olsanız bile, <xref:System.Span%601> parametresi yerine bir <xref:System.Memory%601> parametresi kullanmanız gerekir. Büyük olasılıkla bağlı olduğunuz bir API yalnızca <xref:System.Memory%601> bağımsız değişkenlerini kabul eder. Bu sorun iyidir, ancak <xref:System.Memory%601> zaman uyumlu olarak kullanılırken ilgili olan avantajları göz önünde bulundurun.

<a name="rule-2" />

**Kural #2: arabelleğin Salt okunabilir olması gerekiyorsa, ReadOnlySpan\<T > veya ReadOnlyMemory\<T > kullanın.**

Önceki örneklerde `DisplayBufferToConsole` yöntemi yalnızca arabellekten okur; arabelleğin içeriğini değiştirmez. Yöntem imzası aşağıdaki şekilde değiştirilmelidir.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Aslında, bu kuralı ve kuralı #1 birleştirirseniz, daha iyi bir şekilde yapabiliriz ve yöntem imzasını aşağıdaki gibi yeniden yazabilirsiniz:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` yöntemi artık neredeyse her arabellek türü kodlamalardaki: `T[]`, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış depolama ve benzeri ile çalışmaktadır. Hatta, bir <xref:System.String> doğrudan! ' a geçirebilirsiniz.

**Kural #3: yönteminiz, bellek\<T > kabul eder ve `void`döndürürse, yöntemi döndürbaşladıktan sonra bellek\<T > örneğini kullanmamalıdır.**

Bu, daha önce bahsedilen "Kira" kavramıyla ilgilidir. <xref:System.Memory%601> örneği üzerinde void döndüren bir yöntemin kirası, yöntem girildiğinde başlar ve Yöntem çıktığında sonlanır. Bir döngüsünde `Log`, konsoldan gelen girişe göre çağıran aşağıdaki örneği göz önünde bulundurun.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

`Log` tamamen zaman uyumlu bir yöntem ise, belirli bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi olduğundan bu kod beklendiği gibi davranır.
Ancak `Log` bu uygulamaya sahip olması yerine düşünün.

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

Bu uygulamada, özgün Yöntem döndürülmeden sonra hala arka planda <xref:System.Memory%601> örneğini kullanmaya çalıştığı için `Log` kirayı ihlal ediyor. `Main` yöntemi, `Log` okumayı denediğinde arabelleği bir süre sonra da veri bozulmasına neden olabilir.

Bu sorunu çözmek için birkaç yol vardır:

- `Log` yönteminin aşağıdaki uygulanması `Log` yöntemi `void`yerine <xref:System.Threading.Tasks.Task> döndürebilir.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log` bunun yerine aşağıdaki gibi uygulanabilir:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Kural #4: yönteminiz bir bellek\<T > kabul ediyorsa ve bir görevi döndürürse, görev bir Terminal durumuna geçirdikten sonra, bellek\<T > örneğini kullanmanız gerekir.**

Bu yalnızca kural #3 zaman uyumsuz bir değişkendir. Önceki örnekteki `Log` yöntemi bu kuralla uyum sağlamak için aşağıdaki gibi yazılabilir:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Burada "Terminal durumu", görevin tamamlanmış, hatalı veya iptal edilmiş durumuna geçirdiğinin anlamına gelir. Diğer bir deyişle "Terminal durumu", "çalışmasına neden olan herhangi bir şey" anlamına gelir ve yürütme devam eder. "

Bu kılavuz <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>veya benzer bir tür döndüren yöntemler için geçerlidir.

**Kural #5: oluşturucunuz bir parametre olarak bellek\<T > kabul ediyorsa, oluşturulan nesnedeki örnek yöntemleri, bellek\<T > örneği olarak kabul edilir.**

Aşağıdaki örneği göz önünde bulundurun:

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

Burada `OddValueExtractor` Oluşturucu bir `ReadOnlyMemory<int>` Oluşturucu parametresi olarak kabul eder, bu nedenle oluşturucunun kendisi bir `ReadOnlyMemory<int>` örneğinin tüketicisidir ve döndürülen değer içindeki tüm örnek yöntemleri de orijinal `ReadOnlyMemory<int>` örneğinin tüketicisidir. Yani, örnek doğrudan `TryReadNextOddValue` yöntemine geçirilmese de `TryReadNextOddValue` `ReadOnlyMemory<int>` örneğini kullanır.

**Kural #6: türümde ayarlanabilir bir >\<belleğe (veya eşdeğer bir örnek yöntemi) sahipseniz, söz konusu nesnedeki örnek yöntemleri, bellek\<T > örneği olarak kabul edilir.**

Bu, yalnızca kural #5 bir değişkendir. Bu kural, özellik ayarlayıcıları veya eşdeğer Yöntemler girdilerini yakalama ve kalıcı hale getirilemediği için vardır, bu nedenle aynı nesne üzerindeki örnek yöntemleri yakalanan durumu kullanabilir.

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

**Kural #7: bir ımemoryowner\<T > başvurunuz varsa, bu dosyanın bir noktası atılmalıdır ya da sahipliğini (her ikisi değil) aktarırsınız.**

<xref:System.Memory%601> bir örnek yönetilen veya yönetilmeyen bellek tarafından desteklenen olduğundan, <xref:System.Memory%601> örneğinde gerçekleştirilen iş tamamlandığında sahip <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> çağırmalıdır. Alternatif olarak, sahip, <xref:System.Buffers.IMemoryOwner%601> örneğinin sahipliğini farklı bir bileşene aktarabilir, bu noktada alma bileşeni, uygun zamanda (daha sonra bu konuda daha fazla) <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> çağrılmadan sorumlu olur.

<xref:System.Buffers.MemoryPool%601.Dispose%2A> yöntemi çağıramaması, yönetilmeyen bellek sızıntılarına veya diğer performans düşüşüne neden olabilir.

Bu kural, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>gibi Fabrika yöntemlerini çağıran kod için de geçerlidir. Çağıran, döndürülen <xref:System.Buffers.IMemoryOwner%601> sahibi olur ve tamamlandığında örneği elden atma sorumludur.

**Kural #8: API yüzeyinizde ımemoryowner\<T > parametresi varsa, bu örneğin sahipliğini kabul etmiş olursunuz.**

Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı amaçladığı sinyallere işaret eder. Bileşeniniz, kural #7 göre uygun elden çıkarılmasından sorumludur.

<xref:System.Buffers.IMemoryOwner%601> örneğinin sahipliğini farklı bir bileşene aktaran herhangi bir bileşen, yöntem çağrısının tamamlanmasından sonra bu örneği artık kullanmamalıdır.

> [!IMPORTANT]
> Oluşturucu bir parametre olarak <xref:System.Buffers.IMemoryOwner%601> kabul ediyorsa, türü <xref:System.IDisposable>uygulamalıdır ve <xref:System.IDisposable.Dispose%2A> yönteminiz <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>çağırmalıdır.

**Kural #9: zaman uyumlu bir p/Invoke yöntemini sardıysanız, API 'niz bir parametre olarak\<T > yayma kabul etmelidir.**

Kural #1 göre, <xref:System.Span%601> genellikle zaman uyumlu API 'Ler için kullanılacak doğru türdür. Aşağıdaki örnekte olduğu gibi, [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğü aracılığıyla <xref:System.Span%601> örnekleri sabitleyebilir.

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

Önceki örnekte, örneğin, giriş alanı boş ise `pbData` null olabilir. İhraç edilen yöntem, `cbData` 0 olsa bile null olmayan `pbData` gerektiriyorsa, yöntem aşağıdaki gibi uygulanabilir:

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

**Kural #10: zaman uyumsuz bir p/Invoke yöntemi sarmalandıysanız, API 'niz bir parametre olarak bellek\<T > kabul etmelidir.**

Zaman uyumsuz işlemler arasında [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğünü kullanamıyorsanız, örneğin ardışık bellek türünden bağımsız olarak <xref:System.Memory%601> örnekleri sabitlemek için <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> yöntemini kullanırsınız. Aşağıdaki örnek, bu API 'nin zaman uyumsuz p/Invoke çağrısı gerçekleştirmek için nasıl kullanılacağını gösterir.

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
