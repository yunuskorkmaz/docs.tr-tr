---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 1f0d513e8bfd1668ee548315597385c555d374ef
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135782"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Memory\<T > ve Span\<T > kullanım yönergeleri

.NET Core, belleğin rastgele bir bitişik bölgesini temsil eden bir dizi tür içerir. .NET Core 2,0, <xref:System.Span%601> yönetilen <xref:System.ReadOnlySpan%601>veya yönetilmeyen bellekle desteklenen basit bellek arabellekleri olan ve tarafından kullanıma sunulmuştur. Bu türler yalnızca yığında depolanabileceğinden, zaman uyumsuz yöntem çağrıları dahil olmak üzere çok sayıda senaryo için uygun değildir. .NET Core 2,1, <xref:System.Memory%601>,, ve <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601> <xref:System.Buffers.MemoryPool%601>dahil olmak üzere çeşitli ek türler ekler. Benzer <xref:System.Span%601>şekilde <xref:System.Memory%601> ve ilgili türleri hem yönetilen hem de yönetilmeyen bellekle desteklenir. Aksine <xref:System.Span%601>, <xref:System.Memory%601> yönetilen yığında depolanabilir.

Her <xref:System.Span%601> ikisi <xref:System.Memory%601> de, işlem hatlarında kullanılabilecek yapılandırılmış verilerin arabelleklerdir. Diğer bir deyişle, verilerin bazılarının veya tümünün işlem hattındaki bileşenlere etkin bir şekilde geçirilmesi için tasarlanmaları ve isteğe bağlı olarak arabelleği değiştirebilmeleri için tasarlanmıştır. <xref:System.Memory%601> Ve ilgili türlerine birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiğinden, geliştiricilerin sağlam kod üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.

## <a name="owners-consumers-and-lifetime-management"></a>Sahipler, tüketiciler ve ömür yönetimi

Arabellekler API 'Ler arasında geçirilebileceği ve arabelleklerin bazen birden fazla iş parçacığından erişilebilir olduğundan, ömür yönetimini göz önünde bulundurmanız önemlidir. Üç temel kavram vardır:

- **Sahiplik**. Arabellek örneğinin sahibi, artık kullanımda olmadığında arabelleği yok etme da dahil olmak üzere ömür yönetiminden sorumludur. Tüm arabelleklerin tek bir sahibi vardır. Genellikle sahip, arabelleği oluşturan veya bir fabrikadan arabelleği alan bileşendir. Sahiplik da aktarılabilir; **Bileşen-a** arabellek denetimini **bileşen-b**' y e yeniden denetleyebilir ve bu noktada, o nokta **bileşeni-A** artık arabellek kullanamaz ve **bileşen-b** artık kullanımda olmadığında arabelleği yok etmeden sorumlu olur.

- **Tüketim**. Bir arabellek örneğinin tüketicisi, onu okuyarak ve muhtemelen ona yazarak arabellek örneğini kullanmasına izin verilir. Bazı dış eşitleme mekanizması sağlanmadığı takdirde arabellekler tek seferde bir tüketiciye sahip olabilir. Bir arabelleğin etkin tüketicisinin, arabelleğin sahibi olması gerekmediğini unutmayın.

- **Kira**. Kira, belirli bir bileşenin arabelleğin tüketicisi olmasına izin verilen süredir.

Aşağıdaki sözde kod örneğinde bu üç kavram gösterilmektedir. Bu, türünde `Main` <xref:System.Memory%601> <xref:System.Char>bir arabellek örnekleyen bir yöntemi içerir, arabelleğe bir `WriteInt32ToBuffer` tamsayının dize gösterimini yazmak için yöntemini çağırır ve ardından arabelleğin değerini göstermek için `DisplayBufferToConsole` yöntemini çağırır.

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

