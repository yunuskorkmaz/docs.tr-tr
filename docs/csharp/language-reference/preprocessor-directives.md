---
description: Koşullu derlemeyi, uyarıları, null yapılabilir analizini ve daha fazlasını denetleyen farklı C# önişlemci yönergelerini öğrenin
title: C# ön işlemci yönergeleri
ms.date: 03/17/2021
f1_keywords:
- cs.preprocessor
- '#nullable'
- '#if'
- '#else'
- '#elif'
- '#endif'
- '#define'
- '#undef'
- '#warning'
- '#error'
- '#line'
- '#region'
- '#endregion'
- '#pragma'
- '#pragma warning'
- '#pragma checksum'
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
- '#nullable directive [C#]'
- '#if directive [C#]'
- '#else directive [C#]'
- '#elif directive [C#]'
- '#endif directive [C#]'
- '#define directive [C#]'
- '#undef directive [C#]'
- '#warning directive [C#]'
- '#error directive [C#]'
- '#line directive [C#]'
- '#region directive [C#]'
- '#endregion directive [C#]'
- '#pragma directive [C#]'
- '#pragma warning [C#]'
- '#pragma checksum [C#]'
ms.openlocfilehash: 373952282a684da25414af9853e18b7bc4874108
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637676"
---
# <a name="c-preprocessor-directives"></a>C# ön işlemci yönergeleri

Derleyicinin ayrı bir önişlemcisi olmasa da, bu bölümde açıklanan yönergeler bir gibi işlenir. Koşullu derlemede yardımcı olması için bunları kullanabilirsiniz. C ve C++ yönergelerinden farklı olarak, bu yönergeleri makrolar oluşturmak için kullanamazsınız. Bir Önişlemci yönergesi, bir satırdaki tek yönerge olmalıdır.

## <a name="nullable-context"></a>Null yapılabilir bağlam

`#nullable`Önişlemci yönergesi *null yapılabilir ek açıklama bağlamını* ve *null yapılabilir uyarı bağlamını* ayarlar. Bu yönerge, null yapılabilir ek açıklamaların geçerli olup olmadığını ve null olabilme uyarılarının verilip verilmediğini denetler. Her bağlam *devre dışı* ya da *etkin*.

