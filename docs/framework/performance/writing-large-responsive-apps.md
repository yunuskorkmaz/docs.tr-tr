---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8c73f1a4373583530d5afde113c5c4ec049bcea4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195898"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
Bu makalede, büyük bir .NET Framework uygulamaları veya işlem büyük miktarda verileri dosyalar veya veritabanları gibi uygulama performansını iyileştirmek için ipuçları sağlar. C# ve Visual Basic derleyicileri, yönetilen kodda yeniden yazma bu ipuçlarını gelir ve bu makale, çeşitli gerçek örnekler C# derleyicisi içerir. 
  
 .NET Framework uygulamaları oluşturmak için son derece üretken. Uygulama oluşturma, güçlü ve güvenli diller ve kitaplıkların zengin bir koleksiyonu yüksek oranda bankanın olun. Ancak, sorumluluk harika üretkenlik ile birlikte gelir. .NET Framework'ün tüm gücünü kullanın ancak gerektiğinde kodunuzun performansını ayarlamak hazırlanması gerekir. 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Yeni derleyici performans uygulamanıza neden geçerlidir  
 .NET derleyici Platformu ("Roslyn") ekibi C# yeniden yazıldı ve Visual Basic derleyicileri, yönetilen kodu modelleme ve kodunu analiz etme, derleme araçları ve çok daha zengin, kod duyarlı deneyimler Visual Studio'da etkinleştirme için yeni API'ler sağlar. Yeniden yazma System.codeDom ve Visual Studio oluşturma yeni derleyiciler üzerinde deneyimlerin büyük herhangi bir .NET Framework uygulama veya çok miktarda veri işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörüleri göstermiştir. Görüş ve örnekler C# derleyicisi yararlanmak için derleyiciler hakkında bilmeniz gerekmez. 
  
 Visual Studio tanımlayıcıları ve anahtar sözcükler, söz dizimi tamamlanma listeleri, renklendirme dalgalı çizgiler gibi hataları, parametre ipuçları, kod sorunları ve kod eylemleri için kullanıcıların hayran, tüm IntelliSense özelliklerini oluşturmak için derleyicinin API'leri kullanır. Visual Studio, geliştiricilerin yazarak ve kodlarını değiştirme ve derleyici geliştiriciler Düzenle kod sürekli modeller sırada Visual Studio yanıt kalması gereken bu Yardım sağlar. 
  
 Son kullanıcılarınızın uygulamanızla etkileşim kurduğunuzda, bunlar esnek olmasını bekler. Yazarak ya da komut işleme hiçbir zaman engellenmelidir. Yardım hızla açılır veya kullanıcı yazmaya devam ederse vazgeçmeniz gerekir. Uygulamanızı ağır düşünüyorsanız uygulamayı uzun hesaplamalar ile UI iş parçacığı engelleme kaçınmanız gerekir. 
  
 Roslyn derleyicileri hakkında daha fazla bilgi için bkz: [.NET derleyici Platformu SDK](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Bulguları  
 Performans ayarlama, bu bilgileri göz önünde bulundurun ve hızlı yanıt veren .NET Framework uygulamaları oluşturma. 
  
### <a name="fact-1-dont-prematurely-optimize"></a>Olgu 1: beklenenden önce iyileştirme  
 Olmasını ihtiyaç duyduğundan daha karmaşık kod yazma, hata ayıklama ve maliyetleri polishing bakım doğurur. Sezgisel bir kavrayın kodlama sorunlarını çözmek ve daha verimli kod yazma, programcılar vardır. Ancak, bunlar bazen erken kodlarını iyileştirin. Örneğin, bir Basit dizi yeterli veya değerleri yalnızca yeniden hesaplanıyor yerine bellekte sızıntı karmaşık önbelleğe kullandığınızda bir karma tablo kullanın. Bir deneyim Programcı olmasanız bile için performans testi ve sorunları bulmak, kodunuzu analiz gerekir. 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Olgu 2:, ölçüm yaptığınız değil ise, tahmin  
 Profilleri ve ölçümler yer yok. Profilleri, CPU tam yüklü olmadığı ya da disk g/ç üzerinde engellendi gösterir. Profilleri bahsedin, ne tür ve ne kadar bellek ayırma ve mi CPU harcama çok zaman içinde [çöp toplama](../../../docs/standard/garbage-collection/index.md) (GC). 
  
 Uygulamanızda performans hedeflerini önemli müşteri deneyimleri veya senaryoları ayarlayın ve performansını ölçmek için testleri yazmak gerekir. Başarısız olan testler bilimsel yöntemi uygulayarak araştırın: profillerini kullanmak için size rehberlik, ne sorun olabilir, hipotezler varsayımınızın deneme ile test ve kod değişikliği. Performans gerilemeleri neden değişiklikleri yalıtabilirsiniz için normal test ile zaman içinde temel performans ölçümleri kurun. Sıkı bir şekilde performans iş yaklaşan tarafından zaman ihtiyacınız olmayan kod güncelleştirmeleriyle önlenir. 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Olgu 3: İyi Araçlar fark olun.  
 Hızlı bir şekilde büyük performans sorunları (CPU, bellek veya disk) ve bu sorunları neden kodu bulun Yardım ayrıntılarına girmek iyi araçları sağlar. Microsoft gelen çeşitli performans araçları gibi [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone analiz aracı](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567). 
  
 PerfView disk g/ç gibi ayrıntılı sorunlara odaklanmak, GC olayları ve bellek yardımcı olan ücretsiz ve şaşırtıcı derecede güçlü bir araçtır. Performansla ilgili yakalayabilirsiniz [olay izleme için Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) olayları ve görünümü, uygulama başına bir kolayca, her işlem, yığın başına ve başına iş parçacığı bilgileri. PerfView uygulamanızı ayırır, bellek ve hangi işlevleri veya çağrı yığınlarını ne kadar bellek ayırmaları için katkıda bulunan ne kadar ve ne tür gösterir. Zengin Yardım konuları, tanıtımlar ve videolar aracıyla dahil Ayrıntılar için bkz. (gibi [PerfView öğreticiler](https://channel9.msdn.com/Series/PerfView-Tutorial) Channel 9). 
  
### <a name="fact-4-its-all-about-allocations"></a>Olgu 4: Tüm ayırmaları hakkında olduğu  
 Bu bir yanıt oluşturmak düşündüğünüzden .NET Framework uygulaması Kabarcık sıralama yerine Hızlı sıralama kullanma gibi tüm algoritmalar hakkında ancak bu durum geçerli değildir. Özellikle uygulama çok büyükse veya büyük miktarlarda veri işler hızlı yanıt veren bir uygulama oluşturmanın en büyük faktör, bellek ayırma olduğu. 
  
 Neredeyse tüm esnek IDE oluşturmak için iş API'leri yeni derleyici ile deneyimleri ayırmaları önleme ve önbelleğe alma stratejilerine yönetme dahil. İzleme PerfView yeni C# ve Visual Basic derleyicileri performansını nadiren CPU bağımlı olduğunu gösterir. Oluşturulan kod yayan veya derleyiciler meta verileri okuma binlerce veya milyonlarca satır kod, yüzlerce okurken g/ç olabilir. UI iş parçacığı gecikmeleri neredeyse tüm çöp toplama nedeniyle ' dir. .NET Framework GC yüksek performans için ayarlanmış ve aynı anda uygulama kodu yürütürken işini çoğunu yapar. Ancak, tek bir ayırma pahalı bir tetikleyebilirsiniz [gen2](../../../docs/standard/garbage-collection/fundamentals.md) tüm iş parçacıklarını durdurma koleksiyonu. 
  
## <a name="common-allocations-and-examples"></a>Ortak ayırmaları ve örnekler  
 Bu bölümdeki örnek ifadeler küçük görünen ayırmaları gizli. Ancak, çok sayıda uygulama, yeterli sayıda deyimleri yürütür, megabayt, hatta gigabayt ayırmaların yüzlerce nedenlerini olabilir. Gigabayt cinsinden bellek tahsis düzenleyicide Geliştirici yazarak simulated ve performans takım senaryoları yazarken odaklanmak için yönetilen Örneğin, bir dakikalık sınar. 
  
### <a name="boxing"></a>Kutulama  
 [Kutulama](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) normal olarak değer türleri yığında live veya veri yapılarını nesneyi sarmalanır gerçekleşir. Diğer bir deyişle, verileri tutmak için bir nesne ayrılamadı ve ardından nesneye bir işaretçi döndürür. .NET Framework, bazen bir yöntem veya bir depolama konumu türünün imza nedeniyle değerleri kutular. Bir değer türü bir nesne nedenleri bellek ayırmayı kaydırma. Birçok kutulama işlemleri, megabayt veya gigabayt uygulamanızı daha fazla GC'ler sebep uygulamanıza ayırmaların katkıda bulunabilir. .NET Framework ve dil derleyicileri kutulama mümkün olduğunda kaçının, ancak bazen az beklediğiniz olur. 
  
 Perfview'de Aç kutulama görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığında bakın (unutmayın, PerfView tüm işlemlerde raporları). Türleri gibi görürseniz <xref:System.Int32?displayProperty=nameWithType> ve <xref:System.Char?displayProperty=nameWithType> ayırmaları altında değer türleri kutulama. Bu türlerinden birini seçerek Kutulu işlevler ve yığınlarını gösterir. 
  
 **Örnek 1: dize yöntemlerini ve değer tür bağımsız değişkenleri**  
  
 Bu örnek kod, büyük olasılıkla gereksiz ve aşırı kutulama gösterilmektedir:  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 Bu kod günlüğü işlevini sağlar. böylece, bir uygulamayı çağırabilir `Log` sık, milyonlarca kez belki de işlev. Sorunu olan çağrı `string.Format` çözümler <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yükleme. 
  
 Bu aşırı yükü .NET Framework kutusuna gerektirir `int` bu yöntem çağrısına geçirilecek nesnelere değerleri. Kısmi bir düzeltme çağırmaktır `id.ToString()` ve `size.ToString()` ve (hangi nesneleri) tüm dizeleri geçirmek `string.Format` çağırın. Çağırma `ToString()` ayırma içinde yine de gerçekleşir ancak bu bir dize tahsis `string.Format`. 
  
 Bu temel düşünebilirsiniz çağrısı `string.Format` yalnızca dize birleştirme olduğundan, bunun yerine bu kodu yazabilirsiniz:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ancak, kodun o satırına için derleme nedeni kutulama ayırma tanıtır <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. .NET Framework karakter çağrılacak sabiti kutusunda gerekir `Concat`  
  
 **Örneğin 1 Düzelt**  
  
 Tüm düzeltme, basit bir işlemdir. Yalnızca karakteri bir dize sabit değeri, değişmez değer dizeleri nesneler olduğundan, hiçbir kutulama doğurur değiştirin:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Örnek 2: sabit listesi kutulama**  
  
 Bu örnekte, sık kullanılması nedeniyle yeni C# ve Visual Basic derleyicileri, bir ayırma Numaralandırma türleri, özellikle sözlük arama işlemleri sektörünüz sorumluydu. 
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 Bu sorun, çok hafif olmasıdır. PerfView olarak rapor <xref:System.Enum.GetHashCode> yöntemi temel alınan numaralandırma türü, Uygulama nedenlerinden gösterimini kutular çünkü kutulama. PerfView içinde yakından bakarsanız, her çağrı için iki kutulama ayırmaları görebilirsiniz <xref:System.Enum.GetHashCode>. Derleyici bir ekler ve diğer .NET Framework ekler. 
  
 **Örnek 2 düzeltme**  
  
 Atama temel alınan gösterimi çağırmadan önce tarafından her iki ayırma kolayca kaçınabilirsiniz <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Numaralandırma türleri kutulama, başka bir ortak kaynak <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemi. Geçirilen bağımsız değişken <xref:System.Enum.HasFlag%28System.Enum%29> Kutulu gerekir. Çoğu durumda, çağrıları değiştirerek <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bir bit düzeyinde ile daha basit ve ayırma testtir. 
  
 İlk performans gerçeği göz önünde bulundurun (diğer bir deyişle, erken iyileştirme) ve bu şekilde tüm kodunuzu yeniden başlatma. Bu kutulama maliyetlerini unutmayın, ancak yalnızca uygulama profili oluşturma ve etkin noktaları bulma sonra kodunuzu değiştirin. 
  
### <a name="strings"></a>Dizeler  
 Dize işlemeleri ayırmalar için büyük culprits bazıları, ve bunlar genellikle PerfView ilk beş ayırmalar şeklinde gösterilir. Program serileştirme, JSON ve REST API'leri için dizeleri kullanın. Numaralandırma türleri kullanamadığınızda sistemleriyle birlikte çalışma için dizeleri programlı sabitleri kullanabilirsiniz. Dizeleri yüksek oranda performansı etkilediğinden, profil oluşturma gösterilmektedir, çağrılar için konum <xref:System.String> gibi yöntemler <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>ve benzeri. Kullanarak <xref:System.Text.StringBuilder> bir dize oluşturma çok sayıda parça yardımcı olur, ancak bile ayırma maliyetini önlemek için <xref:System.Text.StringBuilder> nesne yönetmeniz gereken bir performans sorunu haline. 
  
 **Örnek 3: dize işlemleri**  
  
 C# derleyicisi, metnin bir biçimlendirilmiş XML belge açıklamasının yazar bu kodu sahipti:  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 Bu kod dize düzenlemesi çok mu olduğunu görebilirsiniz. Kod satırları ayrı dizelere içerecek şekilde kırpmanıza denetlemek için beyaz boşluk, bölme için kitaplık yöntemleri kullanır. olmadığını bağımsız değişken `text` bir XML belge açıklaması ve satırlarından alt dizeleri ayıklama. 
  
 İçinde ilk satırda `WriteFormattedDocComment`, `text.Split` çağrı her çağrıldığında bu yeni üç öğeli bir dizi bağımsız değişken olarak ayırır. Derleyici, her zaman bu dizi ayırmak için kod yaymak vardır. Derleyici, bilmez çünkü <xref:System.String.Split%2A> yere burada dizisi değiştirilmesine sonraki çağrılar etkileyecek diğer kod tarafından dizi depolar `WriteFormattedDocComment`. Çağrı <xref:System.String.Split%2A> ayrıca her satır için bir dize ayırır `text` ve bu işlemi gerçekleştirmek için diğer bellek ayırır. 
  
 `WriteFormattedDocComment` üç çağrı sahip <xref:System.String.TrimStart%2A> yöntemi. İş ve ayırmaları yinelenen iç Döngülerde ikisidir. Önemli olan konuya daha da kötüsü, arama yapmak için <xref:System.String.TrimStart%2A> yöntemi bağımsız değişken içermeyen boş bir dizi ayırır (için `params` parametresi) dize sonucu yanı sıra. 
  
 Son olarak, bir çağrı yoktur <xref:System.String.Substring%2A> yöntemi genellikle yeni bir dize ayırır. 
  
 **Örneğin 3 düzeltme**  
  
 Önceki örneklerde, bu ayırma küçük düzenlemelerle düzeltemiyor. Geri adım, sorun ve farklı yaklaşım gerekir. Örneğin, olduğunu fark edeceksiniz bağımsız değişkeni `WriteFormattedDocComment()` kod birçok kısmi dizeler ayırma yerine daha fazla dizin oluşturma yapabilir, yöntemi gerektiren tüm bilgilere sahip bir dizedir. 
  
 Derleyicinin performans takım bu ayırmaları aşağıdakine benzer bir kod ile tackled:  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc... 
```  
  
 Ürününün ilk sürümünü `WriteFormattedDocComment()` dizisi ve alt dizelerin kırpılmış bir alt dizesi boş birlikte ayrılan `params` dizisi. Ayrıca kullanıma "/ / / için". Düzeltilen kod yalnızca dizin kullanır ve hiçbir şey ayırır. Bu dize başlayıp başlamadığını "/ / /" ile görmek için boşluk değildir ve ardından karakter denetler ilk karakteri bulur. Yeni kod `IndexOfFirstNonWhiteSpaceChar` yerine <xref:System.String.TrimStart%2A> boşluk olmayan karakter oluştuğu (sonra belirtilen başlangıç dizini) ilk dizin dönün. Düzeltmenin tam değil, ancak benzer düzeltmeleri için eksiksiz bir çözüm uygulamak nasıl görebilirsiniz. Bu yaklaşım kod genelindeki uygulayarak, tüm ayırmaları kaldırabilirsiniz `WriteFormattedDocComment()`. 
  
 **Örnek 4: StringBuilder**  
  
 Bu örnekte bir <xref:System.Text.StringBuilder> nesne. Tam tür adı genel türler için aşağıdaki işlevi oluşturur:  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 Odağı oluşturan yeni bir satırda olduğu <xref:System.Text.StringBuilder> örneği. Kod için bir ayırma neden `sb.ToString()` ve içinde iç Tahsisatları <xref:System.Text.StringBuilder> uygulaması, ancak denetimi bu ayırmaları dize sonucu istiyorsanız. 
  
 **Örneğin, 4 Düzelt**  
  
 Düzeltmek için `StringBuilder` nesne ayırma, nesne önbelleğe alma. Atılan tek bir örnek bile önbelleğe alma performansını önemli ölçüde artırabilir. Bu işlevin yeni uygulama, yeni ilk ve son satırlar dışında tüm kod atlama.  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Yeni bazı önemli bölümleri `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` İşlevler:  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 Yeni derleyiciler iş parçacığı kullandığından, bu uygulamaları bir iş parçacığı statik alan kullanır (<xref:System.ThreadStaticAttribute> özniteliği) önbelleğe <xref:System.Text.StringBuilder>, ve büyük olasılıkla bırakmayı `ThreadStatic` bildirimi. İş parçacığı statik alanı bu kodu yürüten her bir iş parçacığı için benzersiz bir değer tutar. 
  
 `AcquireBuilder()` önbelleğe alınan döndürür <xref:System.Text.StringBuilder> varsa, alan veya önbellek null olarak ayarlamak ve temizlemeden sonra örnek. Aksi takdirde, `AcquireBuilder()` yeni bir örneğini oluşturur ve alan veya önbellek kümesi null olarak bırakarak döndürür. 
  
 Bitirdiğinizde ile <xref:System.Text.StringBuilder> , çağırmanızı `GetStringAndReleaseBuilder()` dize sonucu elde etmek için Kaydet <xref:System.Text.StringBuilder> örnek alanı veya önbellek ve sonucu döndürür. Bu kodu tekrar girin ve birden çok oluşturmak için yürütme için mümkündür <xref:System.Text.StringBuilder> (, nadiren gerçekleşir ancak) nesneleri. Yalnızca en son yayımlanan kod kaydeder <xref:System.Text.StringBuilder> daha sonra kullanmak için örneği. Bu basit bir önbelleğe alma stratejisi, yeni derleyiciler ayırmalarda önemli ölçüde azaldığından. .NET Framework ve MSBuild ("MSBuild") bölümleri, performansı artırmak için benzer bir teknik kullanın. 
  
 Bir boyut sınırına sahip olduğundan bu basit bir önbelleğe alma stratejisi iyi önbellek tasarım uyar. Ancak, daha fazla bakım maliyetlerini diğer bir deyişle orijinal, artık daha fazla kod yoktur. Yalnızca bir performans sorunu buldunuz ve PerfView, gösterilen önbelleğe alma stratejisi benimseyin <xref:System.Text.StringBuilder> ayırmaları olan önemli bir katkıda bulunan. 
  
### <a name="linq-and-lambdas"></a>LINQ ve lambda ifadeleri  
Dil ile tümleşik sorgu (LINQ), lambda ifadeleri ile birlikte bir üretkenlik özellik örneğidir. Ancak, kullanımı zaman içerisinde performansı üzerinde önemli bir etkisi olabilir ve kodunuzu yeniden yazmak zorunda bulabilirsiniz.
  
 **5. örnek: Lambda ifadeleri, liste\<T > ve IEnumerable\<T >**  
  
 Bu örnekte [LINQ ve işlev stili kod](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) adı dizesi verilmiş bir sembol derleyicinin modelinde bulmak için:  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 Yeni derleyici ve çağrı bunu temel IDE deneyimleri `FindMatchingSymbol()` tek satır kod bu işlevin, birkaç gizli ayırmaları çok sık ve var olan. Bu ayırmalar incelemek için ilk işlevin tek satır kod iki çizgiye bölün:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 İlk satırda [lambda ifadesi](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [üzerinden kapatır](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) yerel değişken `name`. Bunun için bir nesne ayırma ek olarak anlamı [temsilci](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` tutar, kodu değerini yakalayan bir ortam için bir statik sınıf ayırır `name`. Derleyici, aşağıdaki gibi bir kod oluşturur:  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 İki `new` ayırmalar (bir ortam sınıfı için) ve bir temsilci için açık şimdi. 
  
 Artık çağrısına bakın `FirstOrDefault`. Bu genişletme yöntemini <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türü bir ayırma çok doğurur. Çünkü `FirstOrDefault` götüren bir <xref:System.Collections.Generic.IEnumerable%601> nesne, ilk bağımsız değişkeni olarak (hakkında ayrıntılı bilgi için biraz Basitleştirilmiş) aşağıdaki koda çağrı genişletebilirsiniz:  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ... 
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 `symbols` Değişken türüne sahip <xref:System.Collections.Generic.List%601>. <xref:System.Collections.Generic.List%601> Koleksiyon türü uygulayan <xref:System.Collections.Generic.IEnumerable%601> ve zekice bir numaralandırıcı tanımlar (<xref:System.Collections.Generic.IEnumerator%601> arabirimi), <xref:System.Collections.Generic.List%601> ile uygulayan bir `struct`. Bir sınıf yerine bir yapı kullanarak hangi sırayla, çöp toplama performansı etkileyebilir herhangi bir yığın ayırma genellikle kaçının anlamına gelir. Numaralandırıcılar genellikle dil kullanılan `foreach` döngü çağrı yığınındaki döndürülür, numaralandırıcı yapısını kullanır. Bir nesne için yer açmak için çağrı yığın işaretçisi artan yaptığı gibi bir yığın ayırma GC etkilemez. 
  
 Genişletilmiş durumunda `FirstOrDefault` çağrı, kod çağırmak gereken `GetEnumerator()` üzerinde bir <xref:System.Collections.Generic.IEnumerable%601>. Atama `symbols` için `enumerable` türündeki değişken `IEnumerable<Symbol>` gerçek nesneye bilgileri kaybeder bir <xref:System.Collections.Generic.List%601>. Kod ile Numaralandırıcı getirir olduğunda bunun anlamı `enumerable.GetEnumerator()`, geri döndürülen yapı atamak kutu içine almak .NET Framework sahip `enumerator` değişkeni. 
  
 **Örneğin 5 Düzelt**  
  
 Düzeltme yeniden yazmaktır `FindMatchingSymbol` gibi yine de kısa, okumanız ve anlamanız kolay ve sürdürmek daha kolay olan altı kod satırıyla, tek satırlık bir kod değiştirme:  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 Bu kod, LINQ genişletme yöntemleri, lambdalar veya numaralandırıcılar kullanmaz ve edilmedi doğurur. Derleyici, görebilirsiniz çünkü edilmedi olan `symbols` koleksiyonu bir <xref:System.Collections.Generic.List%601> ve sonuçta elde edilen Numaralandırıcı (yapı) yerel bir değişkene kutulama önlemek için doğru tür ile bağlayabilirsiniz. Bu işlevin özgün sürümle etkileyici gücüyle C# ve .NET Framework'ün üretkenlik harika bir örneği oluştu. Bu yeni ve daha verimli sürümü bu kalitelerini korumak için karmaşık kodlar eklemeden korur. 
  
### <a name="async-method-caching"></a>Zaman uyumsuz yöntem önbelleğe alma  
 Sonraki örnek, ortak bir sorunu gösterir, önbelleğe alınan sonuçları kullanmaya çalıştığınızda bir [zaman uyumsuz](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) yöntemi. 
  
 **Örnek 6: zaman uyumsuz yöntemlerde önbelleğe alma**  
  
 Söz dizimi ağacı sık yeni C# ve Visual Basic derleyicileri üzerinde oluşturulmuş Visual Studio IDE özelliklerini getirmek ve derleyiciler Visual Studio yanıt saklamak için Bunun yapılması, zaman uyumsuz kullanın. Sözdizimi ağacı almak için yazabilirsiniz kod ilk hali aşağıdadır:  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Çağırmanın gördüğünüz `GetSyntaxTreeAsync()` örnekleyen bir `Parser`kodunu ayrıştırır ve ardından döndürür bir <xref:System.Threading.Tasks.Task> nesnesi `Task<SyntaxTree>`. Pahalı bölümü ayırma `Parser` örneği ve kod ayrıştırma. İşlev döndürür bir <xref:System.Threading.Tasks.Task> çağıranlar ayrıştırma işi await ve kullanıcı girişine yanıt olarak UI iş parçacığı ücretsiz. 
  
 Birçok Visual Studio özellikleri zaman ve ayırmaların Kaydet ayrıştırma sonucunu önbelleğe almak için aşağıdaki kodu yazabilirsiniz aynı söz dizimi ağacı almak deneyebilir. Ancak, bu kod, bir ayırma doğurur:  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 Önbelleğe alma ile yeni kod olduğunu gördüğünüz bir `SyntaxTree` adlı alan `cachedResult`. Bu alan boş olduğunda `GetSyntaxTreeAsync()` çalışır ve sonuçları önbelleğe kaydeder. `GetSyntaxTreeAsync()` döndürür `SyntaxTree` nesne. Varsa, sorunu olan bir `async` türünde işlevi `Task<SyntaxTree>`, ve türünde bir değer döndürür `SyntaxTree`, derleyici sonucu tutmak için bir görev ayırmak için kodu yayan (kullanarak `Task<SyntaxTree>.FromResult()`). Görevin tamamlandı olarak işaretlenir ve sonuç hemen kullanılabilir. Yeni derleyicileri için kodunda <xref:System.Threading.Tasks.Task> zaten tamamlanmış nesneler, böylece genellikle bu düzeltmeyle Bu ayırmaları yanıt hızını önemli ölçüde geliştirilmiş oluştu. 
  
 **Örneğin 6 Düzelt**  
  
 Tamamlanan kaldırmak için <xref:System.Threading.Tasks.Task> ayırma, görev nesnesi tamamlanmış sonucuyla önbelleğe alabilir:  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??   
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Bu kod değişiklikleri türde `cachedResult` için `Task<SyntaxTree>` ve kullandığı bir `async` özgün koda göre tutan yardımcı işlevini `GetSyntaxTreeAsync()`. `GetSyntaxTreeAsync()` artık kullanan [null birleşim işleci](../../csharp/language-reference/operators/null-coalescing-operator.md) döndürülecek `cachedResult` null değilse. Varsa `cachedResult` null ise `GetSyntaxTreeAsync()` çağrıları `GetSyntaxTreeUncachedAsync()` ve sonucu önbelleğe alır. Dikkat `GetSyntaxTreeAsync()` çağrısı await değil `GetSyntaxTreeUncachedAsync()` kod normalde yaptığınız gibi. Kullanmayan await anlamına gelir olduğunda `GetSyntaxTreeUncachedAsync()` döndürür, <xref:System.Threading.Tasks.Task> nesnesi `GetSyntaxTreeAsync()` hemen döndürür <xref:System.Threading.Tasks.Task>. Artık, önbelleğe alınan sonucu olan bir <xref:System.Threading.Tasks.Task>var. Bu nedenle önbelleğe alınan sonuçları döndürmek için edilmedi. 
  
### <a name="additional-considerations"></a>Ek hususlar  
 Büyük uygulamalar veya çok miktarda veri işleyen uygulamalar olası sorunlar hakkında birkaç daha fazla noktalar şunlardır. 
  
 **sözlükler**  
  
 Ancak çok kullanışlı ve verimli kendiliğinden sözlükleri ve sözlükleri ubiquitously birçok programlarda kullanılır. Ancak, bunlar genellikle uygunsuz bir şekilde kullanılır. Visual Studio ve yeni derleyicileri, analiz sözlükleri birçoğu bulunan tek bir öğe veya boş gösterir. Boş bir <xref:System.Collections.Generic.Dictionary%602> on alanları olan ve 48 bayt x x86 yığın üzerinde kapladığı makine. Sabit zamanlı arama ile eşleştirme veya ilişkili bir veri yapısı gerektiğinde sözlükleri mükemmel özellikler. Ancak, yalnızca birkaç öğeleri varsa, bir sözlük kullanarak alanı çok fazla vakit. Bunun yerine, örneğin, tekrarlayarak bakarak bir `List<KeyValuePair\<K,V>>`, yalnızca hızlı. Yalnızca ile veri yükleme ve ardından, (çok yaygın bir düzen) okumak için Sözlük kullanma, bir N(log(N)) arama ile sıralanmış bir diziyi kullanılarak yaklaşık olarak kullandığınız öğeleri sayısına bağlı olarak daha hızlı olabilir. 
  
 **Yapılar ve sınıflar**  
  
 Bir yolla, sınıfları ve yapıları Klasik alanı/saat tradeoff uygulamalarınızı ayarlama için sağlar. Sınıfları ücret 12 x x86 yükü baytını bile hiçbir alan sahiptirler, ancak bunlar etrafında yalnızca bir sınıf örneğine başvurmak için bir işaretçi aldığından geçirilecek ucuzdur makine. Yapıları Kutulu değildir, ancak büyük yapılar işlevi bağımsız değişken olarak geçirin veya dönüş değerleri, tüm veri üyelerini yapıları atomik olarak kopyalamak için CPU zaman alır, hiçbir yığın ayırmaları yansıtılmaz. Yinelenen çağrılar için iade yapıları ve özelliğin değerini aşırı miktarda veri kopyalamayı önlemek için yerel bir değişkende önbellek özellikleri dikkat edin. 
  
 **Önbellekler**  
  
 Genel bir performans elde sonuçlarını önbelleğe alma ' dir. Ancak, bir önbellek boyutu büyük harf ya da elden çıkarma İlkesi olmadan bir bellek sızıntısı olabilir. Çok miktarda bellek önbelleğinde tutun büyük miktarda veri işleme, çöp toplama, önbelleğe alınan aramaları avantajlarını geçersiz kılmak neden olabilir. 
  
 Bu makalede, nasıl özellikle büyük sistemleri veya büyük miktarda veri işleyen sistemleri için uygulamanızın yanıt hızını etkileyebilir performans sorununun belirtileri bilincinde olmalısınız almıştık. Ortak culprits kutulama, dize işlemeleri, LINQ ve lambda, önbellek boyutu sınırı veya çıkarma ilkesini, uygunsuz kullanımdan sözlükleri ve yapıları etrafında geçirme olmadan zaman uyumsuz yöntemlerde önbelleğe almayı içerir. Uygulamalarınızı ayarlama dört bilgiler göz önünde bulundurun:  
  
-   Yoksa beklenenden önce en iyi duruma getirme – üretken ve problemleri fark, uygulamanızı ayarlama. 
  
-   Profilleri şekilde yok –, olmayan ölçüm yaptığınız, tahmin. 
  
-   İyi Araçlar fark olun – PerfView indirin ve deneyin. 
  
-   Tüm olduğu ayırmaları hakkında – diğer bir deyişle derleyici platformu ekibinden yeni derleyiciler performansını iyileştirme zamanlarının çoğunu burada harcanan. 
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sunu bu konunun videosu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
- [Performans Profili Oluşturma Başlangıç Kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
- [Performans](../../../docs/framework/performance/index.md)  
- [.NET Performans İpuçları](https://msdn.microsoft.com/library/ms973839.aspx)  
- [Windows Phone Performans analiz aracı](https://msdn.microsoft.com/magazine/hh781024.aspx)  
- [Visual Studio Profiler uygulama performans sorunlarını bulun](https://msdn.microsoft.com/magazine/cc337887.aspx)  
- [Channel 9 PerfView öğreticiler](https://channel9.msdn.com/Series/PerfView-Tutorial)  
- [.NET derleyici Platformu SDK'sı](../../csharp/roslyn-sdk/index.md)
- [github'da dotnet/roslyn depo](https://github.com/dotnet/roslyn)
