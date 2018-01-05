---
title: "Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload: wiwagn
ms.openlocfilehash: ac4052773044e44f546894a54dc21728dbd6634a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-large-responsive-net-framework-apps"></a>Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
Bu makalede, büyük miktarda veri dosyaları veya veritabanları gibi işlem uygulamaları büyük .NET Framework uygulamaları veya performansını iyileştirmek için ipuçları verilmektedir. C# ve Visual Basic derleyicileri yönetilen kod yeniden yazma bu ipuçlarını gelir ve bu makale, C# Derleyici birkaç gerçek örneklerinden içermektedir.  
  
 .NET Framework uygulamaları oluşturmak için son derece verimli kümesidir.  Güçlü ve güvenli diller ve zengin bir koleksiyon kitaplıkların uygulama yapı yüksek oranda fruitful olun.  Ancak, harika verimliliğini sorumluluk gelir.  .NET Framework'ün tüm güç kullanır ancak gerektiğinde, kodun performansı ayarlamak hazırlanması gerekir.  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Yeni derleyici performans uygulamanıza neden uygular  
 .NET derleme Platformu ("Roslyn") ekibin C# yeniden yazıldı ve Visual Basic derleyicileri yönetilen kodu modelleme ve kodunu analiz etme, araçları oluşturmaya ve çok daha zengin, kod algılayan deneyimleri Visual Studio'da etkinleştirilmesi için yeni API sağlamak için.  Derleyicileri yeniden yazma işlemi ve Visual Studio derleme yeni derleyicileri deneyimler büyük herhangi bir .NET Framework uygulama ya da çok miktarda veri işleyen herhangi bir uygulama için geçerli olan yararlı performansı öngörüleri göstermiştir.  Öngörüler ve örnekler C# Derleyici yararlanmak için derleyicileri hakkında bilmeniz gerek yoktur.  
  
 Visual Studio API derleyici tanımlayıcıları ve anahtar sözcükler, sözdizimi tamamlanma listeleri, renklendirme dalgalı çizgiler gibi hatalar, parametre ipuçları, kod sorunları ve kod eylemleri için kullanıcıların hayran, tüm IntelliSense özellikleri oluşturmak için kullanır.  Visual Studio, geliştiricilerin yazarak ve kendi kod değiştirme ve derleyici sürekli kodu geliştiriciler Düzenle modeller sırada Visual Studio yanıt verebilir durumda kalması gereken çalışırken bu Yardım sağlar.  
  
 Son kullanıcılarınızın uygulamanızla etkileşim kurduklarında, bunlar esnek olmasını bekler.  Yazarak veya komut işleme hiçbir zaman engellenmelidir.  Yardım, hızlı bir şekilde pop veya kullanıcı yazmaya devam ederse işlemden vazgeçerlerdi.  Uygulamanızın kullanıcı Arabirimi iş parçacığı ağır eşitleyerek uygulama olun uzun hesaplamalar ile engelleme kaçınmalısınız.  
  
 Roslyn derleyicileri hakkında daha fazla bilgi için ziyaret [dotnet/roslyn](https://github.com/dotnet/roslyn) bağlantıların github'da.
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a>Yalnızca bulguları  
 Bu bilgiler performans ayarlama yaparken göz önünde bulundurun ve yanıt veren .NET Framework uygulamaları oluşturma.  
  
### <a name="fact-1-dont-prematurely-optimize"></a>Olgu 1: erken en iyi duruma getirme yok  
 Olması gerekenden daha karmaşıktır kod yazma hata ayıklama ve maliyetleri polishing bakım doğurur.  Deneyimli programcıları sezgisel bir kavrayın kodlama sorunlarını çözmek ve daha verimli kod yazmak nasıl olması.  Ancak, bunlar bazen erken kendi kodu en iyi duruma getirme.  Örneğin, basit bir dizi yeterli veya yalnızca değerleri recomputing yerine bellek sızıntısı görülebilir karmaşık önbelleğe kullandığınızda bir karma tablosu kullanın.  Bir deneyim Programcı olsa için performans testi ve sorunları bulduğunuzda, kodunuzun analiz edin.  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Olgu 2:, ölçüm yaptığınız değil ise, tahmin  
 Profilleri ve ölçümleri yer yok.  Profilleri CPU tam olarak yüklü olduğu ya da disk g/ç üzerinde engellenen göster.  Profilleri söyleyin, size, ne tür ve ne kadar bellek ayırma ve mi, CPU harcama çok zaman içinde [çöp toplama](../../../docs/standard/garbage-collection/index.md) (GC).  
  
 Anahtar müşteri için performans hedeflerini deneyimleri veya senaryolar uygulamanızı ayarlama ve performansını ölçmek için testleri yazmak gerekir.  Başarısız olan testleri bilimsel yöntemi uygulayarak araştırın: profillerini kullanmak için size yol, ne sorun olabilir, hypothesize ve varsayımınızın bir denemeyi ile test veya kod değişikliği.  Performans gerileme neden değişiklikleri yalıtabilirsiniz şekilde normal test ile zamanla temel performans ölçümleri oluşturun.  Sıkı bir şekilde performans iş yaklaşan tarafından gerekmeyen kod güncelleştirmeleriyle zaman kaçının.  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Olgu 3: İyi araçları tüm fark kolaylaştırır.  
 Hızlı bir şekilde büyük performans sorunlarını (CPU, bellek veya disk) ve bu performans sorunu neden kodu bulun Yardım ayrıntıya iyi araçları sağlar.  Microsoft çeşitli performans araçları gibi birlikte gelen [Visual Studio profil oluşturucu](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone çözümleme aracı](http://msdn.microsoft.com/en-us/e67e3199-ea43-4d14-ab7e-f7f19266253f), ve [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).  
  
 PerfView disk g/ç gibi ayrıntılı sorunları odaklanmak, GC olayları ve bellek yardımcı olan ücretsiz ve son derece güçlü bir araçtır.  Performansla ilgili yakalayabilirsiniz [Windows için olay izleme](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) olayları ve görünüm kolayca uygulama başına, işlem başına, yığın başına ve başına iş parçacığı bilgileri.  PerfView uygulamanızı ayırır, bellek ve hangi işlevleri veya çağrı yığınları ne kadar bellek ayırmaları katkıda ne kadar ve ne tür gösterir. Ayrıntılar için bkz: zengin Yardım konuları, gösterileri ve aracıyla dahil videoları (gibi [PerfView öğreticileri](http://channel9.msdn.com/Series/PerfView-Tutorial) Channel 9).  
  
### <a name="fact-4-its-all-about-allocations"></a>Olgu 4: Tüm ayırmaları hakkında olduğu  
 Bu esnek bir derleme düşünebilirsiniz .NET Framework uygulaması Kabarcık sıralama yerine Hızlı sıralama kullanarak gibi tüm algoritmalar hakkında ancak bu durumda değil.  Özellikle uygulamanız çok büyük olduğunda veya büyük miktarlarda verinin işler esnek bir uygulaması oluşturmanın en büyük faktörü bellek ayırma olduğu.  
  
 Neredeyse tüm iş esnek IDE oluşturmak için yeni derleyici API'leri ile karşılaştığında ayırmaları önleme ve önbelleğe alma stratejilerine yönetme dahil.  PerfView izlemeleri yeni C# ve Visual Basic derleyicileri performansını nadiren CPU'ya olmadığını gösterir.  Oluşturulan kod yayma veya derleyicileri meta verileri okuma binlerce veya kod satırı milyonlarca yüzlerce okunurken bağlı g/ç olabilir.  Kullanıcı Arabirimi iş parçacığı gecikmeler neredeyse tüm atık toplama nedeniyle ' dir.  .NET Framework GC yüksek performans için ayarlanmış ve uygulama kodu eşzamanlı olarak çalışırken çalışmasını çoğunu yapar.  Ancak, tek bir ayırma pahalı bir tetikleyebilir [gen2](../../../docs/standard/garbage-collection/fundamentals.md) koleksiyon, tüm iş parçacıklarını durdurma.  
  
## <a name="common-allocations-and-examples"></a>Ortak ayırma ve örnekler  
 Bu bölümdeki örnek ifadeler küçük görünür ayırmaları gizli.  Ancak, büyük uygulama yeterli kez ifadeleri yürütülürse, megabayt, hatta gigabayt cinsinden ayırmalarının yüzlerce nedenleri olabilir.  Bir geliştiricinin bellek tahsis düzenleyicisinde yazarak benzetimli ve senaryoları yazarak odaklanmak için performans takım öncülük Örneğin, bir dakikalık sınamaları.  
  
### <a name="boxing"></a>Kutulama  
 [Kutulama](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) normalde değer türleri yığında Canlı veya nesneyi Sarmalanan veri yapılarını oluşur.  Diğer bir deyişle, verileri tutmak için bir nesne ayrılamadı ve ardından bir işaretçi nesnesine dönün.  .NET Framework bazen değerleri bir yöntem veya bir depolama konumu türünün imza nedeniyle kutuları.  Değer türü içinde bir nesne nedenler bellek ayırma kaydırma.  Birçok kutulama işlemleri, megabayt veya gigabayt uygulamanızı daha fazla GC'ler sebep ve uygulamanızın ayırmalarının katkıda bulunabilir. .NET Framework ve dil derleyicileri kutulama mümkün olduğunda kaçının ancak bazen az beklediğiniz olur.  
  
 PerfView kutulama görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığında bakın (unutmayın, PerfView raporları tüm işlemleri).  Türleri gibi görürseniz <xref:System.Int32?displayProperty=nameWithType> ve <xref:System.Char?displayProperty=nameWithType> ayırmaları altında değer türleri kutulama.  Bu türlerinden birini seçerek Kutulu işlevler ve yığınları gösterir.  
  
 **Örnek 1: dize yöntemlerini ve değer türü bağımsız değişkenleri**  
  
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
  
 Bu kod bir uygulama çağırabilir günlük işlevini sağlar `Log` sık, belki de kez milyonlarca işlev.  Sorunu olan çağrısı `string.Format` çözümler <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yükleme.  
  
 .NET Framework kutusuna bu aşırı gerektirir `int` bu yöntem çağrısı geçirilecek nesneleri içine değerleri.  Kısmi bir düzeltme çağırmaktır `id.ToString()` ve `size.ToString()` ve geçişi için (hangi nesnelerin olduğunu) tüm dizeleri `string.Format` çağırın.  Çağırma `ToString()` ayırma içinde yine de gerçekleşir ancak bu bir dize tahsis `string.Format`.  
  
 Bu bu temel düşünebilirsiniz çağrısı `string.Format` yalnızca dize birleştirme olduğundan, bunun yerine bu kod yazabilirsiniz:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ancak, bu kod satırı kutulama ayırma tanıtır için derler olduğundan <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.  .NET Framework çağırmak için değişmez değer karakter kutusunda gerekir`Concat`  
  
 **Örneğin 1 Düzelt**  
  
 Tam düzeltme basit bir işlemdir.  Yalnızca karakter değişmez değeri bir dize değişmez değer dizeleri nesneler olduğundan, hiçbir kutulama doğurur değiştirin:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Örnek 2: enum kutulama**  
  
 Bu örnekte sık kullanılan nedeniyle yeni C# ve Visual Basic derleyicileri tahsisini sözlük arama işlemlerinde özellikle numaralandırma türlerinin çok büyük miktarlarda sorumlu.  
  
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
  
 Bu sorun çok ince oluşur.  PerfView bu olarak rapor <xref:System.Enum.GetHashCode> yöntemi uygulama nedeniyle numaralandırma türü temeldeki gösterimini kutular çünkü kutulama.  İçinde PerfView yakından bakarsanız, her çağrı için iki kutulama ayırmaları görebilirsiniz <xref:System.Enum.GetHashCode>.   Derleyici bir ekler ve .NET Framework diğer ekler.  
  
 **Örneğin 2 düzeltme**  
  
 Temel alınan gösterimi çağırmadan önce atama tarafından her iki ayırma kolayca önleyebilirsiniz <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Kutulama Numaralandırma türleri üzerinde başka bir ortak kaynağı <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemi.  Geçirilen bağımsız değişken <xref:System.Enum.HasFlag%28System.Enum%29> Kutulu gerekir.  Çoğu durumda, çağrıları değiştirme <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bit düzeyinde bir test ile daha basit ve ayırma boş olur.  
  
 İlk performans olgu unutmayın (diğer bir deyişle, erken İyileştir yok) ve bu şekilde tüm kodunuzu yeniden yazma işlemi başlatma.    Bu kutulama maliyetinden unutmayın, ancak yalnızca uygulama profili oluşturma ve etkin noktalar bulma sonra kodunuzu değiştirmek.  
  
### <a name="strings"></a>Dizeler  
 Dize işlemeleri ayırmaları için büyük culprits bazıları ve bunlar genellikle PerfView içinde ilk beş ayırma gösterilir.  Programları dizeleri serileştirme, JSON ve REST API'lerini kullanır.  Numaralandırma türleri kullanamadığında sistemleriyle birlikte için programlı sabitleri dizelerini kullanabilirsiniz.  Çağrılar, profil dizeleri performans yüksek oranda etkileyen göstermediğinde arayın <xref:System.String> gibi yöntemler <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>ve benzeri.  Kullanarak <xref:System.Text.StringBuilder> bir dize oluşturma çok sayıda parça yardımcı olur, ancak bile ayırma maliyetini önlemek için <xref:System.Text.StringBuilder> nesne yönetmeniz gereken bir performans sorunu hale.  
  
 **Örnek 3: dize işlemleri**  
  
 C# Derleyici biçimlendirilmiş XML Belge açıklama metni yazar bu kodunu döndürdü:  
  
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
  
 Bu kod dize düzenlemesi çok mu görebilirsiniz.  Kod kitaplığı yöntemi satırları denetlemek için boşluk, kırpma için ayrı dizeleri, bölmek için kullanır. olup olmadığını bağımsız değişkeni `text` bir XML belge açıklaması ve satırlarından alt dizeler ayıklamak için.  
  
 İçinde ilk satırda `WriteFormattedDocComment`, `text.Split` çağrısı her çağrıldığında bu yeni üç öğeli bir dizi bağımsız değişken olarak ayırır.  Bu dizinin her zaman ayırmak için kod yaymak üzere derleyici sahiptir.  Derleyici, bilmiyor çünkü <xref:System.String.Split%2A> yere Burada dizi değiştirilmesi daha sonraki çağrıları etkileyecek diğer kodu tarafından dizi depolar `WriteFormattedDocComment`.  Çağrı <xref:System.String.Split%2A> ayrıca her satır için bir dize ayırır `text` ve işlemi gerçekleştirmek için başka bir bellek ayırır.  
  
 `WriteFormattedDocComment`üç çağrı sahip <xref:System.String.TrimStart%2A> yöntemi.  İş ve ayırmaları yinelenen iç Döngülerde ikisidir.  Önemlidir daha da kötüsü, arama yapmak için <xref:System.String.TrimStart%2A> yöntemi bağımsız değişken içermeyen boş bir dizi ayırır (için `params` parametresi) dize sonucu yanı sıra.  
  
 Son olarak, bir arama var. <xref:System.String.Substring%2A> genellikle yeni bir dize ayırır yöntemi.  
  
 **Örneğin 3 Düzelt**  
  
 Önceki örneklerin aksine bu ayırmaları küçük düzenlemeler düzeltilemiyor.  Geri adım, sorun ve farklı şekilde yaklaşır gerekir.  Örneğin, olduğunu fark edeceksiniz bağımsız değişkeni `WriteFormattedDocComment()` kodu birçok kısmi dizeler ayırma yerine daha fazla dizin oluşturma yapabilirsiniz, böylece yöntemi gerektiren tüm bilgilere sahip bir dizedir.  
  
 Derleyicinin performans takım bu ayırma aşağıdakine benzer bir kod ile tackled:  
  
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
  
 İlk sürümü `WriteFormattedDocComment()` bir dizi, birkaç alt dizeler ve boş bir birlikte bölünen substring ayrılan `params` dizi.  Bu ayrıca kontrol `"///"`.  Düzeltilmiş kod yalnızca dizin oluşturma kullanır ve hiçbir şey ayırır.  Boşluk ve denetimleri karakter dizesi ile başlayıp başlamadığını görmek için düzeyinde değil ilk karakteri bulur `"///"`.  Yeni kod kullanır `IndexOfFirstNonWhiteSpaceChar` yerine <xref:System.String.TrimStart%2A> bir boşluk olmayan karakter oluştuğu (sonra belirtilen başlangıç dizini) ilk dizin dönün.  Düzeltme tam değilse, ancak eksiksiz bir çözüm için benzer düzeltmelerini uygulamak nasıl görebilirsiniz.  Bu yaklaşım kod genelindeki uygulayarak, tüm ayırma kaldırabilirsiniz `WriteFormattedDocComment()`.  
  
 **Örnek 4: StringBuilder**  
  
 Bu örnekte bir <xref:System.Text.StringBuilder> nesnesi.  Genel türler için tam tür adı aşağıdaki işlevi oluşturur:  
  
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
  
 Yeni bir satıra odak noktasıdır <xref:System.Text.StringBuilder> örneği.  Kod için bir ayırma neden `sb.ToString()` ve iç ayırmaları içinde <xref:System.Text.StringBuilder> uygulaması, ancak denetimi bu ayırmaları dize sonucu istiyorsanız.  
  
 **Örneğin 4 Düzelt**  
  
 Düzeltmek için `StringBuilder` ayırma nesne, nesne önbellek.  Hatta atılmak tek bir örnek önbelleğe alma performansını önemli ölçüde artırabilir.  Bu yeni ilk ve son satır hariç tüm kod atlama işlevin yeni uygulama.  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Anahtar bölümleri yenidir `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` işlevleri:  
  
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
  
 Yeni derleyicileri iş parçacığı oluşturma kullandığından, bu uygulamaların bir iş parçacığı statik alanı kullanın (<xref:System.ThreadStaticAttribute> özniteliği) önbelleğe <xref:System.Text.StringBuilder>, ve büyük olasılıkla atlayabilirsiniz `ThreadStatic` bildirimi.  İş parçacığı statik alan bu kodu yürütür her iş parçacığı için benzersiz bir değere sahiptir.  
  
 `AcquireBuilder()`önbelleğe alınan döndürür <xref:System.Text.StringBuilder> varsa, temizlemeden ve alan veya önbellek null değerine ayarlayarak sonra örneği.  Aksi takdirde `AcquireBuilder()` yeni bir örnek oluşturur ve alan veya önbellek kümesi null bırakarak döndürür.  
  
 İle bitirdiğinizde <xref:System.Text.StringBuilder> , çağırmanız `GetStringAndReleaseBuilder()` dize sonucu elde etmek için Kaydet <xref:System.Text.StringBuilder> örnek alan veya önbellek ve sonucu döndürür.  Bu kod yeniden girin ve birden çok oluşturmak için yürütme için mümkündür <xref:System.Text.StringBuilder> (, nadiren gerçekleşir rağmen) nesneleri.  Yalnızca son yayımlanan kod kaydeder <xref:System.Text.StringBuilder> örnek daha sonra kullanmak için.  Bu basit önbelleğe alma stratejisi yeni derleyicileri ayırma önemli ölçüde azalır.  MSBuild ("MSBuild") ve .NET Framework bölümleri, performansı artırmak için benzer bir teknik kullanın.  
  
 Bir boyut cap içerdiğinden bu basit önbelleğe alma stratejisi iyi önbellek tasarım uyar.  Ancak, daha fazla bakım maliyetlerinin anlamı özgün, artık daha fazla kod yoktur.  Yalnızca bir performans sorununu buldunuz ve PerfView, gösterilen önbelleğe alma stratejisi benimsemeyi <xref:System.Text.StringBuilder> ayırmaları olan önemli katılımcı.  
  
### <a name="linq-and-lambdas"></a>LINQ ve lambdas  
 Dil ile tümleşik sorgu (LINQ) ve lambda ifadeleri kullanma kodu performansı önemli bir etkisi olursa yeniden yazmak zorunda daha sonra bulabileceğiniz üretken özellikleri kullanarak, harika bir örnektir.  
  
 **Örnek 5: Lambda'lar, liste\<T > ve IEnumerable\<T >**  
  
 Bu örnekte [LINQ ve işlevsel stili kodu](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) ad dizesini verilen bir sembol derleyicinin modelinde bulmak için:  
  
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
  
 Yeni derleyici ve arama üzerinde oluşturulmuş IDE deneyimleri `FindMatchingSymbol()` bu işlevin tek satırlık bir kod birkaç gizli ayırma şunlardır: çok sık ve vardır.  Bu ayırmaları incelemek için ilk işlevin tek satırlık bir kod iki çizgiye bölün:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 İlk satırdaki [lambda ifadesi](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[üzerinden kapatır](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) yerel değişken `name`.  Bu, bir nesne için ayırma yanı sıra gelir [temsilci](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` tutan kodu ayırır değerini yakalar ortamı tutmak için bir statik sınıf `name`.  Derleyici aşağıdaki gibi bir kod oluşturur:  
  
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
  
 İki `new` ayırmaları (bir ortam sınıfı için) ve bir temsilci için açık şimdi.  
  
 Şimdi çağrısına bakın `FirstOrDefault`. Bu uzantı metodu <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türü bir ayırma çok doğurur.  Çünkü `FirstOrDefault` geçen bir <xref:System.Collections.Generic.IEnumerable%601> nesnesi, ilk bağımsız değişkeni olarak (bir bit tartışma için Basitleştirilmiş) aşağıdaki kodu çağrısı genişletebilirsiniz:  
  
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
  
 `symbols` Değişken türüne sahip <xref:System.Collections.Generic.List%601>.  <xref:System.Collections.Generic.List%601> Koleksiyon türü uygulayan <xref:System.Collections.Generic.IEnumerable%601> ve zekice bir numaralandırıcı tanımlar (<xref:System.Collections.Generic.IEnumerator%601> arabirimi), <xref:System.Collections.Generic.List%601> ile uygulayan bir `struct`.  Bir sınıf yerine bir yapı kullanarak hangi sırayla, atık toplama performansını etkileyebilecek herhangi yığın ayırmaları genellikle kaçının anlamına gelir.  Numaralandırmalar genelde dil kullanılan `foreach` çağrı yığınındaki döndürülen Numaralandırıcı yapısı kullanır döngüsü.  Bir nesne için yer açmak için çağrı yığını işaretçi artırma yaptığı gibi bir yığın ayırma GC etkilemez.  
  
 Genişletilmiş durumunda `FirstOrDefault` çağrısı kod gereken çağırmak `GetEnumerator()` üzerinde bir <xref:System.Collections.Generic.IEnumerable%601>.  Atama `symbols` için `enumerable` değişken türü `IEnumerable<Symbol>` gerçek nesne bilgileri kaybeder bir <xref:System.Collections.Generic.List%601>.  Kod Numaralandırıcı ile getirir, yani `enumerable.GetEnumerator()`, .NET Framework atamak döndürülen yapısı kutusunda gereken `enumerator` değişkeni.  
  
 **Örneğin 5 Düzelt**  
  
 Düzeltme yeniden yazmaktır `FindMatchingSymbol` gibi kendi tek satırlık bir kod hala kısa, kolay okuduğunuzdan ve anladığınızdan ve bakımını kolay olan altı kod satırıyla değiştirme:  
  
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
  
 Bu kod LINQ genişletme yöntemleri, Lambda'lar veya numaralandırıcıları kullanmayan ve hiçbir ayırmaları doğurur.  Derleyici görebilirsiniz çünkü hiçbir ayırmaları olan `symbols` koleksiyonu bir <xref:System.Collections.Generic.List%601> ve sonuçta elde edilen Numaralandırıcı (yapı) yerel bir değişkene kutulama önlemek için doğru türü ile bağlayabilirsiniz.  Bu işlev özgün sürümü gücüyle C# ve .NET Framework'ün üretkenlik harika bir örneği oluştu.  Bu yeni ve daha verimli sürümü korumak için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.  
  
### <a name="async-method-caching"></a>Zaman uyumsuz yöntem önbelleğe alma  
 Önbelleğe alınan sonuçları kullanmaya çalıştığınızda sonraki örnek ortak bir sorunu gösterir. bir [zaman uyumsuz](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) yöntemi.  
  
 **Örnek 6: zaman uyumsuz yöntemleri önbelleğe alma**  
  
 Sözdizimi ağacı üzerinde yeni C# ve Visual Basic derleyicileri sık yerleşik olarak bulunan Visual Studio IDE özelliklerinden getirebilir ve derleyicileri Visual Studio yanıt verebilir durumda tutmak için bunu yaparken zaman uyumsuz kullanın.  Sözdizimi ağacı almak için yazabilir kod ilk sürümü şöyledir:  
  
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
  
 Bu arama görebilirsiniz `GetSyntaxTreeAsync()` başlatır bir `Parser`kodu ayrıştırır ve ardından döndürür bir <xref:System.Threading.Tasks.Task> nesnesi `Task<SyntaxTree>`.  Pahalı bölümü ayırma `Parser` örneği ve kod ayrıştırma.  İşlevi döndürür bir <xref:System.Threading.Tasks.Task> böylece çağıranlar ayrıştırma iş bekler ve kullanıcı girişine yanıt vermesi kullanıcı Arabirimi iş parçacığı boş.  
  
 Saat ve ayırmaları kaydetmek için ayrıştırma sonucu önbelleğe almak için aşağıdaki kodu yazabilirsiniz aynı sözdizimi ağacı almak birkaç Visual Studio özellikleri deneyebilirsiniz.  Ancak, bu kod bir ayırma oluşturur:  
  
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
  
 Önbelleğe alma ile yeni koduna sahip olduğunu gördüğünüz bir `SyntaxTree` adlı alanı `cachedResult`.  Bu alan boş olduğunda `GetSyntaxTreeAsync()` işi yapar ve sonuç önbelleğine kaydeder.  `GetSyntaxTreeAsync()`döndürür `SyntaxTree` nesnesi.  Varsa olan sorunu bir `async` türündeki işlevi `Task<SyntaxTree>`, ve türünde bir değer döndürmesi `SyntaxTree`, sonuç tutmak için bir görev ayırmak için kod derleyicisi yayar (kullanarak `Task<SyntaxTree>.FromResult()`).  Görev tamamlandı olarak işaretlenir ve sonucu hemen kullanılabilir.  Yeni derleyicileri kodunda <xref:System.Threading.Tasks.Task> zaten tamamlandığından nesneleri oluştu nedenle genellikle bu düzeltmeyle Bu ayırmaları yanıtlama hızı önemli ölçüde geliştirildi.  
  
 **Örneğin 6 Düzelt**  
  
 Tamamlanan kaldırmak için <xref:System.Threading.Tasks.Task> ayırma, tamamlanmış sonuç görev nesnesiyle önbelleğe alabilir:  
  
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
  
 Bu kod türünü değiştirir `cachedResult` için `Task<SyntaxTree>` ve kullanan bir `async` özgün kod tutan yardımcı işlevini `GetSyntaxTreeAsync()`.  `GetSyntaxTreeAsync()`Şimdi kullanan [null birleştirmesi işleci](~/docs/csharp/language-reference/operators/null-conditional-operator.md) dönmek için `cachedResult` null değilse.  Varsa `cachedResult` null ise `GetSyntaxTreeAsync()` çağrıları `GetSyntaxTreeUncachedAsync()` ve sonucu önbelleğe alır.  Dikkat `GetSyntaxTreeAsync()` çağrısı await değil `GetSyntaxTreeUncachedAsync()` kodu normal olarak.  Await anlamına gelir kullanmıyor olduğunda `GetSyntaxTreeUncachedAsync()` döndürür kendi <xref:System.Threading.Tasks.Task> nesnesi, `GetSyntaxTreeAsync()` hemen döndürür <xref:System.Threading.Tasks.Task>.  Şimdi, önbelleğe alınan sonucu olan bir <xref:System.Threading.Tasks.Task>, bu nedenle hiçbir ayırmaları önbelleğe alınmış bir sonuç yok.  
  
### <a name="additional-considerations"></a>Ek hususlar  
 Büyük uygulamalar ya da çok miktarda veri işleyen uygulamalar olası sorunlar hakkında daha fazla birkaç noktalar şunlardır.  
  
 **Sözlük**  
  
 Ancak çok kullanışlı ve kendiliğinden verimli sözlükler ve sözlükleri ubiquitously birçok programda kullanılır.  Ancak, bunlar genellikle açamayacağı kullanılır.  Visual Studio ve yeni derleyicileri, analiz sözlükler birçoğu tek bir öğe içeriyor veya boş gösterir.  Boş bir <xref:System.Collections.Generic.Dictionary%602> on alanları olan ve bir x86 üzerinde yığında 48 bayt kaplar makine.  Bir eşleme veya ilişkilendirilebilir veri yapısı sabiti zamanı arama ile gerektiğinde sözlükler mükemmeldir.  Yalnızca birkaç öğeler varsa, ancak, çok fazla alan bir sözlüğünü kullanarak boşa harcanmasına.  Bunun yerine, örneğin, yinelemeli olarak görünebilir bir `List<KeyValuePair\<K,V>>`, yalnızca hızlı.  Sıralanmış bir dizi N(log(N)) arama ile kullanarak, kullanmakta olduğunuz öğeleri sayısına bağlı olarak, hızlı olarak neredeyse yalnızca ile veri yükleme ve ondan (çok yaygın bir desen) okumak için bir sözlük kullanıyorsanız olabilir.  
  
 **Sınıfları ve yapıları**  
  
 Bir biçimde sınıfları ve yapıları Klasik alanı/saat kolaylığını uygulamalarınızı ayarlamak için sağlar.  Sınıfları kullanan bir x86 ek yükü 12 bayt hiçbir alan sahip, ancak yalnızca bir sınıf örneğine başvuru yapmak için bir işaretçi aldığından geçici geçirmek uygun maliyetli olsa bile makine.  Yapıları hiçbir yığın ayırmaları Kutulu değil, ancak işlev bağımsız değişkenleri olarak büyük yapıları geçirmenizi ya da dönüş değerleri otomatik olarak yapıları tüm veri üyeleri kopyalamak için CPU süresi geçen doğurur.  Yinelenen çağrılar yapıları dönün ve özelliğin değeri, aşırı miktarda veri kopyalamayı önlemek için bir yerel değişkende önbellek özellikleri için dikkat edin.  
  
 **Önbellekler**  
  
 Ortak bir performans elde sonuçlarını önbelleğe alma ' dir.  Ancak, bir önbellek boyutu cap ya da elden ilkesine sahip olmayan bir bellek sızıntısı olabilir.  Çok sayıda önbellekleri bellekte tutun, büyük miktarlarda verilerin işlerken, önbelleğe alınan aramaları yararları geçersiz kılmak atık toplama neden olabilir.  
  
 Bu makalede, nasıl özellikle büyük sistemleri veya büyük miktarda veri işleyen sistemleri için uygulama yanıt hızını etkileyebilir performans sorununu Belirtiler bilincinde olmalısınız açıklanmıştır. Ortak culprits kutulama dize işlemeleri, LINQ ve lambda, önbellek boyutu sınırı ya da elden İlkesi, sözlükler ve yapıları geçici geçirme uygunsuz kullanımını olmadan zaman uyumsuz yöntemleri önbelleğe alma yer alır.  Uygulamalarınızı ayarlama dört bulguları göz önünde bulundurun:  
  
-   Yoksa erken en iyi duruma getirme – üretken ve sorunları nokta olduğunda, uygulamanızın ayarlayın.  
  
-   Profilleri kalan yok –, değil ölçümleri gerçekleştiriyoruz, tahmin.  
  
-   İyi araçları tüm fark olun – PerfView indirin ve deneyin.  
  
-   Tüm olmasından ayırmaları hakkında – başka bir deyişle derleyici platform takım yeni derleyicileri performansını iyileştirme zamanının çoğunu burada harcanan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bu konuda sunumu videosu](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [Performans profili oluşturma Başlangıç Kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [Performans](../../../docs/framework/performance/index.md)  
 [.NET Performans İpuçları](http://msdn.microsoft.com/library/ms973839.aspx)  
 [Windows Phone performans çözümleme aracı](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [Visual Studio Profil Oluşturucu ile uygulama engelleri bulun](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [Kanal 9 PerfView öğreticileri](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [Üst düzey performans ipuçları](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [DotNet/roslyn bağlantıların github'da](https://github.com/dotnet/roslyn)
