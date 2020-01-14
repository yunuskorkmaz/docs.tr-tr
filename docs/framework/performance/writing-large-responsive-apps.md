---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c320d004b05e58fc7c239cd8c1f3bcec84ad8f78
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937918"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma

Bu makalede, büyük .NET Framework uygulamalarının veya dosyalar ya da veritabanları gibi büyük miktarda veriyi işleyen uygulamaların performansını iyileştirmeye yönelik ipuçları sunulmaktadır. Bu ipuçları, Yönetilen koddaki C# ve Visual Basic derleyicilerinin yeniden yazma işleminden gelir ve bu makalede C# derleyicinin çeşitli gerçek örnekleri yer almaktadır. 
  
.NET Framework uygulamalar oluşturmak için son derece üretken değildir. Güçlü ve güvenli diller ve zengin kitaplıkların bir koleksiyonu, uygulamanın yüksek düzeyde meyve özelliği olmasını kolaylaştırır. Bununla birlikte, harika üretkenlik sorumluluğu gelir. .NET Framework tüm gücünü kullanmanız gerekir, ancak gerektiğinde kodunuzun performansını ayarlamaya hazır olursunuz. 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Yeni derleyici performansının neden uygulamanız için geçerli olduğu  
 .NET Compiler Platform ("Roslyn") ekibi, Visual Studio 'da C# kod modellemesi ve analiz etmek, araçları oluşturmak ve çok daha zengin, kod duyarlı deneyimler sağlamak Için yeni API 'ler sağlamak üzere Yönetilen koddaki ve Visual Basic derleyicilerini yeniden yazdı. Derleyicilerin yeniden oluşturulması ve yeni derleyicilerde Visual Studio deneyimleri oluşturmak, büyük .NET Framework uygulamaları veya çok sayıda veriyi işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörülerini ortaya çıkarmaktadır. Derleyicilerin sunduğu öngörülerden C# ve örneklerden yararlanmak için derleyiciler hakkında bilmeniz gerekmez. 
  
 Visual Studio, tanımlayıcıların ve anahtar sözcüklerin, sözdizimi tamamlanma listelerinin, dalgalı çizgiler hataları, parametre ipuçları, kod sorunları ve kod eylemleri gibi çok sevdiği tüm IntelliSense özelliklerini oluşturmak için derleyici API 'Lerini kullanır. Visual Studio, geliştiriciler kodu yazarken ve değiştirirken bu yardım 'ı sağlar ve derleyici sürekli olarak kod geliştiricilerin düzenlemesini düzenleyecağından Visual Studio yanıt vermeye devam etmelidir. 
  
 Son kullanıcılarınız uygulamanızla etkileşdiğinde, yanıt vermesini bekler. Yazma veya komut işleme hiçbir şekilde engellenmemelidir. Yardım hızlı bir şekilde açılır veya Kullanıcı yazmaya devam ederse bunu vermelidir. Uygulamanız, uygulamayı ağır hale getirmek için uzun hesaplamalar ile UI iş parçacığını engellemeyi engellememelidir. 
  
 Roslyn derleyicileri hakkında daha fazla bilgi için [.net Compiler Platform SDK 'sına](../../csharp/roslyn-sdk/index.md)bakın.
  
## <a name="just-the-facts"></a>Yalnızca olgu  
 Performansı ayarlama ve yanıt veren .NET Framework uygulamalar oluşturma konusunda bu olguları göz önünde bulundurun. 
  
### <a name="fact-1-dont-prematurely-optimize"></a>Olgu 1: zamanından önce iyileştirmeyin  
 Bu değerden daha karmaşık olan ve bakım, hata ayıklama ve polishing maliyetleri için gereken bir kod yazma. Deneyimli programcıların kodlama sorunlarını çözme ve daha verimli kod yazma hakkında sezgisel bir attık vardır. Ancak, bazen kodlarını daha önce iyileştirirler. Örneğin, basit bir dizi yeterli olduğunda bir karma tablo kullanır ya da yalnızca yeniden hesaplama değerleri yerine bellek sızıntısına neden olabilecek karmaşık önbellek kullanır. Deneyim programlayıcı olsanız bile, sorunları bulduğunuzda performansı test etmeniz ve kodunuzu çözümlemeniz gerekir. 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Olgu 2: ölçmeye başladıysanız tahmin edersiniz  
 Profiller ve ölçümler yer almıyor. Profiller, CPU 'nun tam olarak yüklenip yüklenmediğini veya disk g/ç üzerinde engellenip engellenmeyeceğini gösterir. Profiller size ne tür ve ne kadar bellek ayrılacağını ve CPU 'nun [çöp toplamada](../../standard/garbage-collection/index.md) (GC) çok fazla zaman harcamadığını söyler. 
  
 Uygulamanızda önemli müşteri deneyimleri veya senaryolar için performans hedefleri ayarlamanız ve ölçü performansına yönelik testler yazmanız gerekir. Bilimsel yöntemi uygulayarak başarısız testleri araştırın: size rehberlik etmek için profilleri kullanın, sorunun ne olabileceğini hypothesize ve bir deneme veya kod değişikliği ile varsayımını test edin. Düzenli test ile zaman içinde temel performans ölçümleri oluşturun, böylece performans üzerinde gerilemeyi ortaya tutmaya yönelik değişiklikleri ayırabilirsiniz. Performans çalışmasına ciddi bir şekilde yaklaşarak, ihtiyacınız olmayan kod güncelleştirmeleriyle zaman harcamaktan kaçınabilirsiniz. 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>3\. olgu: Iyi araçlar tüm farkları yapar  
 İyi araçlar, en büyük performans sorunlarına (CPU, bellek veya disk) hızla göz atalım ve bu performans sorunlarına neden olan kodu bulmanıza yardımcı olur. Microsoft, [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)gibi çeşitli performans araçları ile birlikte sunulur. 
  
 PerfView, disk g/ç, GC olayları ve bellek gibi derin sorunlara odaklanmanıza yardımcı olan ücretsiz ve başaramayabiliriz güçlü bir araçtır. Windows için performans ile ilgili [olay izleme](../wcf/samples/etw-tracing.md) (ETW) olaylarını yakalayabilir ve uygulama başına, işlem başına, yığın başına ve iş parçacığı bilgileri başına kolayca görüntüleyebilirsiniz. PerfView, uygulamanızın ne kadar ve ne tür bellek ayırdığını ve hangi işlevlerin veya çağrı yığınlarının bellek ayırmalarının ne kadar katkıda bulunduğunu gösterir. Ayrıntılar için bkz. araçla birlikte sunulan zengin yardım konuları, tanıtımlar ve videolar (örneğin, Channel 9 ' da [PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial) ). 
  
### <a name="fact-4-its-all-about-allocations"></a>Olgu 4: tüm ayırmalar hakkında  
 Bir yanıt veren .NET Framework uygulamasının, kabarcık sıralaması yerine hızlı sıralama kullanma gibi algoritmaların hepsi olduğunu düşünebilirsiniz, ancak bu durum böyle değildir. Yanıt veren bir uygulama oluşturmanın en büyük faktörü, özellikle uygulamanız çok büyükse veya büyük miktarlarda veriyi işliyorsa bellek ayırmaktır. 
  
 Ayırmaktan ve önbelleğe alma stratejilerinin yönetilmesine neden olan yeni derleyici API 'Leri ile yanıt veren IDE deneyimleri oluşturmaya yönelik neredeyse tüm çalışmalar. PerfView izlemeleri, yeni C# ve Visual Basic derleyicilerinin PERFORMANSıNıN nadiren CPU ile bağlantılı olduğunu gösterir. Derleyiciler yüzlerce binlerce veya milyonlarca satırı okurken, meta verileri okurken veya üretilen kod yayırken g/ç bağlantılı olabilir. Kullanıcı arabirimi iş parçacığı gecikmeleri çöp toplama nedeniyle neredeyse hepsi olur. .NET Framework GC, performans için yüksek düzeyde ayarlanmıştır ve uygulama kodu yürütüldüğü sırada işinin çoğunu eşzamanlı olarak yapar. Ancak, tek bir ayırma pahalı bir [Gen2](../../standard/garbage-collection/fundamentals.md) koleksiyonunu tetikleyip tüm iş parçacıklarını durdurabilir. 
  
## <a name="common-allocations-and-examples"></a>Ortak ayırmalar ve örnekler  
 Bu bölümdeki örnek ifadelerde küçük görünen gizli ayırmalar vardır. Ancak, büyük bir uygulama ifadeleri yeterince uzun bir şekilde yürütülüyorsa, yüzlerce megabayt, hatta gigabayt, hatta ayırmaya neden olabilir. Örneğin, düzenleyicide bir geliştiricinin yazı tipini uygulayan tek dakikalık testler, gigabayt bellek ayırmıştır ve performans ekibinin yazma senaryolarına odaklanmaya yol açmaktadır. 
  
### <a name="boxing"></a>Kutulama  
 [Kutulama](../../csharp/programming-guide/types/boxing-and-unboxing.md) , normalde yığında veya veri yapılarında bulunan değer türleri bir nesneye sarmalandıktan sonra gerçekleşir. Yani, verileri tutacak bir nesne ayırırsınız ve sonra nesneye bir işaretçi döndürülür. .NET Framework bazen bir yöntemin imzası veya bir depolama konumu türü nedeniyle değerlere izin vermez. Bir nesne içindeki bir değer türünü sarmalama, bellek ayırmaya neden olur. Birçok paketleme işlemi uygulamanıza megabayt veya gigabayt 'lik ayırmaları katkıda bulunabilir, bu da uygulamanızın daha fazla GB 'a neden olacağı anlamına gelir. .NET Framework ve dil derleyicileri, mümkün olduğunda kutulamayı önler, ancak bazen en azından beklediğinde meydana gelir. 
  
 PerfView içinde kutulamayı görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığınlarına bakın (tüm süreçlerdeki PerfView raporlarını unutmayın). <xref:System.Int32?displayProperty=nameWithType> gibi türler ve ayırmalar altında <xref:System.Char?displayProperty=nameWithType> görüyorsanız, değer türlerini kutulanıyorsanız. Bu türlerden birini seçmek, paketlenmiş yığınları ve işlevleri gösterir. 
  
 **Örnek 1: dize yöntemleri ve değer türü bağımsız değişkenleri**  
  
 Bu örnek kod, potansiyel olarak gereksiz ve aşırı kutulamayı göstermektedir:  
  
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
  
 Bu kod günlüğe kaydetme işlevselliği sağlar; bu nedenle, bir uygulama çoğunlukla milyonlarca kez `Log` işlevi çağırabilir. Sorun, `string.Format` çağrısının <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> aşırı yüklemeye çözümlenme sorunudur. 
  
 Bu aşırı yükleme, .NET Framework `int` değerlerini bu yöntem çağrısına iletmek için nesneleri olarak çağırmasını gerektirir. Kısmi bir çözüm `id.ToString()` ve `size.ToString()` çağırmak ve tüm dizeleri (nesneler) `string.Format` çağrısına iletmektir. `ToString()` çağırmak bir dize ayırır, ancak bu ayırma `string.Format`içinde de olur. 
  
 `string.Format` bu temel çağrının yalnızca dize birleştirme olduğunu düşünebilirsiniz, bu nedenle bunun yerine bu kodu yazabilirsiniz:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ancak, bu kod satırı <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>derlediğinden bir paketleme ayırması tanıtır. .NET Framework çağırmak için bir karakter sabit değeri kutusu gerekir `Concat`  
  
 **Örnek 1 için çözüm**  
  
 Tüm düzeltmeler basittir. Yalnızca karakter sabit değerini bir dize sabit değeri ile değiştirin, ancak dizeler zaten nesneler olduğundan kutulama yok:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Örnek 2: sabit listesi paketleme**  
  
 Bu örnek, özellikle sözlük arama işlemlerinde listeleme türlerinin sık sık kullanılması nedeniyle C# yeni ve Visual Basic derleyicilerde çok büyük miktarda ayrılmasından sorumludur. 
  
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
  
 Bu sorun çok daha hafif. Yöntem, uygulama nedenleriyle numaralandırma türünün temel gösterimine bir kutu olduğundan PerfView bunu <xref:System.Enum.GetHashCode> kutulama olarak bildirir. PerfView 'a yakından bakarsanız <xref:System.Enum.GetHashCode>her bir çağrı için iki paketleme ayırması görebilirsiniz. Derleyici bir tane ekler ve .NET Framework diğerini ekler. 
  
 **Örneğin 2**  
  
 <xref:System.Enum.GetHashCode>çağrılmadan önce temeldeki temsilde kaldırarak her iki ayırmadan kolayca kaçınabilirsiniz:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Numaralandırma türlerinde başka bir ortak paketleme kaynağı <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemidir. <xref:System.Enum.HasFlag%28System.Enum%29> geçirilen bağımsız değişken kutulanmış olmalıdır. Çoğu durumda, <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> çağrılarını bit düzeyinde bir test ile değiştirmek daha basit ve ayırma ücretsizdir. 
  
 İlk performans olgusunu göz önünde bulundurun (yani, zamanından önce iyileştirmeyin) ve tüm kodunuzu bu şekilde yeniden yazmayı başlamayamazsınız. Bu paketleme maliyetlerinden haberdar olun, ancak yalnızca uygulamanızın profilini oluşturup etkin noktaları bulduktan sonra kodunuzu değiştirin. 
  
### <a name="strings"></a>Dizeler  
 Dize işlemeleri, ayırmaların en büyük küllerinin bazılarıdır ve genellikle ilk beş tahsisde PerfView ' de görünür. Programlar serileştirme, JSON ve REST API 'Leri için dizeler kullanır. Sabit Listesi türlerini kullanamıyoruz, sistemlerle birlikte çalışmak için, dizeleri programlama sabitleri olarak kullanabilirsiniz. Profil oluşturma, dizelerin yüksek düzeyde etkilenmediğini gösteriyorsa, <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>gibi <xref:System.String> yöntemlere yönelik çağrılar olup olmadığına bakın. Birçok parçadan bir dize oluşturma maliyetinden kaçınmak için <xref:System.Text.StringBuilder> kullanmak yardımcı olur, ancak <xref:System.Text.StringBuilder> nesnesini ayırmak, yönetmeniz gereken bir performans sorunu haline gelebilir. 
  
 **Örnek 3: dize işlemleri**  
  
 Derleyici C# , BIÇIMLI bir XML belgesi açıklamasının metnini yazan bu koda sahipti:  
  
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
  
 Bu kodun çok sayıda dize düzenlemesi olduğunu görebilirsiniz. Kod, satırları ayrı dizelere bölmek, boşluk kırpmak, bağımsız değişken `text` bir XML belgesi yorumu olup olmadığını denetlemek ve satırlardan alt dizeleri ayıklamak için kitaplık yöntemlerini kullanır. 
  
 `WriteFormattedDocComment`içindeki ilk satırda `text.Split` çağrısı, her çağrıldığında bağımsız değişken olarak yeni bir üç öğeli dizi ayırır. Derleyicinin her seferinde bu diziyi ayırmak için kod yaymalıdır. Bunun nedeni, derleyicinin diziyi <xref:System.String.Split%2A> başka bir kodla bir yere depolayıp depoladığını, daha sonra `WriteFormattedDocComment`çağrılarını etkileyecek şekilde depolayabileceğini bilmez. <xref:System.String.Split%2A> çağrısı Ayrıca `text` her satır için bir dize ayırır ve işlemi gerçekleştirmek için diğer belleği ayırır. 
  
 `WriteFormattedDocComment`, <xref:System.String.TrimStart%2A> yöntemine üç çağrı içerir. İkisi de yinelenen iş ve ayırmaları yineleyen iç Döngülerde bulunur. Önemli hale getirmek için <xref:System.String.TrimStart%2A> yöntemi bağımsız değişken olmadan çağırmak, dize sonucuna ek olarak boş bir dizi (`params` parametresi için) ayırır. 
  
 Son olarak, genellikle yeni bir dize ayıran <xref:System.String.Substring%2A> yöntemine bir çağrı vardır. 
  
 **3. örnekte çözüm**  
  
 Önceki örneklerden farklı olarak, küçük düzenlemeler bu ayırmaları düzeltemedi. Geri dönüp soruna bakmanız ve farklı bir yaklaşım yapmanız gerekir. Örneğin, `WriteFormattedDocComment()` bağımsız değişkeninin yöntemin ihtiyacı olan tüm bilgilere sahip bir dize olduğunu fark edersiniz. bu nedenle kod birçok kısmi dize ayırmak yerine daha fazla dizin oluşturma işlemi yapabilmiştir. 
  
 Derleyicinin performans ekibi, tüm bu ayırmaların şu şekilde kodla aynı şekilde olduğunu.  
  
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
  
 `WriteFormattedDocComment()` ilk sürümü bir diziyi, birkaç alt dizeyi ve boş bir `params` dizisiyle birlikte bölünen bir alt dizeyi ayırmış. Ayrıca "///" için kontrol edilir. Düzeltilen kod yalnızca dizin oluşturmayı kullanır ve hiçbir şey ayırır. Boşluk olmayan ilk karakteri bulur ve sonra dizenin "///" ile başlatılıp başlatılmadığını görmek için karaktere göre karakteri denetler. Yeni kod, boşluk olmayan bir karakterin gerçekleştiği ilk dizini (belirtilen başlangıç dizininden sonra) döndürmek için <xref:System.String.TrimStart%2A> yerine `IndexOfFirstNonWhiteSpaceChar` kullanır. Düzeltme tamamlanmaz, ancak tüm çözümler için benzer düzeltmelerin nasıl uygulanacağını görebilirsiniz. Bu yaklaşımı kodun tamamında uygulayarak `WriteFormattedDocComment()`tüm ayırmaları kaldırabilirsiniz. 
  
 **Örnek 4: StringBuilder**  
  
 Bu örnek bir <xref:System.Text.StringBuilder> nesnesi kullanır. Aşağıdaki işlev genel türler için tam bir tür adı üretir:  
  
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
  
 Odak, yeni bir <xref:System.Text.StringBuilder> örneği oluşturan satırdır. Kod, <xref:System.Text.StringBuilder> uygulamasındaki `sb.ToString()` ve iç ayırmaların ayrılmasına neden olur, ancak dize sonucunu istiyorsanız bu ayırmaları kontrol edebilirsiniz. 
  
 **Örneğin 4 için çözüm**  
  
 `StringBuilder` nesne ayırmayı onarmak için nesneyi önbelleğe alma. Oluşan tek bir örneği önbelleğe almak bile, performansı önemli ölçüde iyileştirebilir. Bu, yeni ilk ve son satırlar hariç tüm kodu atlayarak işlevin yeni uygulamasıdır:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Anahtar parçalar yeni `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` işlevleridir:  
  
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
  
 Yeni derleyiciler iş parçacığı kullandığından, bu uygulamalar <xref:System.Text.StringBuilder>önbelleğe almak için bir iş parçacığı statik alanı (<xref:System.ThreadStaticAttribute> özniteliği) kullanır ve büyük olasılıkla `ThreadStatic` bildirimine geçebilirsiniz. Thread-static alanı, bu kodu yürüten her iş parçacığı için benzersiz bir değer tutar. 
  
 `AcquireBuilder()`, varsa, önbelleğe alınmış <xref:System.Text.StringBuilder> örneğini döndürür, temizlemeden sonra alanı veya önbelleği null olarak ayarlar. Aksi takdirde, `AcquireBuilder()` yeni bir örnek oluşturup, alan veya önbelleği null olarak bırakarak bu örneği döndürür. 
  
 <xref:System.Text.StringBuilder> ile işiniz bittiğinde, dize sonucunu almak için `GetStringAndReleaseBuilder()` çağırır, <xref:System.Text.StringBuilder> örneğini alan veya önbellekte kaydedin ve sonra sonucu geri döndürün. Yürütmenin bu kodu yeniden girmesi ve birden çok <xref:System.Text.StringBuilder> nesne oluşturmak (nadiren gerçekleşse de) mümkündür. Kod, daha sonra kullanılmak üzere yalnızca son yayınlanan <xref:System.Text.StringBuilder> örneğini kaydeder. Bu basit önbelleğe alma stratejisi, yeni derleyicilerde ayırmaları önemli ölçüde düşürür. .NET Framework ve MSBuild 'in ("MSBuild") bölümleri, performansı artırmak için benzer bir teknik kullanır. 
  
 Bu basit önbelleğe alma stratejisi, boyut üst sınırı içerdiğinden iyi önbellek tasarımına uyar. Ancak, artık orijinalden daha fazla kod vardır. Bu, daha fazla bakım maliyeti anlamına gelir. Önbelleğe alma stratejisini yalnızca bir performans sorunu bullediyseniz benimsemelisiniz ve PerfView <xref:System.Text.StringBuilder> ayırmaların önemli bir katkı olduğunu göstermiştir. 
  
### <a name="linq-and-lambdas"></a>LINQ ve Lambdalar  
Lambda ifadeleriyle birlikte, dil ile tümleşik sorgu (LINQ), üretkenlik özelliğine bir örnektir. Ancak, kullanımı zaman içinde performans üzerinde önemli bir etkiye sahip olabilir ve kodunuzu yeniden yazmanız gerektiğini fark edebilirsiniz.
  
 **Örnek 5: Lambdalar, List\<T > ve IEnumerable\<T >**  
  
 Bu örnek, bir ad dizesi verildiğinde derleyicinin modelinde bir sembol bulmak için [LINQ ve işlevsel stil kodu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) kullanır:  
  
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
  
 Yeni derleyici ve IDE deneyimleri, `FindMatchingSymbol()` çok sık çağrı üzerine oluşturulmuştur ve bu işlevin tek satırında birkaç gizli ayırma bulunur. Bu ayırmaları incelemek için, önce işlevin tek satırlık kod satırını iki satıra ayırın:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 İlk satırda, [lambda ifadesi](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` yerel değişken `name`[üzerinde kapanır](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) . Yani, `predicate` [temsil](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) için bir nesne ayırmanın yanı sıra kod, `name`değerini yakalayan ortamı tutmak için statik bir sınıf ayırır. Derleyici, aşağıdaki gibi bir kod üretir:  
  
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
  
 İki `new` ayırma (ortam sınıfı ve diğeri temsilci için bir tane) artık açıktır. 
  
 Şimdi `FirstOrDefault`çağrısına bakın. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> türündeki bu genişletme yöntemi çok fazla tahsisat doğurur. `FirstOrDefault` ilk bağımsız değişkeni olarak bir <xref:System.Collections.Generic.IEnumerable%601> nesnesi alacağından, aşağıdaki koda yapılan çağrıyı genişletebilirsiniz (bir tartışmaya yönelik bir bit basitleştirilmiştir):  
  
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
  
 `symbols` değişkeni tür <xref:System.Collections.Generic.List%601>. <xref:System.Collections.Generic.List%601> koleksiyon türü <xref:System.Collections.Generic.IEnumerable%601> uygular ve Cleverly, <xref:System.Collections.Generic.List%601> `struct`uygulayan bir Numaralandırıcı (<xref:System.Collections.Generic.IEnumerator%601> arabirimi) tanımlar. Sınıf yerine bir yapı kullanılması, genellikle atık toplama performansını etkileyebilecek yığın ayırmalarının önüne geçmek anlamına gelir. Numaralandırıcılar genellikle, çağrı yığınında döndürüldüğünden Numaralandırıcı yapısını kullanan dilin `foreach` döngüsüyle kullanılır. Bir nesne için yer açmak üzere çağrı yığını işaretçisinin arttırılmasının, yığın ayırma yöntemi GC 'yi etkilemez. 
  
 Genişletilmiş `FirstOrDefault` çağrısı durumunda kodun bir <xref:System.Collections.Generic.IEnumerable%601>`GetEnumerator()` çağırması gerekir. `IEnumerable<Symbol>` türündeki `enumerable` değişkenine `symbols` atamak, gerçek nesnenin bir <xref:System.Collections.Generic.List%601>olduğu bilgileri kaybeder. Bu, kod numaralandırıcıyı `enumerable.GetEnumerator()`aldığında, .NET Framework `enumerator` değişkenine atamak için döndürülen yapıya sahip olması gerektiği anlamına gelir. 
  
 **5. örnek için çözüm**  
  
 Bu, `FindMatchingSymbol`, tek satırlık kod satırını, hala net, okunması ve anlaşılması kolay ve bakımını yapmak kolay olan altı satırlık kodla değiştirerek aşağıdaki gibi yeniden yazmaktır:  
  
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
  
 Bu kod LINQ uzantı yöntemleri, Lambdalar veya Numaralandırıcılar kullanmaz ve hiçbir ayırma yapmaz. Derleyici `symbols` koleksiyonun bir <xref:System.Collections.Generic.List%601> olduğunu görebildiğinden ve ortaya çıkan Numaralandırıcı (bir yapı), kutulamayı önlemek için doğru türe sahip bir yerel değişkene bağlayabildiğinden hiçbir ayırma yoktur. Bu işlevin orijinal sürümü C# ve .NET Framework verimliliği hakkında harika bir örnektir. Bu yeni ve daha verimli sürüm, sürdürmek için herhangi bir karmaşık kod eklemeden bu nitelikleri korur. 
  
### <a name="async-method-caching"></a>Zaman uyumsuz metot önbelleğe alma  

Sonraki örnek, önbelleğe alınmış sonuçları [zaman uyumsuz](../../csharp/programming-guide/concepts/async/index.md) bir yöntemde kullanmaya çalıştığınızda yaygın bir sorunu gösterir.
  
 **Örnek 6: zaman uyumsuz metotlarda önbelleğe alma**  
  
 New C# ve Visual Basic derleyicileri üzerinde oluşturulan VISUAL Studio IDE özellikleri genellikle sözdizimi ağaçlarını getirir ve derleyiciler, Visual Studio 'yu yanıt vermeye devam etmek için zaman uyumsuz olarak kullanır. Bir sözdizimi ağacı almak için, yazmanız gerekebilecek kodun ilk sürümü aşağıda verilmiştir:  
  
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
  
 Çağıran `GetSyntaxTreeAsync()` bir `Parser`örnekleyen, kodu ayrıştırdığı ve sonra `Task<SyntaxTree>`<xref:System.Threading.Tasks.Task> nesnesini döndüren görebilirsiniz. Pahalı bölüm `Parser` örneği tahsis etme ve kodu ayrıştırma. Bu işlev, çağıranların ayrıştırma işini bekleme ve kullanıcı girişine yanıt vermek için UI iş parçacığını boşaltabilmesi için bir <xref:System.Threading.Tasks.Task> döndürür. 
  
 Birçok Visual Studio özelliği aynı sözdizimi ağacını almayı deneyebilir, bu nedenle zaman ve ayırmaları kaydetmek için ayrıştırma sonucunu önbelleğe almak üzere aşağıdaki kodu yazabilirsiniz. Ancak, bu kod bir ayırma doğurur:  
  
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
  
 Önbelleğe alma ile yeni kodun `cachedResult`adlı bir `SyntaxTree` alanı olduğunu görürsünüz. Bu alan null olduğunda, `GetSyntaxTreeAsync()` işi yapar ve sonucu önbelleğe kaydeder. `GetSyntaxTreeAsync()` `SyntaxTree` nesnesini döndürür. Sorun, `Task<SyntaxTree>`türünde bir `async` işleviniz olduğunda ve `SyntaxTree`türünde bir değer döndürdüğünüzde, derleyicinin sonucu tutmak için bir görev ayırmak üzere kod yayar (`Task<SyntaxTree>.FromResult()`kullanarak). Görev tamamlandı olarak işaretlenir ve sonuç hemen kullanılabilir. Yeni derleyicilerin kodunda, zaten tamamlanmış olan <xref:System.Threading.Tasks.Task> nesneler, genellikle bu ayırmaları düzeltme hızını önemli ölçüde düzeltmeye yönelik olarak oluşmuştur. 
  
 **Örnek 6**  
  
 Tamamlanan <xref:System.Threading.Tasks.Task> ayırmayı kaldırmak için, görev nesnesini tamamlanan sonuçla önbelleğe alabilirsiniz:  
  
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
  
 Bu kod, `cachedResult` türünü `Task<SyntaxTree>` olarak değiştirir ve `GetSyntaxTreeAsync()`orijinal kodu tutan bir `async` yardımcı işlevi kullanır. `GetSyntaxTreeAsync()` artık null olmayan `cachedResult` döndürmek için [null birleştirme işlecini](../../csharp/language-reference/operators/null-coalescing-operator.md) kullanmaktadır. `cachedResult` null ise, `GetSyntaxTreeAsync()` çağırır `GetSyntaxTreeUncachedAsync()` ve sonucu önbelleğe alır. Kod normal olarak `GetSyntaxTreeAsync()` `GetSyntaxTreeUncachedAsync()` çağrısını beklediğine dikkat edin. Await kullanılması `GetSyntaxTreeUncachedAsync()` <xref:System.Threading.Tasks.Task> nesnesini döndürdüğünde `GetSyntaxTreeAsync()` hemen <xref:System.Threading.Tasks.Task>döndüren anlamına gelir. Şimdi önbelleğe alınmış sonuç bir <xref:System.Threading.Tasks.Task>olduğundan, önbelleğe alınmış sonucu döndürecek bir ayırma yoktur. 
  
### <a name="additional-considerations"></a>Ek hususlar  
 Büyük uygulamalarda veya çok sayıda veriyi işleyen uygulamalarda olası sorunlar hakkında daha fazla noktaya yer verilmiştir. 
  
 **Sözlüğü**  
  
 Sözlüklerde çok sayıda programda her ikisi de kullanılır, ancak sözlüklerde çok kullanışlı ve doğal olarak etkilidir. Ancak, bunlar genellikle uygun şekilde kullanılır. Visual Studio ve yeni derleyiciler ' de analiz, sözlüklerin çoğunun tek bir öğe içerdiğini veya boş olduğunu gösterir. Boş bir <xref:System.Collections.Generic.Dictionary%602> on alana sahiptir ve bir x86 makinesindeki yığında 48 bayt kaplar. Sözlük, sabit zamanlı arama ile bir eşleme veya ilişkilendirilebilir veri yapısına ihtiyacınız olduğunda harika. Ancak yalnızca birkaç öğe varsa, bir sözlük kullanarak çok fazla alan duydum. Bunun yerine, örneğin, hızlı bir şekilde bir `List<KeyValuePair\<K,V>>`arasında gezinmeniz de yeterlidir. Bir sözlüğü yalnızca verileri kullanarak yüklemek ve bundan sonra (çok yaygın bir düzende) okumak için kullanırsanız, bir N (günlük (N)) arama ile sıralanmış bir diziyi kullanmak, kullanmakta olduğunuz öğelerin sayısına bağlı olarak neredeyse hızlı olabilir. 
  
 **Sınıflar ve yapılar**  
  
 Bir şekilde, sınıflar ve yapılar, uygulamalarınızı ayarlamak için klasik bir alan/saat zorunluluğunu getirir sağlar. Sınıflar bir x86 makinesinde alan olmasa bile 12 baytlık ek yük sağlar, ancak yalnızca bir sınıf örneğine başvurmak için bir işaretçi kullandığından, bunlara geçiş yapmak pahalı değildir. Yapılar, kutulamadıklarında yığın ayırmaları oluşturmaz, ancak büyük yapıları işlev bağımsız değişkenleri veya dönüş değerleri olarak geçirdiğinizde, yapıların tüm veri üyelerini otomatik olarak kopyalamak için CPU süresi sürer. Yapıları döndüren özelliklere yapılan yinelenen çağrılar için izleyin ve aşırı veri kopyalamayı önlemek için özelliğin değerini yerel bir değişkende önbelleğe koyun. 
  
 **Caches**  
  
 Yaygın bir performans eli, sonuçları önbelleğe almak için kullanılır. Ancak, boyut Cap veya çıkarma ilkesi olmayan bir önbellek bellek sızıntısı olabilir. Büyük miktarlarda verileri işlerken önbellekler üzerinde çok fazla bellek tutarsanız, çöp toplamanın önbelleğe alınmış aramalarınızın avantajlarını geçersiz kılmasına neden olabilirsiniz. 
  
 Bu makalede, özellikle büyük miktarda veri işleyen büyük sistemler veya sistemler için uygulamanızın yanıt hızını etkileyebilecek performans sorunu belirtilerini nasıl anlamış olursunuz. Ortak külekler kutulama, dize işlemeleri, LINQ ve lambda, zaman uyumsuz metotlarda önbelleğe alma, boyut sınırı veya aktiften çıkarma ilkesi olmadan önbelleğe alma, uygunsuz sözlüklerin kullanımı ve yapıların etrafında geçiş içerir. Uygulamalarınızı ayarlamaya yönelik dört olgu göz önünde bulundurun:  
  
- , Sorunsuz bir şekilde iyileştirmeyin; sorunları belirlediğinizde uygulamanızı üretken yapın ve ayarlayın. 
  
- Profiller yok – ölçmeniz durumunda tahmin edersiniz. 
  
- İyi araçlar, tüm farkları yapar – PerfView 'ı indirin ve deneyin. 
  
- Bu, her zaman, derleyici platformu ekibinin yeni derleyicilerin performansını en iyi şekilde harcadığı bir ayırdır. 
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bu konunun sunumunun videosu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Performans Profili Oluşturma Başlangıç Kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Performans](index.md)
- [.NET performans Ipuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Channel 9 PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [.NET Compiler Platform SDK 'Sı](../../csharp/roslyn-sdk/index.md)
- [GitHub 'da DotNet/Roslyn deposu](https://github.com/dotnet/roslyn)
