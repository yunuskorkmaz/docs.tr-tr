---
title: Memory<T> ve Span<T> kullanım yönergeleri
description: Bu makalede <T> <T> , .NET Core 'da işlem hatları 'nda kullanılabilecek yapılandırılmış verilerin arabellekleri olan bellek ve yayılma açıklanmaktadır.
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: cb9075a12bb8d842cd8e937e74f8869c910fc0ab
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201934"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Memory\<T> ve Span\<T> kullanım yönergeleri

.NET Core, belleğin rastgele bir bitişik bölgesini temsil eden bir dizi tür içerir. .NET Core 2,0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> , yönetilen veya yönetilmeyen bellekle desteklenen basit bellek arabellekleri olan ve tarafından kullanıma sunulmuştur. Bu türler yalnızca yığında depolanabileceğinden, zaman uyumsuz yöntem çağrıları dahil olmak üzere çok sayıda senaryo için uygun değildir. .NET Core 2,1,,, ve dahil olmak üzere çeşitli ek türler ekler <xref:System.Memory%601> <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601> <xref:System.Buffers.MemoryPool%601> . Benzer <xref:System.Span%601> şekilde <xref:System.Memory%601> ve ilgili türleri hem yönetilen hem de yönetilmeyen bellekle desteklenir. Aksine <xref:System.Span%601> , <xref:System.Memory%601> yönetilen yığında depolanabilir.

Her ikisi de, işlem hatlarında <xref:System.Span%601> <xref:System.Memory%601> kullanılabilecek yapılandırılmış verilerin arabelleklerdir. Diğer bir deyişle, verilerin bazılarının veya tümünün işlem hattındaki bileşenlere etkin bir şekilde geçirilmesi için tasarlanmaları ve isteğe bağlı olarak arabelleği değiştirebilmeleri için tasarlanmıştır. <xref:System.Memory%601>Ve ilgili türlerine birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiğinden, geliştiricilerin sağlam kod üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.

## <a name="owners-consumers-and-lifetime-management"></a>Sahipler, tüketiciler ve ömür yönetimi

Arabellekler API 'Ler arasında geçirilebileceği ve arabelleklerin bazen birden fazla iş parçacığından erişilebilir olduğundan, ömür yönetimini göz önünde bulundurmanız önemlidir. Üç temel kavram vardır:

- **Sahiplik**. Arabellek örneğinin sahibi, artık kullanımda olmadığında arabelleği yok etme da dahil olmak üzere ömür yönetiminden sorumludur. Tüm arabelleklerin tek bir sahibi vardır. Genellikle sahip, arabelleği oluşturan veya bir fabrikadan arabelleği alan bileşendir. Sahiplik da aktarılabilir; **Bileşen-a** arabellek denetimini **bileşen-b**' y e yeniden denetleyebilir ve bu noktada, o nokta **bileşeni-A** artık arabellek kullanamaz ve **bileşen-b** artık kullanımda olmadığında arabelleği yok etmeden sorumlu olur.

- **Tüketim**. Bir arabellek örneğinin tüketicisi, onu okuyarak ve muhtemelen ona yazarak arabellek örneğini kullanmasına izin verilir. Bazı dış eşitleme mekanizması sağlanmadığı takdirde arabellekler tek seferde bir tüketiciye sahip olabilir. Bir arabelleğin etkin tüketicisi, arabelleğin sahibi değildir.

- **Kira**. Kira, belirli bir bileşenin arabelleğin tüketicisi olmasına izin verilen süredir.

Aşağıdaki sözde kod örneğinde bu üç kavram gösterilmektedir. Bu `Main` , türünde bir arabellek örnekleyen bir yöntemi içerir <xref:System.Memory%601> <xref:System.Char> , `WriteInt32ToBuffer` arabelleğe bir tamsayının dize gösterimini yazmak için yöntemini çağırır ve ardından `DisplayBufferToConsole` arabelleğin değerini göstermek için yöntemini çağırır.

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

