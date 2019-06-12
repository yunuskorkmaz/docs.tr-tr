---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380c0eef137eb5142c30e63f5446f5d60723087a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834052"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Bellek\<T > ve aralık\<T > kullanım yönergeleri

.NET core, bir rastgele bitişik bellek bölgesini temsil eden türler içerir. .NET core 2.0 kullanılmaya <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601>, yönetilen veya yönetilmeyen bellek tarafından yedeklenen hafif bellek arabelleği olduğu. Yığın üzerinde bu türleri depolanabilir olduğundan, bunlar zaman uyumsuz yöntem çağrıları gibi senaryolar, bir dizi için uygun değil. .NET core 2.1 ekler gibi ek türleri sayısı <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, ve <xref:System.Buffers.MemoryPool%601>. Gibi <xref:System.Span%601>, <xref:System.Memory%601> ve ilgili türlerinden tarafından yönetilen ve yönetilmeyen bellek yedeklenebilir. Farklı <xref:System.Span%601>, <xref:System.Memory%601> yalnızca yönetilen yığında depolanabilir.

Her ikisi de <xref:System.Span%601> ve <xref:System.Memory%601> hatlarında kullanılabilir yapılandırılmış verilerin arabellek. Böylece onları işleyebilir ve isteğe bağlı olarak önbelleği değiştiren bileşenleri için ardışık düzeninde, bazı veya tüm verileri verimli bir şekilde geçirilebilir diğer bir deyişle, bunlar tasarlanmıştır. Çünkü <xref:System.Memory%601> ve ilgili türlerinden erişilebilir birden çok bileşen veya birden çok iş parçacığı tarafından geliştiricilerin güçlü kod üretmek için bazı standart kullanım yönergeleri takip edin önemlidir.

## <a name="owners-consumers-and-lifetime-management"></a>Sahipleri, tüketicilere ve ömür Yönetimi

Arabellekler etrafında ve API arasında arabelleklere bazen birden çok iş parçacığı tarafından erişilebilir olduğundan geçirilebilir olduğundan, ömür Yönetimi dikkate almak önemlidir. Üç temel kavram vardır:

- **Sahipliği**. Sahibi bir arabellek örneğinin kullanım ömrü Yönetimi artık kullanımda olmadığında arabellek yok etme içeren sorumludur. Tüm arabellekler tek bir sahip. Genellikle sahibi, arabellek oluşturulan veya, bir fabrikadan arabelleğe alınan bileşendir. Sahiplik da aktarılabilir; **Bileşen A** arabelleğe denetimin teknisyene **bileşeni B**, hangi noktada **bileşen A** arabellek artık kullanabilir ve **bileşen B**  artık kullanımda olmadığında arabellek yok etme için sorumlu olur.

- **Tüketim**. Tüketici bir arabellek örneğinin arabellek örneği buradan okuma ve büyük olasılıkla yazma kullanmasına izin verilir. Bazı dış eşitleme mekanizması sağlanmadığı sürece arabellekler aynı anda tek bir tüketici olabilir. Etkin kullanıcısı olan bir arabellek arabellek sahibi olmak zorunda olmadığını unutmayın.

- **Kira**. Belirli bir bileşene arabellek tüketici izin verilen süre kira var.

Aşağıdaki sözde kod örneği, bu üç kavramı gösterir. İçerdiği bir `Main` başlatan yöntem bir <xref:System.Memory%601> arabellek türü <xref:System.Char>, çağrıları `WriteInt32ToBuffer` tamsayı dize gösterimini arabellek ve ardından çağrıları yazma yöntemi `DisplayBufferToConsole` değerini görüntülemek için yöntemi arabellek.

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

`Main` Yöntemi arabellek oluşturur (Bu durumda bir <xref:System.Span%601> örnek) sahibi olur. Bu nedenle, `Main` artık kullanımda olmadığında arabellek yok etme için sorumludur. Bunu arabellek çağırarak yapar <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemi. ( <xref:System.Span%601.Clear> Yöntemi burada gerçekten temizler arabellek belleği; <xref:System.Span%601> yapısı gerçekten arabellek yok eder bir yöntem yok.)