Her iki içerik de proje düzeyinde belirtilebilir (C# kaynak kodu dışında). `#nullable`Yönergesi ek açıklamanın ve uyarı bağlamlarını denetler ve proje düzeyi ayarlarından önceliklidir. Bir yönerge, başka bir yönerge tarafından geçersiz kılınana kadar veya kaynak dosyanın sonuna kadar denetlediği bağlamı ayarlar.

Yönergelerin etkisi aşağıdaki gibidir:

- `#nullable disable`: Nullable ek açıklama ve uyarı bağlamlarını *devre dışı* olarak ayarlar.
- `#nullable enable`: Null yapılabilir ek açıklama ve uyarı bağlamlarını *etkin* olarak ayarlar.
- `#nullable restore`: Proje ayarlarına Nullable ek açıklama ve uyarı bağlamlarını geri yükler.
- `#nullable disable annotations`: Nullable ek açıklama bağlamını *devre dışı* olarak ayarlar.
- `#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını *etkin* olarak ayarlar.
- `#nullable restore annotations`: Null yapılabilir ek açıklama bağlamını proje ayarlarına geri yükler.
- `#nullable disable warnings`: Nullable uyarı bağlamını *devre dışı* olarak ayarlar.
- `#nullable enable warnings`: Null yapılabilir uyarı bağlamını *etkin* olarak ayarlar.
- `#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.

## <a name="conditional-compilation"></a>Koşullu derleme

Koşullu derlemeyi denetlemek için dört Önişlemci yönergesi kullanırsınız:

- `#if`: Kodun yalnızca belirtilen sembol tanımlanmışsa derlenmesi durumunda, koşullu bir derleme açılır.
- `#elif`: Önceki koşullu derlemeyi kapatır ve belirtilen simgenin tanımlanması halinde yeni bir koşullu derleme açar.
- `#else`: Önceki koşullu derlemeyi kapatır ve önceki belirtilen sembol tanımlanmamışsa yeni bir koşullu derleme açar.
- `#endif`: Önceki koşullu derlemeyi kapatır.

C# derleyicisi bir yönerge bulduğunda ve `#if` sonunda bir `#endif` yönerge ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler. C ve C++ ' dan farklı olarak, bir simgeye sayısal değer atayamazsınız. `#if`C# ' deki ifade, Boolean ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar. Örnek:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Değerlerini veya test etmek için İşleçleri [ `==` (eşitlik)](operators/equality-operators.md#equality-operator-) ve [ `!=` (eşitsizlik)](operators/equality-operators.md#inequality-operator-) kullanabilirsiniz [`bool`](builtin-types/bool.md) `true` `false` . `true` simgenin tanımlandığı anlamına gelir. İfade, `#if DEBUG` ile aynı anlama sahiptir `#if (DEBUG == true)` . Birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için [ `&&` (ve)](operators/boolean-logical-operators.md#conditional-logical-and-operator-), [ `||` (veya)](operators/boolean-logical-operators.md#conditional-logical-or-operator-)ve [ `!` (Not](operators/boolean-logical-operators.md#logical-negation-operator-) ) işleçlerini kullanabilirsiniz. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.

`#if`,,, `#else` `#elif` `#endif` `#define` ve `#undef` yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar. Koşullu derleme, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.

Yönergeyle başlayan koşullu bir yönerge `#if` , açıkça bir yönergeyle sonlandırılmalıdır `#endif` . `#define` bir sembol tanımlamanızı sağlar. Sembol, yönergeye geçirilen ifade olarak kullanıldığında ifadesi olarak `#if` değerlendirilir `true` . Ayrıca, [**Definesabitleri**](compiler-options/language.md#defineconstants) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. İle bir simge tanımlayabilirsiniz `#undef` . İle oluşturulan sembolün kapsamı, `#define` tanımlandığı dosyadır. **Definesabitleri** veya ile tanımladığınız bir sembol `#define` aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilirler.

`#elif` bileşik bir koşullu yönerge oluşturmanıza olanak sağlar. `#elif`İfade, `#if` ne önce ne de önceki, isteğe bağlı bir `#elif` yönerge ifadesi olarak değerlendiriliyorsa değerlendirilir `true` . Bir `#elif` ifade olarak değerlendirilirse `true` , derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir. Örnek:

```csharp
#define VC7
//...
#if debug
    Console.WriteLine("Debug build");
#elif VC7
    Console.WriteLine("Visual Studio 7");
#endif
```

`#else` , önceki `#if` veya (isteğe bağlı) `#elif` yönergelerinden hiçbiri olarak değerlendiriyorsa `true` , derleyici, ve arasındaki tüm kodları değerlendirmek için bileşik `#else` bir koşullu yönerge oluşturmanıza olanak sağlar `#endif` . `#endif`(#endif) sonraki ön işlemci yönergesi olmalıdır `#else` .

`#endif` yönergeyle başlayan bir koşul yönergesinin sonunu belirtir `#if` .

Yapı sistemi, SDK stili projelerde farklı [hedef çerçeveleri](../../standard/frameworks.md) temsil eden önceden tanımlanmış ön işlemci sembolleri de farkındadır. Birden fazla .NET sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Geleneksel, SDK olmayan projeler için, Visual Studio 'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin Özellikler sayfaları aracılığıyla el ile yapılandırmanız gerekir.

Diğer önceden tanımlanmış semboller, `DEBUG` ve `TRACE` sabitlerini içerir. Kullanarak proje için ayarlanan değerleri geçersiz kılabilirsiniz `#define` . Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.

Aşağıdaki örnek, `MYTEST` bir dosyanın üzerinde bir sembol tanımlanacağını ve sonra ve simgelerinin değerlerini test etmek için size gösterir `MYTEST` `DEBUG` . Bu örneğin çıktısı, projeyi **hata ayıklama** veya **Sürüm** yapılandırma modunda derdığınıza bağlıdır.

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

Aşağıdaki örnekte, mümkünse daha yeni API 'Leri kullanabilmeniz için farklı hedef çerçeveler için nasıl test yapılacağı gösterilmektedir:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="defining-symbols"></a>Sembolleri tanımlama

Koşullu derleme için sembolleri tanımlamak veya tanımlamak üzere aşağıdaki iki Önişlemci yönergesi kullanın:

- `#define`: Bir sembol tanımlayın.
- `#undef`: bir sembol tanımlayın.

`#define`Bir sembol tanımlamak için kullanırsınız. Simgesini yönergeye geçirilen ifade olarak kullandığınızda `#if` , `true` Aşağıdaki örnekte gösterildiği gibi ifade olarak değerlendirilir.

 ```csharp
 #define VERBOSE

#if VERBOSE
    Console.WriteLine("Verbose output version");
#endif

 ```

> [!NOTE]
> `#define`Yönerge, genellikle C ve C++ ' da yapıldığı gibi sabit değerleri bildirmek için kullanılamaz. C# ' deki sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır. Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.

Simgeler, derleme koşullarını belirtmek için kullanılabilir. Ya da simgesiyle test edebilirsiniz `#if` `#elif` . <xref:System.Diagnostics.ConditionalAttribute>Koşullu derleme gerçekleştirmek için öğesini de kullanabilirsiniz. Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız. `#define`Ayrıca Önişlemci yönergeleri olmayan herhangi bir yönergeyi kullanmadan önce yönerge dosyada görünmelidir. Ayrıca, [**Definesabitleri**](compiler-options/language.md#defineconstants) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. İle bir simge tanımlayabilirsiniz `#undef` .

## <a name="defining-regions"></a>Bölgeleri tanımlama

Aşağıdaki iki önişlemci yönergelerini kullanarak bir anahatta daraltılabilen kod bölgelerini tanımlayabilirsiniz:

- `#region`: Bir bölge başlatın.
- `#endregion`: Bölge sonu

`#region` kod düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bir kısmına odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi yararlı olabilir. Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:

```csharp
#region MyClass definition
public class MyClass
{
    static void Main()
    {
    }
}
#endregion
```

Bir `#region` bloğun bir yönergeyle sonlandırılması gerekir `#endregion` . Bir `#region` blok bir blok ile çakışamaz `#if` . Ancak bir blok bir `#region` blokta iç içe olabilir ve bir blok `#if` bir blok `#if` içinde iç içe olabilir `#region` .

## <a name="error-and-warning-information"></a>Hata ve uyarı bilgileri

Derleyicinin Kullanıcı tanımlı derleyici hataları ve uyarıları oluşturmasını ve aşağıdaki yönergeleri kullanarak hat bilgilerini kontrol etmek için talimat alırsınız:

- `#error`: Belirtilen iletiyle derleyici hatası oluşturma.
- `#warning`: Belirli bir iletiyle bir derleyici uyarısı oluşturun.
- `#line`: Derleyici iletileriyle yazdırılan satır numarasını değiştirin.

`#error` kodunuzda belirli bir konumdan [CS1029](compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar. Örnek:

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> Derleyici `#error version` özel bir şekilde davranır ve bir derleyici hatası, CS8304, kullanılan derleyici ve dil sürümlerini içeren bir ileti ile rapor eder.

`#warning` kodunuzda belirli bir konumdan bir [CS1030](../misc/cs1030.md) düzeyinde bir derleyici uyarısı oluşturmanıza olanak sağlar. Örnek:

```csharp
#warning Deprecated code in this method.
```

`#line` Derleyicinin satır numaralandırmasını ve (isteğe bağlı olarak) hata ve uyarı için dosya adı çıktısını değiştirmenize izin verir.

Aşağıdaki örnek, satır numaralarıyla ilişkili iki uyarıyı nasıl bildirekullanacağınızı gösterir. `#line 200`Yönerge, sonraki satırın numarasını 200 (varsayılan değer #6) olarak zorlar ve sonraki `#line` yönergeye kadar dosya adı "özel" olarak raporlanır. `#line default`Yönerge, önceki yönerge tarafından yeniden numaralandırılmış satırları sayan varsayılan numaralandırmayla satır numaralandırmayı döndürür.

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

Derleme aşağıdaki çıktıyı üretir:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

`#line`Yönergesi, yapı işlemindeki otomatik, ara bir adımda kullanılabilir. Örneğin, satır orijinal kaynak kodu dosyasından kaldırılmışsa, ancak derleyicinin dosyadaki özgün satır numaralandırmasını temel alarak çıkış oluşturmasını istiyorsanız, satırları kaldırabilir ve ardından özgün satır numaralandırmasının benzetimini yapabilirsiniz `#line` .

`#line hidden`Yönerge, hata ayıklayıcıdaki ardışık satırları gizler, örneğin, Geliştirici kod içinde, bir `#line hidden` ve sonraki `#line` yönerge (başka bir yönerge olmadığı varsayılarak) arasında herhangi bir satır `#line hidden` üzerinden ele alınacaktır. Bu seçenek, ASP.NET 'in Kullanıcı tanımlı ve makine tarafından oluşturulan kodla ayırt edilmesine imkan tanımak için de kullanılabilir. ASP.NET bu özelliğin birincil tüketicisi olsa da, bu, büyük olasılıkla daha fazla kaynak oluşturanlar tarafından kullanılabilir.

`#line hidden`Yönerge, hata raporlamadaki dosya adlarını veya satır numaralarını etkilemez. Diğer bir deyişle, derleyici gizli bir blokta bir hata bulursa, derleyici geçerli dosya adı ve hatanın satır numarasını bildirir.

`#line filename`Yönergesi, derleyici çıkışında görünmesini istediğiniz dosya adını belirtir. Varsayılan olarak, kaynak kodu dosyasının gerçek adı kullanılır. Dosya adı çift tırnak işareti ("") içinde olmalı ve önünde bir satır numarası gelmelidir.

Aşağıdaki örnek, hata ayıklayıcının koddaki gizli satırları nasıl yoksaydığı gösterilmektedir. Örneği çalıştırdığınızda üç satırlık metin görüntülenir. Ancak, örnekte gösterildiği gibi bir kesme noktası ayarladığınızda ve kodun içinde ilerlemek için F10 'e vuruladığınızda, hata ayıklayıcı gizli çizgiyi yoksayar. Gizli satırda bir kesme noktası ayarlamış olsanız bile, hata ayıklayıcı yine de yok sayılacak.

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="pragmas"></a>Pragmalar

`#pragma` Derleyicinin göründüğü dosyanın derlenmesi için özel yönergeler sağlar. Yönergeler derleyici tarafından desteklenmelidir. Diğer bir deyişle, `#pragma` özel ön işleme yönergeleri oluşturmak için kullanamazsınız.
  
- [`#pragma warning`](#pragma-warning): Uyarıları etkinleştirin veya devre dışı bırakın.
- [`#pragma checksum`](#pragma-checksum): Sağlama toplamı oluştur.

```csharp
#pragma pragma-name pragma-arguments
```

Burada `pragma-name` tanınan bir pragma 'ın adıdır ve `pragma-arguments` pragmaya özgü bağımsız değişkenlerdir.

### <a name="pragma-warning"></a>#pragma uyarısı

`#pragma warning` Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

Burada `warning-list` , uyarı numaralarının virgülle ayrılmış bir listesidir. "CS" ön eki isteğe bağlıdır. Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.

> [!NOTE]
> Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.

`disable`Kaynak dosyanın bir sonraki satırından başlayarak etkisini alır. Uyarı, izleyen satıra geri yüklenir `restore` . `restore`Dosyada yoksa, uyarılar aynı derlemede bulunan sonraki dosyaların ilk satırında varsayılan durumlarına geri yüklenir.

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

### <a name="pragma-checksum"></a>#pragma sağlama toplamı

ASP.NET sayfalarında hata ayıklamaya yardımcı olmak için kaynak dosyaları için sağlama toplamı üretir.

```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"
```

, `"filename"` Değişiklik veya güncelleştirme için izlemeyi gerektiren dosyanın adı, `"{guid}"` karma algoritmanın genel benzersiz TANıMLAYıCıSıDıR (GUID) ve `"checksum_bytes"` sağlama toplamı baytlarını temsil eden onaltılık basamakların dizesidir. Çift sayıda onaltılık basamak olmalıdır. Tek sayıda basamak derleme zamanı uyarısına neden olur ve yönerge yok sayılır.

Visual Studio hata ayıklayıcı, her zaman doğru kaynağı bulmasını sağlamak için bir sağlama toplamı kullanır. Derleyici, kaynak dosya için sağlama toplamını hesaplar ve sonra çıktıyı program veritabanı (PDB) dosyasına yayar. Hata ayıklayıcı daha sonra kaynak dosya için hesapladığı sağlama toplamıyla karşılaştırmak için PDB 'yi kullanır.

Hesaplanan sağlama toplamı,. aspx dosyası yerine oluşturulan kaynak dosya için olduğundan, bu çözüm ASP.NET projelerinde çalışmıyor. Bu sorunu gidermek için `#pragma checksum` ASP.NET sayfaları için sağlama toplamı desteği sağlar.

Visual C# içinde bir ASP.NET projesi oluşturduğunuzda oluşturulan kaynak dosya, kaynağın oluşturulduğu. aspx dosyası için bir sağlama toplamı içerir. Derleyici daha sonra bu bilgileri PDB dosyasına yazar.

Derleyici `#pragma checksum` dosyada bir yönerge bulamazsa, sağlama toplamını hesaplar ve DEĞERI pdb dosyasına yazar.

```csharp
class TestClass
{
    static int Main()
    {
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum
    }
}
```