`Main`Yöntemi, arabelleği oluşturur (Bu durumda bir <xref:System.Span%601> örnek) ve bu nedenle sahibi olur. Bu nedenle, `Main` artık kullanımda olmadığında arabelleği yok etmek sorumludur. Bunu, arabelleğin yöntemini çağırarak yapar <xref:System.Span%601.Clear?displayProperty=nameWithType> . ( <xref:System.Span%601.Clear> Buradaki Yöntem, arabelleğin belleğini temizler; <xref:System.Span%601> yapının aslında arabelleği yok eden bir yöntemi yoktur.)

Arabellek iki tüketiciye sahiptir `WriteInt32ToBuffer` ve `DisplayBufferToConsole` . Tek seferde yalnızca bir tüketici vardır (ilk `WriteInt32ToBuffer` , sonra `DisplayBufferToConsole` ) ve hiçbir tüketicisinin arabelleğe sahip olmadığı. Ayrıca, bu bağlamda "Consumer" öğesinin, arabelleğin salt okunurdur görünümünü göstermez; müşteriler, arabelleğin `WriteInt32ToBuffer` okuma/yazma görünümü verildiyse, olduğu gibi arabelleğin içeriğini değiştirebilir.

Yöntemi, `WriteInt32ToBuffer` yöntem çağrısının başlangıcı ve yöntemin döndürdüğü zaman arasındaki arabelleği (tüketebilir) üzerinde bir kira içerir. Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kiralama vardır ve kira yöntemi zaman içinde serbest bırakılır. (Kiralama Yönetimi için bir API yoktur; "Kira" kavramsal bir kavramdır.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Bellek \<T> ve sahip/tüketici modeli

[Sahipler, tüketiciler ve ömür yönetimi](#owners-consumers-and-lifetime-management) bölümünde, bir arabelleğin her zaman bir sahibi vardır. .NET Core iki sahiplik modelini destekler:

- Tek sahipliği destekleyen bir model. Bir arabelleğin tüm ömrü için tek bir sahibi vardır.

- Sahiplik aktarımını destekleyen bir model. Bir arabelleğin sahipliği, özgün sahibinden (Oluşturucu) başka bir bileşene aktarılabilir ve bu da arabelleğin yaşam süresi yönetiminden sorumludur. Bu sahip, sahipliği başka bir bileşene aktarabilir ve bu şekilde devam eder.

<xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>Bir arabelleğin sahipliğini açıkça yönetmek için arabirimini kullanırsınız. <xref:System.Buffers.IMemoryOwner%601>Her iki sahiplik modelini destekler. Bir başvurusuna sahip olan bileşen <xref:System.Buffers.IMemoryOwner%601> , arabelleğe aittir. Aşağıdaki örnek, <xref:System.Buffers.IMemoryOwner%601?> bir arabelleğin sahipliğini yansıtmak için bir örneği kullanır <xref:System.Memory%601> .

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Bu örneği ile de yazalım [`using`](../../csharp/language-reference/keywords/using-statement.md) :

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Bu kodda:

- `Main`Yöntemi örneğin başvurusunu barındırır <xref:System.Buffers.IMemoryOwner%601> , bu nedenle `Main` Yöntem arabelleğin sahibidir.

- `WriteInt32ToBuffer`Ve `DisplayBufferToConsole` yöntemleri <xref:System.Memory%601> ortak bir API olarak kabul eder. Bu nedenle, arabelleğin tüketicilerinden oluşur. Ve tek seferde yalnızca bir tane tüketir.

Yöntemi, `WriteInt32ToBuffer` arabelleğe bir değer yazmaya yönelik olarak düşünülse de `DisplayBufferToConsole` yöntem değildir. Bunu yansıtmak için, türünde bir bağımsız değişkeni kabul etmiş olabilir <xref:System.ReadOnlyMemory%601> . Hakkında daha fazla bilgi için <xref:System.ReadOnlyMemory%601> bkz. [Kural #2: \<T> \<T> arabelleğin Salt-okunabilir olması gerekiyorsa Readonlyspan veya readonlymemory kullanın](#rule-2).

### <a name="ownerless-memoryt-instances"></a>"OwnerLeSs" bellek \<T> örnekleri

Kullanmadan bir örnek oluşturabilirsiniz <xref:System.Memory%601> <xref:System.Buffers.IMemoryOwner%601> . Bu durumda, arabelleğin sahipliği açık yerine örtük olur ve yalnızca tek sahip modeli desteklenir. Bunu şu şekilde yapabilirsiniz:

- <xref:System.Memory%601>Oluşturuculardan birini doğrudan çağırmak, `T[]` Aşağıdaki örnekte olduğu gibi bir ' a geçirerek.

- Bir örnek oluşturmak için [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) genişletme yöntemi çağrılıyor `ReadOnlyMemory<char>` .

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

İlk olarak örneği oluşturan yöntemi, <xref:System.Memory%601> arabelleğin örtük sahibidir. Aktarımı kolaylaştırmak için bir örnek bulunmadığından, sahiplik başka bir bileşene aktarılamaz <xref:System.Buffers.IMemoryOwner%601> . (Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiği da hayal edebilirsiniz.)

## <a name="usage-guidelines"></a>Kullanım yönergeleri

Bir bellek bloğunun sahibi olduğu, ancak bazıları aynı anda belirli bir bellek bloğunun üzerinde çalışabilen birden çok bileşene geçirilmesi amaçlanan için, hem hem de kullanımı için kılavuz oluşturulması önemlidir <xref:System.Memory%601> <xref:System.Span%601> .  Şu nedenle yönergeler gereklidir:

- Bir bileşenin sahibi serbest bırakıldıktan sonra bir bellek bloğunun başvurusunu bekletmek mümkündür.

- Bir bileşenin, başka bir bileşenin üzerinde çalıştığı aynı anda bir arabellekte çalışması, işlemin arabellekteki verileri bozuyor olması mümkündür.

- Yığın tarafından ayrılan doğası <xref:System.Span%601> performansı iyileştirir ve <xref:System.Span%601> tercih edilen türü bir bellek bloğunda çalıştırmak için, bu da <xref:System.Span%601> bazı önemli kısıtlamalara de neden olur. Ne zaman kullanacağınızı ve ne zaman kullanılacağını bilmemiz önemlidir <xref:System.Span%601> <xref:System.Memory%601> .

Aşağıdakiler ve ilgili türleri başarıyla kullanılarak önerimlerimiz aşağıda verilmiştir <xref:System.Memory%601> . İçin geçerli olan <xref:System.Memory%601> ve <xref:System.Span%601> Ayrıca <xref:System.ReadOnlyMemory%601> , <xref:System.ReadOnlySpan%601> açıkça aksi belirtilmedikçe ve için geçerli olan rehberlik.

**Kural #1: zaman uyumlu bir API Için mümkünse, \<T> bellek yerine span kullanın \<T> .**

<xref:System.Span%601>daha çok daha hızlıdır <xref:System.Memory%601> ve çok sayıda bitişik bellek arabelleğini temsil edebilir. <xref:System.Span%601>Ayrıca, daha iyi performans sunar <xref:System.Memory%601> . Son olarak, <xref:System.Memory%601.Span?displayProperty=nameWithType> özelliği bir örneği dönüştürmek için kullanabilirsiniz, ancak bu, noktadan <xref:System.Memory%601> <xref:System.Span%601> \<T> belleğe \<T> dönüştürme mümkün değildir. Bu nedenle, arayanların bir örneği varsa <xref:System.Memory%601> , yöntemlerinizi <xref:System.Span%601> yine de parametrelerle çağırabileceksiniz.

Türü yerine türünde bir parametre kullanılması <xref:System.Span%601> <xref:System.Memory%601> , doğru bir tüketen Yöntem uygulamasını yazmanıza de yardımcı olur. Metodun kira süresinin ötesinde (daha sonra bu konuda daha fazla) arabelleğe erişmeye girişdiğinizden emin olmak için otomatik olarak derleme zamanı denetimleri alacaksınız.

Bazen, <xref:System.Memory%601> <xref:System.Span%601> tam olarak zaman uyumlu olsanız bile parametre yerine bir parametre kullanmanız gerekecektir. Büyük olasılıkla bağlı olduğunuz bir API yalnızca <xref:System.Memory%601> bağımsız değişkenleri kabul eder. Bu sorun iyidir, ancak eşzamanlı olarak kullanılırken ilgili olan avantajları göz önünde bulundurun <xref:System.Memory%601> .

<a name="rule-2" />

**Kural #2: \<T> \<T> arabelleğin Salt okunabilir olması gerekiyorsa ReadOnlySpan veya ReadOnlyMemory kullanın.**

Önceki örneklerde `DisplayBufferToConsole` Yöntem yalnızca arabellekten okur; arabelleğin içeriğini değiştirmez. Yöntem imzası aşağıdaki şekilde değiştirilmelidir.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

Aslında, bu kuralı ve kuralı #1 birleştirirseniz, daha iyi bir şekilde yapabiliriz ve yöntem imzasını aşağıdaki gibi yeniden yazabilirsiniz:

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole`Yöntemi artık hemen her arabellek türü kodlamalardaki: `T[]` , [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış depolama ve benzeri ile çalışmaktadır. Hatta doğrudan ' a geçirebilirsiniz <xref:System.String> !

**Kural #3: yönteminizin belleği \<T> ve geri dönerse `void` , yönteminizin döndürdüğü bir bellek örneğini kullanmanız gerekir \<T> .**

Bu, daha önce bahsedilen "Kira" kavramıyla ilgilidir. Örnek üzerinde void döndüren bir yöntemin kirası, <xref:System.Memory%601> Yöntem girildiğinde başlar ve Yöntem çıktığında sonlanır. `Log`Bir döngüde konsolundan gelen giriş temelinde çağıran aşağıdaki örneği göz önünde bulundurun.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

`Log`Tamamen zaman uyumlu bir yöntem ise, belirli bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi olduğundan bu kod beklendiği gibi davranır.
Ancak bu uygulamayı içeren yerine Imagine `Log` .

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

Bu uygulamada, `Log` <xref:System.Memory%601> özgün Yöntem döndürülbaşladıktan sonra örneği hala arka planda kullanmaya çalıştığı için kiralamasını ihlal ediyor. Yöntem, bir `Main` arabelleği `Log` okumaya çalışırken, veri bozulmasına yol açabilir.

Bu sorunu çözmek için birkaç yol vardır:

- Yöntemi, `Log` <xref:System.Threading.Tasks.Task> `void` yönteminin aşağıdaki uygulanması olduğundan, yerine bir döndürebilir `Log` .

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- `Log`Bunun yerine, aşağıdaki gibi uygulanabilir:

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**Kural #4: yönteminiz bir belleği kabul eder \<T> ve bir görevi döndürürse, \<T> görev, bir Terminal durumuna geçtikten sonra bellek örneğini kullanmamalıdır.**

Bu yalnızca kural #3 zaman uyumsuz bir değişkendir. `Log`Önceki örnekteki yöntem bu kurala uymak için aşağıdaki gibi yazılabilir:

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Burada "Terminal durumu", görevin tamamlanmış, hatalı veya iptal edilmiş durumuna geçirdiğinin anlamına gelir. Diğer bir deyişle "Terminal durumu", "çalışmasına neden olan herhangi bir şey" anlamına gelir ve yürütme devam eder. "

Bu kılavuz,,, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601> veya benzer bir tür döndüren yöntemler için geçerlidir.

**Kural #5: Oluşturucu belleği \<T> bir parametre olarak kabul ediyorsa, oluşturulan nesnedeki örnek yöntemlerinin, bellek örneğinin tüketicileri olduğu varsayılır \<T> .**

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

Burada Oluşturucu bir `OddValueExtractor` `ReadOnlyMemory<int>` Oluşturucu parametresi olarak kabul eder, bu nedenle oluşturucunun kendisi `ReadOnlyMemory<int>` Örneğin bir tüketicisidir ve döndürülen değer içindeki tüm örnek yöntemleri de orijinal Örneğin tüketicisidir `ReadOnlyMemory<int>` . Bu, `TryReadNextOddValue` `ReadOnlyMemory<int>` Örneğin, örnek doğrudan yöntemine geçirilmese de örneği tükettiği anlamına gelir `TryReadNextOddValue` .

**Kural #6: türinizde ayarlanabilir bir bellek \<T> türü Özellik (veya eşdeğer bir örnek yöntemi) varsa, söz konusu nesnedeki örnek yöntemleri bellek örneğinin tüketicileri olduğu varsayılır \<T> .**

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

**Kural #7: bir ımemoryowner \<T> başvurunuz varsa, bu dosyanın bir noktasını atmaya veya sahipliğini aktarmaya (her ikisi değil) sahip olmanız gerekir.**

Bir <xref:System.Memory%601> örnek yönetilen veya yönetilmeyen bellek tarafından yönetilebileceği için, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> örnek üzerinde gerçekleştirilen iş tamamlandığında sahip çağrısı gerekir <xref:System.Memory%601> . Alternatif olarak, sahip, <xref:System.Buffers.IMemoryOwner%601> Örneğin sahipliğini farklı bir bileşene aktarabilir, bu noktada alma bileşeni <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> uygun zamanda (Bu daha sonra daha fazla) (daha fazla daha fazla) çağrı yapmaktan sorumlu olur.

Yöntemi çağıramaması, <xref:System.Buffers.MemoryPool%601.Dispose%2A> yönetilmeyen bellek sızıntılarına veya diğer performans düşüşüne neden olabilir.

Bu kural, gibi Fabrika yöntemlerini çağıran kod için de geçerlidir <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> . Çağıran, döndürülen sahibi olur <xref:System.Buffers.IMemoryOwner%601> ve tamamlandığında örneği elden atma sorumludur.

**Kural #8: API yüzeyinizde bir ımemoryowner \<T> parametresi varsa, bu örneğin sahipliğini kabul etmiş olursunuz.**

Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı amaçladığı sinyallere işaret eder. Bileşeniniz, kural #7 göre uygun elden çıkarılmasından sorumludur.

Örneğin sahipliğini farklı bir bileşene aktaran herhangi bir bileşen <xref:System.Buffers.IMemoryOwner%601> , yöntem çağrısının tamamlanmasından sonra bu örneği artık kullanmamalıdır.

> [!IMPORTANT]
> Oluşturucunuzu <xref:System.Buffers.IMemoryOwner%601> bir parametre olarak kabul ediyorsa, türünün uygulanması gerekir <xref:System.IDisposable> ve <xref:System.IDisposable.Dispose%2A> yöntemi çağırmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> .

**Kural #9: zaman uyumlu bir p/Invoke yöntemi sarmalandıysanız, API 'niz bir parametre olarak yayılmasını kabul etmelidir \<T> .**

Kural #1 göre <xref:System.Span%601> genellikle zaman uyumlu API 'ler için kullanılan doğru türdür. <xref:System.Span%601> [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) Aşağıdaki örnekte olduğu gibi, örnekleri anahtar sözcük aracılığıyla sabitleyebilirsiniz.

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

`pbData`Örneğin, giriş alanı boş ise, önceki örnekte null olabilir. İçe aktarılmış Yöntem, `pbData` 0 olsa bile null olmayan bir değer gerektiriyorsa, `cbData` yöntemi aşağıdaki gibi uygulanabilir:

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

**Kural #10: zaman uyumsuz bir p/Invoke yöntemi sarmalandıysanız, API 'niz \<T> bir parametre olarak belleği kabul etmelidir.**

[`fixed`](../../csharp/language-reference/keywords/fixed-statement.md)Anahtar sözcüğünü zaman uyumsuz işlemler arasında kullanamıyorsanız, <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> <xref:System.Memory%601> Örneğin ardışık bellek türünden bağımsız olarak örnekleri sabitlemek için yöntemini kullanırsınız. Aşağıdaki örnek, bu API 'nin zaman uyumsuz p/Invoke çağrısı gerçekleştirmek için nasıl kullanılacağını gösterir.

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