Arabellek iki Tüketiciler, sahip `WriteInt32ToBuffer` ve `DisplayBufferToConsole`. Aynı anda yalnızca tek bir tüketici yoktur (ilk `WriteInt32ToBuffer`, ardından `DisplayBufferToConsole`), ve tüketiciler hiçbiri arabellek sahip. Ayrıca, bu bağlamda "Müşteri" bir salt okunur görünüm arabellek yaptığından emin değil unutmayın; Tüketiciler arabellek içeriği olarak değiştirebilirsiniz `WriteInt32ToBuffer` bir arabellek okuma/yazma görünümünü verildiyse yapar.

`WriteInt32ToBuffer` Yöntemi sahip bir kira (kullanabilir) yöntem çağrısının başlangıcı ve yöntemi döndürür. saat arasındaki arabellek. Benzer şekilde, `DisplayBufferToConsole` Yürütülüyor iken arabelleği bir kira var ve yöntem geriye doğru izler kira serbest kalır. (Kiralama yönetimi için hiçbir API yoktur; "kira" kavramsal bir konudur.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Bellek\<T > ve sahibi/tüketici modeli

Olarak [sahipleri, tüketicilere ve ömür Yönetimi](#owners-consumers-and-lifetime-management) bölümünde Not, bir arabellek her zaman bir sahip vardır. .NET core iki sahipliği modeli destekler:

- Tek sahipliği destekleyen bir model. Arabellek tüm yaşam süresi için tek bir kullanıcıya sahiptir.

- Bir modeli sahipliğinin aktarılmasını destekler. Arabellek sahipliğini özgün sahibi (oluşturana), ardından arabellek ömür yönetimi için sorumlu olur başka bir bileşene aktarılabilir. Bu sahibi sırayla sahipliğini başka bir bileşene ve benzeri.

Kullandığınız <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> açıkça bir arabellek sahipliğini yönetmek için arabirim. <xref:System.Buffers.IMemoryOwner%601> Her iki sahipliği modelleri destekler. Sahip bileşen bir <xref:System.Buffers.IMemoryOwner%601> başvuru arabellek sahip. Aşağıdaki örnekte bir <xref:System.Buffers.IMemoryOwner%601?> sahipliğini yansıtmak için örnek bir <xref:System.Memory%601> arabellek.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Bu örnekle aynı zamanda yazabiliriz [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Bu kod:

- `Main` Yöntemi başvuru tutan <xref:System.Buffers.IMemoryOwner%601> örneği, bu nedenle `Main` yöntemi arabellek sahibidir.

- `WriteInt32ToBuffer` Ve `DisplayBufferToConsole` yöntemleri kabul <xref:System.Memory%601> Genel API olarak. Bu nedenle, arabellek tüketicilerinin altındadır. Ve bunların yalnızca birini tüketicilerimizin birer güncelleştirir.

Ancak `WriteInt32ToBuffer` yöntemi bir değer arabelleğe yazmak için tasarlanmıştır `DisplayBufferToConsole` yöntemi değildir. Bunu yansıtmak için onu türünde bir bağımsız değişken kabul ettiğini <xref:System.ReadOnlyMemory%601>. Hakkında daha fazla bilgi için <xref:System.ReadOnlyMemory%601>, bkz: [Kural 2: ReadOnlySpan kullanın\<T > ya da ReadOnlyMemory\<T > salt okunur arabellek olması gerekiyorsa](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"Ownerless" bellek\<T > örnekleri

Oluşturabileceğiniz bir <xref:System.Memory%601> kullanmadan örneği <xref:System.Buffers.IMemoryOwner%601>. Bu durumda, arabellek sahiplik açık ve yalnızca yerine örtük tek sahip model desteklenir. Bunu yapabilirsiniz:

- Birini çağırma <xref:System.Memory%601> oluşturucular doğrudan öğesinde geçen bir `T[]`, aşağıdaki örnekte olduğu gibi.

- Çağırma [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) üretmek için genişletme yöntemi bir `ReadOnlyMemory<char>` örneği.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

Başlangıçta oluşturan yöntemine <xref:System.Memory%601> arabellek örtük sahibi örneğidir. Sahipliği olduğundan başka bir bileşen için aktarılamaz hiçbir <xref:System.Buffers.IMemoryOwner%601> aktarımı kolaylaştırmak için örneği. (Alternatif olarak, ayrıca çalışma zamanının atık toplayıcısı arabellek sahibi ve tüm yöntemleri yalnızca arabellek tüketen hayal edebilirsiniz.)

## <a name="usage-guidelines"></a>Kullanım yönergeleri

Bir bellek bloğuna sahip olduğu ancak bazıları çalışan belirli bellek bloğu üzerinde aynı anda birden çok bileşeni için geçirilecek yöneliktir çünkü her ikisi de kullanma yönergeleri kurmak daha önemlidir <xref:System.Memory%601> ve <xref:System.Span%601>.  Yönergeleri gereklidir çünkü:

- Bir bileşen sahibi kullanıma sundu sonra bellek bloğu için bir başvuru korumak mümkündür.

- Bir bileşen başka bir bileşen üzerinde arabellekteki verileri bozmasına işlemde çalıştığından aynı anda bir arabellek üzerinde çalışılacak mümkündür.

- Yığın ayırma yapısını while <xref:System.Span%601> performansı en iyi duruma getirir ve yapar <xref:System.Span%601> Ayrıca, bir bellek bloğu üzerinde çalışmak tercih edilen türünü konuları <xref:System.Span%601> bazı önemli kısıtlamaları. Ne zaman kullanılacağını bilmek önemlidir bir <xref:System.Span%601> ve ne zaman kullanılacağı <xref:System.Memory%601>.

Aşağıdakiler önerilerimizle başarıyla kullanmak için <xref:System.Memory%601> ve ilgili türleri. Geçerli Kılavuzu unutmayın <xref:System.Memory%601> ve <xref:System.Span%601> için de geçerlidir <xref:System.ReadOnlyMemory%601> ve <xref:System.ReadOnlySpan%601> sürece biz açıkça aksi unutmayın.

**Kural #1: Aralık için zaman uyumlu bir API kullanmak\<T > bellek yerine\<T > mümkünse bir parametre olarak.**

<xref:System.Span%601> Daha fazla yönlüdür <xref:System.Memory%601> ve çok çeşitli bitişik bellek arabelleği temsil edebilir. <xref:System.Span%601> Ayrıca performans teklifler daha iyi <xref:System.Memory%601>. Son olarak, kullanabileceğiniz <xref:System.Memory%601.Span?displayProperty=nameWithType> dönüştürmek için özellik bir <xref:System.Memory%601> için örnek bir <xref:System.Span%601>, aralık ancak\<T > - to - bellek\<T > dönüştürme mümkün değil. Bunu, Arayanların varsa bir <xref:System.Memory%601> örneği, bunlar yapabileceksiniz yöntemlerinizi ile çağrılacak <xref:System.Span%601> parametreleri yine de.

Türünde bir parametre kullanarak <xref:System.Span%601> tür yerine <xref:System.Memory%601> de doğru kullanan bir yöntem uygulaması yazma yardımcı olur. Derleme zamanı denetimleri, arabellek, yöntemin kira (daha sonra bu) ötesinde erişmeye çalıştığınız değil emin olmak için otomatik olarak alırsınız.

Bazı durumlarda kullanmak zorunda kalırsınız bir <xref:System.Memory%601> yerine parametre bir <xref:System.Span%601> parametresi, tam olarak zaman uyumlu olsa bile. Belki de yalnızca kullandığınız bir API kabul <xref:System.Memory%601> bağımsız değişkenler. Bu bir sakınca yoktur ancak alışverişler kullanırken dikkat <xref:System.Memory%601> zaman uyumlu olarak.

<a name="rule-2" />

**#2. kural: ReadOnlySpan kullanın\<T > ya da ReadOnlyMemory\<T > salt okunur arabellek olması gerekiyorsa.**

Önceki örneklerde, `DisplayBufferToConsole` yöntemi yalnızca arabellekteki okur; arabellek içeriğini değiştirmez. Yöntem imzası, aşağıdaki değiştirilmelidir.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Aslında, bu kural ve kural 1 birleştirdik, biz daha da iyi yapın ve yöntem imzası şu şekilde yeniden yazın:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` Yöntemi hemen her arabellek türü hayal nasıl çalıştığını: `T[]`, depolama ile ayrılmış [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md)ve benzeri. Hatta geçirebilirsiniz bir <xref:System.String> doğrudan alın!

**#3. kural: Bellek yönteminizin kabul ediyorsa\<T > ve döndürür `void`, bellek kullanmamalıdır\<T >, yöntemin dönüşünün ardından örnek.**

Bu, daha önce bahsedilen "kira" kavramı ilişkilendirir. Void döndüren yöntemin kira <xref:System.Memory%601> örneği yöntemi girilir ve yöntemi çıktığında bunu bittiğinde başlar. Çağıran aşağıdaki örneği inceleyin `Log` konsolundan giriş göre döngü içinde.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Varsa `Log` tamamen zaman uyumlu bir yöntem bu kodu herhangi bir zamanda yalnızca bir etkin tüketici bellek örneğinin olduğundan beklendiği gibi davranır.
Ancak bunun yerine, Imagine `Log` bu uygulamaya sahiptir.

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

Bu uygulamada `Log` onu kullanmaya çalışır çünkü kirasını ihlal <xref:System.Memory%601> asıl yöntemi döndürdü sonra arka planda örneği. `Main` Yöntemi sırasında arabellek bulunmamalıdır `Log` kendisinden okumak veri bozulmasına neden çalışır.

Bu sorunu çözmek için birçok yol vardır:

- `Log` Yöntemi döndürebilir bir <xref:System.Threading.Tasks.Task> yerine `void`, aşağıdaki uygulaması olarak `Log` yöntemi yapar.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log` Bunun yerine şu şekilde uygulanabilir:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Kural #4: Bir bellek yönteminizin kabul ediyorsa\<T > ve bir görev döndürür bellek kullanmamalıdır\<T > Görev geçişlerini terminal durumuna sonra örneği.**

Kural 3 yalnızca zaman uyumsuz çeşidini budur. `Log` Yöntemi önceki örnekle yazılabilir gibi bu kurala uygun:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Burada, görev geçişleri tamamlandı, hatalı veya iptal edildi durumu "terminal durumuna" anlamına gelir. Diğer bir deyişle, "terminal durumuna" anlamına gelir "neden olan herhangi bir şey await throw veya yürütmeye devam et."

Bu kılavuz döndüren yöntemler için geçerlidir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, veya benzer bir tür.

**Kural #5: Güvenlik denetimini atladığından bellek kabul ediyorsa\<T > parametre olarak, oluşturulan nesne üzerinde örnek yöntemleri bellek tüketicilerinin olarak kabul edilir\<T > örneği.**

Aşağıdaki örnek göz önünde bulundurun:

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

Burada, `OddValueExtractor` Oluşturucusu kabul eden bir `ReadOnlyMemory<int>` Oluşturucu parametresi olarak, bu nedenle Oluşturucusu olan bir tüketicisi `ReadOnlyMemory<int>` örneği ve döndürülen değer tüm örnek yöntemler olan ayrıca orijinal tüketicilerinin `ReadOnlyMemory<int>` örneği. Diğer bir deyişle `TryReadNextOddValue` tüketir `ReadOnlyMemory<int>` örneği doğrudan geçirilen değil olsa da, örnek `TryReadNextOddValue` yöntemi.

**Kural #6: Ayarlanabilir bir bellek varsa\<T >-örnek yöntemler bu nesne, türü belirlenmiş bir özellik (veya eşdeğer bir örnek yöntemi) varsayılır bellek tüketicilerinin\<T > örneği.**

Bu aslında bir kural 5 çeşididir. Özellik ayarlayıcılarına veya eşdeğer yöntemleri yakalamak ve yakalanan durum kullanabilen aynı nesne üzerinde örnek yöntemleri için kendi girişleri kalıcı hale getirmek için kabul edilir çünkü bu kuralı yok.

Aşağıdaki örnek, bu kural tetiklenir:

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

**#7. kural: Bir IMemoryOwner varsa\<T > başvuru, bir noktada bunu dispose noktası veya gerekir sahipliğini (ancak her ikisini birden değil) aktarım.**

Bu yana bir <xref:System.Memory%601> örneği tarafından yönetilen veya yönetilmeyen bellek yedeklenen, sahibi çağırmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> iş zaman gerçekleştirilen <xref:System.Memory%601> örneği tamamlandığında. Alternatif olarak, sahibi sahipliğini aktarabilir <xref:System.Buffers.IMemoryOwner%601> hangi noktada alınırken bir bileşen için arama sorumlu olur, farklı bir bileşen örneğine <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> (Bu, daha sonra daha fazla) uygun zamanda.

Aranacak hata <xref:System.Buffers.MemoryPool%601.Dispose%2A> yöntemi yönetilmeyen bellek sızıntısı veya diğer performans düşüşüne neden olabilir.

Bu kural gibi Fabrika yöntemleri çağıran kod için de geçerlidir. <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. Arayan döndürülen sahibi olur <xref:System.Buffers.IMemoryOwner%601> ve bittiğinde örneğini disposing için sorumludur.

**Kural #8: Bir IMemoryOwner varsa\<T > parametresi, API yüzeyi, bu örneğe sahipliğini kabul edersiniz.**

Bu türün örneğini kabul bileşenin bu örneği sahipliğini amaçlayan bildirir. Bileşeniniz düzgün bir şekilde elden kural #7 göre sorumlu olur.

Sahipliğini aktaran herhangi bir bileşeni <xref:System.Buffers.IMemoryOwner%601> yöntem çağrısı tamamlandığında örneği farklı bir bileşen için bu örneği artık kullanmalıdır.

> [!IMPORTANT]
> Güvenlik denetimini atladığından kabul ediyorsa <xref:System.Buffers.IMemoryOwner%601> türünü bir parametre olarak, uygulamalıdır <xref:System.IDisposable>ve <xref:System.IDisposable.Dispose%2A> yöntemini çağırma <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**Kural #9: Bir zaman uyumlu p/Invoke yöntemi sarmalama, API'nizi yayılma kabul etmelidir\<T > parametre olarak.**

Kural 1 göre <xref:System.Span%601> genellikle zaman uyumlu API'leri için kullanılacak doğru türüdür. Sabitleyebilmeniz için <xref:System.Span%601> aracılığıyla örnekler [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) aşağıdaki örnekteki gibi anahtar sözcüğü.

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

Önceki örnekte, `pbData` Örneğin, giriş aralık boş ise null olabilir. Dışarı aktarılan yöntemi kesinlikle gerektiriyorsa `pbData` null olmayan, olması bile `cbData` 0 ise, yöntem şu şekilde uygulanabilir:

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

**#10 kuralı: Bir zaman uyumsuz p/Invoke yöntemi sarmalama, API'nizi bellek kabul etmelidir\<T > parametre olarak.**

Bu yana kullanamazsınız [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğü arasında zaman uyumsuz işlemler, kullandığınız <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> sabitlemek yöntemi <xref:System.Memory%601> örnekleri, örnekteki bitişik bellek türü ne olursa olsun. Aşağıdaki örnek, bir zaman uyumsuz p/Invoke araması gerçekleştirmek için bu API kullanmayı gösterir.

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