`Main` Yöntemi, arabelleği oluşturur (Bu durumda bir <xref:System.Span%601> örnek) ve bu nedenle sahibi olur. Bu nedenle `Main` , artık kullanımda olmadığında arabelleği yok etmek sorumludur. Bunu, arabelleğin <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemini çağırarak yapar. (Buradaki <xref:System.Span%601.Clear> Yöntem, arabelleğin belleğini temizler; <xref:System.Span%601> yapının aslında arabelleği yok eden bir yöntemi yoktur.)

Arabellek iki tüketiciye sahiptir `WriteInt32ToBuffer` ve. `DisplayBufferToConsole` Tek seferde yalnızca bir tüketici vardır (ilk `WriteInt32ToBuffer`, sonra `DisplayBufferToConsole`) ve hiçbir tüketicisinin arabelleğe sahip olmadığı. Ayrıca, bu bağlamda "Consumer" öğesinin, arabelleğin salt okunurdur görünümünü göstermez; müşteriler, arabelleğin okuma/yazma görünümü verildiyse, `WriteInt32ToBuffer` olduğu gibi arabelleğin içeriğini değiştirebilir.

`WriteInt32ToBuffer` Yöntemi, yöntem çağrısının başlangıcı ve yöntemin döndürdüğü zaman arasındaki arabelleği (tüketebilir) üzerinde bir kira içerir. Benzer şekilde `DisplayBufferToConsole` , yürütülürken arabellekte bir kiralama vardır ve kira yöntemi zaman içinde serbest bırakılır. (Kiralama Yönetimi için bir API yoktur; "Kira" kavramsal bir kavramdır.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Bellek\<T> ve sahip/tüketici modeli

[Sahipler, tüketiciler ve ömür yönetimi](#owners-consumers-and-lifetime-management) bölümünde, bir arabelleğin her zaman bir sahibi vardır. .NET Core iki sahiplik modelini destekler:

- Tek sahipliği destekleyen bir model. Bir arabelleğin tüm ömrü için tek bir sahibi vardır.

- Sahiplik aktarımını destekleyen bir model. Bir arabelleğin sahipliği, özgün sahibinden (Oluşturucu) başka bir bileşene aktarılabilir ve bu da arabelleğin yaşam süresi yönetiminden sorumludur. Bu sahip, sahipliği başka bir bileşene aktarabilir ve bu şekilde devam eder.

Bir arabelleğin sahipliğini <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> açıkça yönetmek için arabirimini kullanırsınız. <xref:System.Buffers.IMemoryOwner%601>Her iki sahiplik modelini destekler. Bir <xref:System.Buffers.IMemoryOwner%601> başvurusuna sahip olan bileşen, arabelleğe aittir. Aşağıdaki örnek, bir <xref:System.Buffers.IMemoryOwner%601?> <xref:System.Memory%601> arabelleğin sahipliğini yansıtmak için bir örneği kullanır.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Bu örneği ile de yazalım [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Bu kodda:

- Yöntemi örneğin başvurusunu barındırır, bu nedenle `Main` Yöntem arabelleğin sahibidir. <xref:System.Buffers.IMemoryOwner%601> `Main`

- Ve yöntemleri ortak bir API olarak kabul eder <xref:System.Memory%601> `WriteInt32ToBuffer` `DisplayBufferToConsole` Bu nedenle, arabelleğin tüketicilerinden oluşur. Ve tek seferde yalnızca bir tane tüketir.

`WriteInt32ToBuffer` Yöntemi, arabelleğe bir değer yazmaya yönelik olarak düşünülse de `DisplayBufferToConsole` yöntem değildir. Bunu yansıtmak için, türünde <xref:System.ReadOnlyMemory%601>bir bağımsız değişkeni kabul etmiş olabilir. Hakkında <xref:System.ReadOnlyMemory%601>daha fazla bilgi için bkz. [Kural #2: arabelleğin salt-\<okunabilir olması gerekiyorsa, readonlyspan t> veya Readonlymemory\<t> kullanın](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"OwnerLeSs" bellek\<T> örnekleri

Kullanmadan <xref:System.Memory%601> <xref:System.Buffers.IMemoryOwner%601>bir örnek oluşturabilirsiniz. Bu durumda, arabelleğin sahipliği açık yerine örtük olur ve yalnızca tek sahip modeli desteklenir. Bunu şu şekilde yapabilirsiniz:

- <xref:System.Memory%601> Oluşturuculardan birini doğrudan çağırmak, aşağıdaki örnekte olduğu gibi `T[]`bir ' a geçirerek.

- Bir `ReadOnlyMemory<char>` örnek oluşturmak için [String. asmemory](xref:System.MemoryExtensions.AsMemory(System.String)) genişletme yöntemi çağrılıyor.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

İlk olarak <xref:System.Memory%601> örneği oluşturan yöntemi, arabelleğin örtük sahibidir. Aktarımı kolaylaştırmak için bir <xref:System.Buffers.IMemoryOwner%601> örnek bulunmadığından, sahiplik başka bir bileşene aktarılamaz. (Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiği da hayal edebilirsiniz.)

## <a name="usage-guidelines"></a>Kullanım yönergeleri

Bir bellek bloğunun sahibi olduğu, ancak bazıları aynı anda belirli bir bellek bloğunun üzerinde çalışabilen birden çok bileşene geçirilmesi amaçlanan için, hem hem de <xref:System.Memory%601> kullanımı için kılavuz oluşturulması önemlidir. <xref:System.Span%601>  Şu nedenle yönergeler gereklidir:

- Bir bileşenin sahibi serbest bırakıldıktan sonra bir bellek bloğunun başvurusunu bekletmek mümkündür.

- Bir bileşenin, başka bir bileşenin üzerinde çalıştığı aynı anda bir arabellekte çalışması, işlemin arabellekteki verileri bozuyor olması mümkündür.

- Yığın tarafından ayrılan doğası performansı <xref:System.Span%601> iyileştirir ve tercih edilen türü bir <xref:System.Span%601> bellek bloğunda çalıştırmak için, bu da bazı önemli kısıtlamalara de <xref:System.Span%601> neden olur. Ne zaman kullanacağınızı <xref:System.Span%601> ve ne zaman kullanılacağını bilmemiz önemlidir <xref:System.Memory%601>.

Aşağıdakiler ve ilgili türleri başarıyla kullanılarak <xref:System.Memory%601> önerimlerimiz aşağıda verilmiştir. İçin <xref:System.Memory%601> geçerli olan ve <xref:System.Span%601> Ayrıca, açıkça aksi belirtilmedikçe ve <xref:System.ReadOnlyMemory%601> <xref:System.ReadOnlySpan%601> için geçerli olan yönergelerin olduğunu unutmayın.

**Kural #1: zaman uyumlu bir API Için, mümkünse\<bir parametre olarak> bellek\<t yerine> span t kullanın.**

<xref:System.Span%601>daha çok daha hızlıdır <xref:System.Memory%601> ve çok sayıda bitişik bellek arabelleğini temsil edebilir. <xref:System.Span%601>Ayrıca, daha iyi performans <xref:System.Memory%601>sunar. Son olarak, <xref:System.Memory%601.Span?displayProperty=nameWithType> <xref:System.Memory%601> özelliği bir örneği bir <xref:System.Span%601>örneğine dönüştürmek için kullanabilirsiniz, ancak\<t>-bellek\<t> dönüştürme mümkün olmaz. Bu nedenle, arayanların bir <xref:System.Memory%601> örneği varsa, yöntemlerinizi yine de <xref:System.Span%601> parametrelerle çağırabileceksiniz.

Türü yerine türünde <xref:System.Span%601> bir parametre kullanılması, doğru <xref:System.Memory%601> bir tüketen Yöntem uygulamasını yazmanıza de yardımcı olur. Metodun kira süresinin ötesinde (daha sonra bu konuda daha fazla) arabelleğe erişmeye girişdiğinizden emin olmak için otomatik olarak derleme zamanı denetimleri alacaksınız.

Bazen, tam olarak zaman uyumlu olsanız bile <xref:System.Memory%601> <xref:System.Span%601> parametre yerine bir parametre kullanmanız gerekecektir. Büyük olasılıkla bağlı olduğunuz bir API yalnızca <xref:System.Memory%601> bağımsız değişkenleri kabul eder. Bu sorun iyidir, ancak eşzamanlı olarak kullanılırken <xref:System.Memory%601> ilgili olan avantajları göz önünde bulundurun.

<a name="rule-2" />

**Kural #2: arabelleğin Salt okunabilir olması\<gerekiyorsa ReadOnlySpan t>\<veya readonlymemory t> kullanın.**

Önceki örneklerde `DisplayBufferToConsole` Yöntem yalnızca arabellekten okur; arabelleğin içeriğini değiştirmez. Yöntem imzası aşağıdaki şekilde değiştirilmelidir.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Aslında, bu kuralı ve kuralı #1 birleştirirseniz, daha iyi bir şekilde yapabiliriz ve yöntem imzasını aşağıdaki gibi yeniden yazabilirsiniz:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` Yöntemi artık hemen her arabellek türü kodlamalardaki: `T[]`, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış depolama ve benzeri ile çalışmaktadır. Hatta doğrudan ' a <xref:System.String> geçirebilirsiniz!

**Kural #3: yönteminiz, bellek\<t> ve döndürürse `void`, yönteminizin döndürdüğü bir bellek\<t> örneğini kullanmamalıdır.**

Bu, daha önce bahsedilen "Kira" kavramıyla ilgilidir. <xref:System.Memory%601> Örnek üzerinde void döndüren bir yöntemin kirası, yöntem girildiğinde başlar ve Yöntem çıktığında sonlanır. Bir döngüde konsolundan gelen giriş temelinde `Log` çağıran aşağıdaki örneği göz önünde bulundurun.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

`Log` Tamamen zaman uyumlu bir yöntem ise, belirli bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi olduğundan bu kod beklendiği gibi davranır.
Ancak bu uygulamayı içeren `Log` yerine Imagine.

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

Bu uygulamada, `Log` özgün Yöntem döndürülbaşladıktan sonra <xref:System.Memory%601> örneği hala arka planda kullanmaya çalıştığı için kiralamasını ihlal ediyor. `Main` Yöntem, bir arabelleği okumaya çalışırken `Log` , veri bozulmasına yol açabilir.

Bu sorunu çözmek için birkaç yol vardır:

- `Log` Yöntemi, `Log` yönteminin aşağıdaki uygulanması <xref:System.Threading.Tasks.Task> olduğundan `void`, yerine bir döndürebilir.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`Bunun yerine, aşağıdaki gibi uygulanabilir:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Kural #4: yönteminiz bir bellek\<t> kabul eder ve bir görevi döndürürse, görev bir Terminal durumuna geçirdikten sonra bellek\<t> örneğini kullanmanız gerekir.**

Bu yalnızca kural #3 zaman uyumsuz bir değişkendir. Önceki `Log` örnekteki yöntem bu kurala uymak için aşağıdaki gibi yazılabilir:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Burada "Terminal durumu", görevin tamamlanmış, hatalı veya iptal edilmiş durumuna geçirdiğinin anlamına gelir. Diğer bir deyişle "Terminal durumu", "çalışmasına neden olan herhangi bir şey" anlamına gelir ve yürütme devam eder. "

Bu kılavuz, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>,, veya benzer bir tür döndüren yöntemler için geçerlidir.

**Kural #5: oluşturucunuz bir parametre olarak\<bellek t> kabul ediyorsa, oluşturulan nesnedeki örnek yöntemlerinin, bellek\<t> örneğinin tüketicileri olduğu varsayılır.**

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

`OddValueExtractor` Burada Oluşturucu bir oluşturucu parametresi `ReadOnlyMemory<int>` olarak kabul eder, bu nedenle oluşturucunun kendisi `ReadOnlyMemory<int>` örneğin bir tüketicisidir ve döndürülen değer içindeki tüm örnek yöntemleri de orijinal `ReadOnlyMemory<int>` örneğin tüketicisidir. Bu, örneğin `TryReadNextOddValue` , örnek `ReadOnlyMemory<int>` doğrudan `TryReadNextOddValue` yöntemine geçirilmese de örneği tükettiği anlamına gelir.

**Kural #6: türinizde ayarlanabilir bir> bellek\<(veya eşdeğer bir örnek yöntemi) varsa, söz konusu nesnedeki örnek yöntemleri bellek\<t> örneğinin tüketicileri olduğu varsayılır.**

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

**Kural #7: bir ımemoryowner\<T> başvurunuz varsa, bu dosyanın bir noktası atılmalıdır veya sahipliğini (her ikisi de değil) aktarırsınız.**

Bir <xref:System.Memory%601> örnek yönetilen veya yönetilmeyen bellek tarafından yönetilebileceği için, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> <xref:System.Memory%601> örnek üzerinde gerçekleştirilen iş tamamlandığında sahip çağrısı gerekir. Alternatif olarak, sahip, <xref:System.Buffers.IMemoryOwner%601> örneğin sahipliğini farklı bir bileşene aktarabilir, bu noktada alma bileşeni uygun zamanda (Bu daha sonra daha fazla) <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> (daha fazla daha fazla) çağrı yapmaktan sorumlu olur.

Yöntemi çağıramaması, <xref:System.Buffers.MemoryPool%601.Dispose%2A> yönetilmeyen bellek sızıntılarına veya diğer performans düşüşüne neden olabilir.

Bu kural, gibi <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>Fabrika yöntemlerini çağıran kod için de geçerlidir. Çağıran, döndürülen <xref:System.Buffers.IMemoryOwner%601> sahibi olur ve tamamlandığında örneği elden atma sorumludur.

**Kural #8: API yüzeyinizde bir ımemoryowner\<T> parametresi varsa, bu örneğin sahipliğini kabul etmiş olursunuz.**

Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı amaçladığı sinyallere işaret eder. Bileşeniniz, kural #7 göre uygun elden çıkarılmasından sorumludur.

<xref:System.Buffers.IMemoryOwner%601> Örneğin sahipliğini farklı bir bileşene aktaran herhangi bir bileşen, yöntem çağrısının tamamlanmasından sonra bu örneği artık kullanmamalıdır.

> [!IMPORTANT]
> Oluşturucunuzu bir parametre <xref:System.Buffers.IMemoryOwner%601> olarak kabul ediyorsa, türünün uygulanması <xref:System.IDisposable>gerekir ve <xref:System.IDisposable.Dispose%2A> yöntemi çağırmalıdır. <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>

**Kural #9: zaman uyumlu bir p/Invoke yöntemini sardıysanız, API 'niz bir parametre olarak span\<T> kabul etmelidir.**

Kural #1 <xref:System.Span%601> göre genellikle zaman uyumlu API 'ler için kullanılan doğru türdür. Aşağıdaki örnekte olduğu <xref:System.Span%601> gibi, örnekleri [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) anahtar sözcük aracılığıyla sabitleyebilirsiniz.

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

Örneğin, giriş alanı boş `pbData` ise, önceki örnekte null olabilir. İçe aktarılmış Yöntem, 0 olsa bile `pbData` `cbData` null olmayan bir değer gerektiriyorsa, yöntemi aşağıdaki gibi uygulanabilir:

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

**Kural #10: zaman uyumsuz bir p/Invoke yöntemi sarmalandıysanız, API 'niz bir parametre olarak\<bellek T> kabul etmelidir.**

[`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) Anahtar sözcüğünü zaman uyumsuz işlemler arasında kullanamıyorsanız, örneğin ardışık bellek türünden <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> bağımsız olarak örnekleri <xref:System.Memory%601> sabitlemek için yöntemini kullanırsınız. Aşağıdaki örnek, bu API 'nin zaman uyumsuz p/Invoke çağrısı gerçekleştirmek için nasıl kullanılacağını gösterir.

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
    var actualState = (MyCompletedCallbackState)(handle.Target);
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
