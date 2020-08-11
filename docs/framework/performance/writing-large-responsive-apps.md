---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
description: Dosya veya veritabanları gibi büyük miktarda veriyi işleyen büyük, hızlı yanıt veren .NET uygulamaları veya uygulamalar yazın.
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a9f5d50ad78b2b0bef0ece3c4fce47d2925aca5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063763"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma

Bu makalede, büyük .NET Framework uygulamalarının veya dosyalar ya da veritabanları gibi büyük miktarda veriyi işleyen uygulamaların performansını iyileştirmeye yönelik ipuçları sunulmaktadır. Bu ipuçları, Yönetilen koddaki C# ve Visual Basic derleyicileri yeniden yazma işleminden gelir ve bu makale C# derleyicisinden birkaç gerçek örnek içerir.
  
.NET Framework uygulamalar oluşturmak için son derece üretken değildir. Güçlü ve güvenli diller ve zengin kitaplıkların bir koleksiyonu, uygulamanın yüksek düzeyde meyve özelliği olmasını kolaylaştırır. Bununla birlikte, harika üretkenlik sorumluluğu gelir. .NET Framework tüm gücünü kullanmanız gerekir, ancak gerektiğinde kodunuzun performansını ayarlamaya hazır olursunuz.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Yeni derleyici performansının neden uygulamanız için geçerli olduğu  
 .NET Compiler Platform ("Roslyn") ekibi, Visual Studio 'da kod modellemesi ve analiz etmek, araçlar oluşturmak ve çok daha zengin, kod duyarlı deneyimler sağlamak üzere yeni API 'Ler sağlamak için, Yönetilen koddaki C# ve Visual Basic derleyicilerini yeniden yazdı. Derleyicilerin yeniden oluşturulması ve yeni derleyicilerde Visual Studio deneyimleri oluşturmak, büyük .NET Framework uygulamaları veya çok sayıda veriyi işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörülerini ortaya çıkarmaktadır. C# derleyicisinden Öngörüler ve örneklerden yararlanmak için derleyiciler hakkında bilgi sahibi olmanız gerekmez.
  
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
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>3. olgu: Iyi araçlar tüm farkları yapar  
 İyi araçlar, en büyük performans sorunlarına (CPU, bellek veya disk) hızla göz atalım ve bu performans sorunlarına neden olan kodu bulmanıza yardımcı olur. Microsoft, [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)gibi çeşitli performans araçları ile birlikte sunulur.
  
 PerfView, disk g/ç, GC olayları ve bellek gibi derin sorunlara odaklanmanıza yardımcı olan ücretsiz ve başaramayabiliriz güçlü bir araçtır. Windows için performans ile ilgili [olay izleme](../wcf/samples/etw-tracing.md) (ETW) olaylarını yakalayabilir ve uygulama başına, işlem başına, yığın başına ve iş parçacığı bilgileri başına kolayca görüntüleyebilirsiniz. PerfView, uygulamanızın ne kadar ve ne tür bellek ayırdığını ve hangi işlevlerin veya çağrı yığınlarının bellek ayırmalarının ne kadar katkıda bulunduğunu gösterir. Ayrıntılar için bkz. araçla birlikte sunulan zengin yardım konuları, tanıtımlar ve videolar (örneğin, Channel 9 ' da [PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial) ).
  
### <a name="fact-4-its-all-about-allocations"></a>Olgu 4: tüm ayırmalar hakkında  
 Bir yanıt veren .NET Framework uygulamasının, kabarcık sıralaması yerine hızlı sıralama kullanma gibi algoritmaların hepsi olduğunu düşünebilirsiniz, ancak bu durum böyle değildir. Yanıt veren bir uygulama oluşturmanın en büyük faktörü, özellikle uygulamanız çok büyükse veya büyük miktarlarda veriyi işliyorsa bellek ayırmaktır.
  
 Ayırmaktan ve önbelleğe alma stratejilerinin yönetilmesine neden olan yeni derleyici API 'Leri ile yanıt veren IDE deneyimleri oluşturmaya yönelik neredeyse tüm çalışmalar. PerfView izlemeleri, yeni C# ve Visual Basic derleyicilerinin performansının nadiren CPU Ile bağlantılı olduğunu gösterir. Derleyiciler yüzlerce binlerce veya milyonlarca satırı okurken, meta verileri okurken veya üretilen kod yayırken g/ç bağlantılı olabilir. Kullanıcı arabirimi iş parçacığı gecikmeleri çöp toplama nedeniyle neredeyse hepsi olur. .NET Framework GC, performans için yüksek düzeyde ayarlanmıştır ve uygulama kodu yürütüldüğü sırada işinin çoğunu eşzamanlı olarak yapar. Ancak, tek bir ayırma pahalı bir [Gen2](../../standard/garbage-collection/fundamentals.md) koleksiyonunu tetikleyip tüm iş parçacıklarını durdurabilir.
  
## <a name="common-allocations-and-examples"></a>Ortak ayırmalar ve örnekler  
 Bu bölümdeki örnek ifadelerde küçük görünen gizli ayırmalar vardır. Ancak, büyük bir uygulama ifadeleri yeterince uzun bir şekilde yürütülüyorsa, yüzlerce megabayt, hatta gigabayt, hatta ayırmaya neden olabilir. Örneğin, düzenleyicide bir geliştiricinin yazı tipini uygulayan tek dakikalık testler, gigabayt bellek ayırmıştır ve performans ekibinin yazma senaryolarına odaklanmaya yol açmaktadır.
  
### <a name="boxing"></a>Kutulama  
 [Kutulama](../../csharp/programming-guide/types/boxing-and-unboxing.md) , normalde yığında veya veri yapılarında bulunan değer türleri bir nesneye sarmalandıktan sonra gerçekleşir. Yani, verileri tutacak bir nesne ayırırsınız ve sonra nesneye bir işaretçi döndürülür. .NET Framework bazen bir yöntemin imzası veya bir depolama konumu türü nedeniyle değerlere izin vermez. Bir nesne içindeki bir değer türünü sarmalama, bellek ayırmaya neden olur. Birçok paketleme işlemi uygulamanıza megabayt veya gigabayt 'lik ayırmaları katkıda bulunabilir, bu da uygulamanızın daha fazla GB 'a neden olacağı anlamına gelir. .NET Framework ve dil derleyicileri, mümkün olduğunda kutulamayı önler, ancak bazen en azından beklediğinde meydana gelir.
  
 PerfView içinde kutulamayı görmek için bir izleme açın ve uygulamanızın işlem adı altında GC yığın ayırma yığınlarına bakın (tüm süreçlerdeki PerfView raporlarını unutmayın). <xref:System.Int32?displayProperty=nameWithType>Ve <xref:System.Char?displayProperty=nameWithType> ayırma altında, gibi türler görürseniz, değer türlerini kutulanıyorsanız. Bu türlerden birini seçmek, paketlenmiş yığınları ve işlevleri gösterir.
  
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
  
 Bu kod günlüğe kaydetme işlevselliği sağlar; bu nedenle, bir uygulama `Log` çoğunlukla milyonlarca kez işlev çağırabilir. Sorun, `string.Format` aşırı yüklemeye çözümlenme çağrısının <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> .
  
 Bu aşırı yükleme, .NET Framework `int` Bu yöntem çağrısına iletmek için değerleri nesnelere eklemesini gerektirir. Kısmi bir çözüm, çağrı `id.ToString()` yapmak ve `size.ToString()` tüm dizeleri (nesneler) çağırmak ve geçirmek `string.Format` . Çağırma `ToString()` bir dize ayırır, ancak bu ayırma içinde de olur `string.Format` .
  
 Bu temel çağrının `string.Format` yalnızca dize birleştirmesi olduğunu düşünebilirsiniz, bu nedenle bunun yerine bu kodu yazabilirsiniz:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ancak, bu kod satırı, ' a derlendiğinden bir kutulama ayırmayı tanıtır <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29> . .NET Framework çağrılacak karakter sabit değerini Box olmalıdır`Concat`  
  
 **Örnek 1 için çözüm**  
  
 Tüm düzeltmeler basittir. Yalnızca karakter sabit değerini bir dize sabit değeri ile değiştirin, ancak dizeler zaten nesneler olduğundan kutulama yok:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Örnek 2: sabit listesi paketleme**  
  
 Bu örnek, özellikle sözlük arama işlemlerinde, sabit listesi türlerinin sık kullanılması nedeniyle yeni C# ve Visual Basic derleyicilerinin çok büyük bir ayırmasından sorumludur.
  
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
  
 Bu sorun çok daha hafif. <xref:System.Enum.GetHashCode>Yöntem, uygulama nedenleriyle numaralandırma türünün temel gösterimine bir kutu olduğundan PerfView bunu kutulama olarak raporlayabilir. PerfView 'a yakından bakarsanız, her bir çağrı için iki paketleme ayırması görebilirsiniz <xref:System.Enum.GetHashCode> . Derleyici bir tane ekler ve .NET Framework diğerini ekler.
  
 **Örneğin 2**  
  
 ' İ çağırmadan önce temeldeki temsilde kaldırarak her iki ayırmadan kolayca kaçınabilirsiniz <xref:System.Enum.GetHashCode> :  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Numaralandırma türlerinde başka bir ortak paketleme kaynağı <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> yöntemidir. Öğesine geçirilen bağımsız değişken <xref:System.Enum.HasFlag%28System.Enum%29> kutulanmış olmalıdır. Çoğu durumda, çağrıları <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bit düzeyinde bir test ile değiştirmek daha basit ve ayırma ücretsizdir.
  
 İlk performans olgusunu göz önünde bulundurun (yani, zamanından önce iyileştirmeyin) ve tüm kodunuzu bu şekilde yeniden yazmayı başlamayamazsınız. Bu paketleme maliyetlerinden haberdar olun, ancak yalnızca uygulamanızın profilini oluşturup etkin noktaları bulduktan sonra kodunuzu değiştirin.
  
### <a name="strings"></a>Dizeler  
 Dize işlemeleri, ayırmaların en büyük küllerinin bazılarıdır ve genellikle ilk beş tahsisde PerfView ' de görünür. Programlar serileştirme, JSON ve REST API 'Leri için dizeler kullanır. Sabit Listesi türlerini kullanamıyoruz, sistemlerle birlikte çalışmak için, dizeleri programlama sabitleri olarak kullanabilirsiniz. Profil oluşturma, dizelerin performansı yüksek oranda etkilediğini gösteriyorsa,,,, vb. gibi yöntemlere yönelik çağrılar olup olmadığına bakın <xref:System.String> <xref:System.String.Format%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A> <xref:System.String.Join%2A> <xref:System.String.Substring%2A> . <xref:System.Text.StringBuilder>Birçok parçadan bir dize oluşturma maliyetini önlemek için kullanmak yardımcı olur, ancak nesnenin tahsisi bile <xref:System.Text.StringBuilder> yönetmeniz gereken bir performans sorunu olabilir.
  
 **Örnek 3: dize işlemleri**  
  
 C# derleyicisi, biçimli bir XML belgesi açıklamasının metnini yazan bu koda sahipti:  
  
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
  
 Bu kodun çok sayıda dize düzenlemesi olduğunu görebilirsiniz. Kod, satırları ayrı dizelere bölmek, boşluk kırpmak, bağımsız değişkenin `text` BIR XML belgesi yorumu olup olmadığını denetlemek ve satırlardan alt dizeleri ayıklamak için kitaplık yöntemlerini kullanır.
  
 İçindeki ilk satırda `WriteFormattedDocComment` , `text.Split` çağrı her çağrıldığında bağımsız değişken olarak yeni bir üç öğeli dizi ayırır. Derleyicinin her seferinde bu diziyi ayırmak için kod yaymalıdır. Bunun nedeni, derleyicinin diziyi dizinin bir <xref:System.String.Split%2A> yere depoladığını, daha sonra öğesine yapılan çağrıları etkileyecek şekilde depolayabileceğini bilmez `WriteFormattedDocComment` . Ayrıca çağrısı, <xref:System.String.Split%2A> içindeki her satır için bir dize ayırır `text` ve işlemi gerçekleştirmek için diğer belleği ayırır.
  
 `WriteFormattedDocComment`yöntemine üç çağrı içerir <xref:System.String.TrimStart%2A> . İkisi de yinelenen iş ve ayırmaları yineleyen iç Döngülerde bulunur. Önemli hale getirmek için <xref:System.String.TrimStart%2A> bir bağımsız değişken olmadan yöntemi çağırmak, dize sonucuna ek olarak boş bir dizi ( `params` parametresi için) ayırır.
  
 Son olarak, <xref:System.String.Substring%2A> genellikle yeni bir dize ayıran yöntemine bir çağrı vardır.
  
 **3. örnekte çözüm**  
  
 Önceki örneklerden farklı olarak, küçük düzenlemeler bu ayırmaları düzeltemedi. Geri dönüp soruna bakmanız ve farklı bir yaklaşım yapmanız gerekir. Örneğin, bağımsız değişkeninin `WriteFormattedDocComment()` yöntemin ihtiyacı olan tüm bilgilere sahip bir dize olduğunu ve bu nedenle kodun çok sayıda kısmi dize ayırmak yerine daha fazla dizin oluşturulmasını sağlayabileceğini fark edersiniz.
  
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
  
 `WriteFormattedDocComment()`Boş bir dizi ile birlikte bir diziyi, birkaç alt dizeyi ve kırpılmış alt dizeyi ayırmış ilk sürümü `params` . Ayrıca "///" için kontrol edilir. Düzeltilen kod yalnızca dizin oluşturmayı kullanır ve hiçbir şey ayırır. Boşluk olmayan ilk karakteri bulur ve sonra dizenin "///" ile başlatılıp başlatılmadığını görmek için karaktere göre karakteri denetler. Yeni kod, boşluk `IndexOfFirstNonWhiteSpaceChar` <xref:System.String.TrimStart%2A> olmayan bir karakterin gerçekleştiği ilk dizini (belirtilen başlangıç dizininden sonra) döndürmek için yerine kullanır. Düzeltme tamamlanmaz, ancak tüm çözümler için benzer düzeltmelerin nasıl uygulanacağını görebilirsiniz. Bu yaklaşımı kodun tamamında uygulayarak içindeki tüm ayırmaları kaldırabilirsiniz `WriteFormattedDocComment()` .
  
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
  
 Odak, yeni bir örnek oluşturan satırdır <xref:System.Text.StringBuilder> . Kod, `sb.ToString()` uygulama içinde ve iç ayırmalar için bir ayırmaya neden olur <xref:System.Text.StringBuilder> , ancak dize sonucunu istiyorsanız bu ayırmaları kontrol edebilirsiniz.
  
 **Örneğin 4 için çözüm**  
  
 `StringBuilder`Nesne ayırmayı onarmak için nesneyi önbelleğe alma. Oluşan tek bir örneği önbelleğe almak bile, performansı önemli ölçüde iyileştirebilir. Bu, yeni ilk ve son satırlar hariç tüm kodu atlayarak işlevin yeni uygulamasıdır:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Anahtar parçalar yeni `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` işlevlerdir:  
  
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
  
 Yeni derleyiciler iş parçacığı kullandığından bu uygulamalar, önbelleğe almak için bir iş parçacığı statik alanı ( <xref:System.ThreadStaticAttribute> özniteliği) kullanır <xref:System.Text.StringBuilder> ve büyük olasılıkla `ThreadStatic` bildirime geçebilirsiniz. Thread-static alanı, bu kodu yürüten her iş parçacığı için benzersiz bir değer tutar.
  
 `AcquireBuilder()`<xref:System.Text.StringBuilder>bir tane varsa, onu temizleyip, alanı veya önbelleği null olarak ayarlayarak önbelleğe alınmış örneği döndürür. Aksi takdirde, `AcquireBuilder()` Yeni bir örnek oluşturur ve alan ya da önbelleğin null olarak ayarlanması için onu döndürür.
  
 İle işiniz bittiğinde <xref:System.Text.StringBuilder> , `GetStringAndReleaseBuilder()` dize sonucunu elde etmek için çağırın, <xref:System.Text.StringBuilder> örneği alan veya önbellekte kaydedin ve sonra sonucu geri döndürün. Yürütmenin bu kodu yeniden girmesi ve birden çok <xref:System.Text.StringBuilder> nesne oluşturmak (nadiren gerçekleşse de) mümkündür. Kod, <xref:System.Text.StringBuilder> daha sonra kullanılmak üzere yalnızca son yayınlanan örneği kaydeder. Bu basit önbelleğe alma stratejisi, yeni derleyicilerde ayırmaları önemli ölçüde düşürür. .NET Framework ve MSBuild 'in ("MSBuild") bölümleri, performansı artırmak için benzer bir teknik kullanır.
  
 Bu basit önbelleğe alma stratejisi, boyut üst sınırı içerdiğinden iyi önbellek tasarımına uyar. Ancak, artık orijinalden daha fazla kod vardır. Bu, daha fazla bakım maliyeti anlamına gelir. Önbelleğe alma stratejisini yalnızca bir performans sorunu bullediyseniz benimsemelisiniz ve PerfView, <xref:System.Text.StringBuilder> ayırmaların önemli bir katkı olduğunu göstermiştir.
  
### <a name="linq-and-lambdas"></a>LINQ ve Lambdalar  
Lambda ifadeleriyle birlikte, dil ile tümleşik sorgu (LINQ), üretkenlik özelliğine bir örnektir. Ancak, kullanımı zaman içinde performans üzerinde önemli bir etkiye sahip olabilir ve kodunuzu yeniden yazmanız gerektiğini fark edebilirsiniz.
  
 **Örnek 5: Lambdalar, List \<T> ve IEnumerable\<T>**  
  
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
  
 Yeni derleyici ve IDE deneyimleri, çok sık çağrı üzerine oluşturulmuştur `FindMatchingSymbol()` ve bu işlevin tek satırlık kod satırında birkaç gizli ayırma vardır. Bu ayırmaları incelemek için, önce işlevin tek satırlık kod satırını iki satıra ayırın:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 İlk satırda, [lambda ifadesi](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` yerel değişken [üzerinde kapanır](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) `name` . Diğer bir deyişle, tutan [temsilci](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) için bir nesne ayırmanın yanı sıra `predicate` , kod, değerini yakalayan ortamı tutmak için bir statik sınıf ayırır `name` . Derleyici, aşağıdaki gibi bir kod üretir:  
  
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
  
 İki `new` ayırma (ortam sınıfı için bir diğeri temsilci için bir tane) artık açıktır.
  
 Şimdi çağrısına bakın `FirstOrDefault` . Bu tür genişletme yöntemi <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> çok fazla bir ayırma doğurur. `FirstOrDefault` <xref:System.Collections.Generic.IEnumerable%601> , İlk bağımsız değişkeni olarak bir nesne kullandığından, aşağıdaki koda yapılan çağrıyı genişletebilirsiniz (bir tartışmaya yönelik bir bit Basitleştirilmiş):  
  
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
  
 `symbols`Değişkenin türü <xref:System.Collections.Generic.List%601> . <xref:System.Collections.Generic.List%601>Koleksiyon türü uygular <xref:System.Collections.Generic.IEnumerable%601> ve Cleverly, <xref:System.Collections.Generic.IEnumerator%601> ile uygulayan bir Numaralandırıcı (arabirim) tanımlar <xref:System.Collections.Generic.List%601> `struct` . Sınıf yerine bir yapı kullanılması, genellikle atık toplama performansını etkileyebilecek yığın ayırmalarının önüne geçmek anlamına gelir. Numaralandırıcılar genellikle `foreach` , çağrı yığınında döndürüldüğünden Numaralandırıcı yapısını kullanan dilin döngüsü ile kullanılır. Bir nesne için yer açmak üzere çağrı yığını işaretçisinin arttırılmasının, yığın ayırma yöntemi GC 'yi etkilemez.
  
 Genişletilmiş `FirstOrDefault` çağrı durumunda kodun bir üzerinde çağrı yapması gerekir `GetEnumerator()` <xref:System.Collections.Generic.IEnumerable%601> . `symbols` `enumerable` Türü değişkenine atama, `IEnumerable<Symbol>` gerçek nesnenin bir olduğu bilgileri kaybeder <xref:System.Collections.Generic.List%601> . Bu, kod numaralandırıcıyı ile aldığında `enumerable.GetEnumerator()` , .NET Framework değişkene atamak için döndürülen yapıyı Box ' a sahip olduğu anlamına gelir `enumerator` .
  
 **5. örnek için çözüm**  
  
 Bu çözüm aşağıdaki şekilde yeniden yazmak için `FindMatchingSymbol` , tek bir kod satırını, hala net, okunması ve anlaşılması kolay ve bakımı kolay olan altı satırlık kod ile değiştirir:  
  
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
  
 Bu kod LINQ uzantı yöntemleri, Lambdalar veya Numaralandırıcılar kullanmaz ve hiçbir ayırma yapmaz. Derleyici koleksiyonun bir olduğunu görebildiğinden `symbols` <xref:System.Collections.Generic.List%601> ve ortaya çıkan Numaralandırıcı (bir yapı), kutulamayı önlemek için doğru türe sahip yerel bir değişkene bağlayabildiğinden, hiçbir ayırma yoktur. Bu işlevin orijinal sürümü, C# ' nin ifade gücüne ve .NET Framework verimliliğine ilişkin harika bir örnektir. Bu yeni ve daha verimli sürüm, sürdürmek için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.
  
### <a name="async-method-caching"></a>Zaman uyumsuz metot önbelleğe alma  

Sonraki örnek, önbelleğe alınmış sonuçları [zaman uyumsuz](../../csharp/programming-guide/concepts/async/index.md) bir yöntemde kullanmaya çalıştığınızda yaygın bir sorunu gösterir.
  
 **Örnek 6: zaman uyumsuz metotlarda önbelleğe alma**  
  
 Yeni C# ve Visual Basic derleyicileri üzerinde oluşturulan Visual Studio IDE özellikleri genellikle sözdizimi ağaçlarını getirir ve derleyiciler, Visual Studio 'Yu yanıt vermeye devam etmek için zaman uyumsuz olarak kullanır. Bir sözdizimi ağacı almak için, yazmanız gerekebilecek kodun ilk sürümü aşağıda verilmiştir:  
  
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
  
 Çağıran `GetSyntaxTreeAsync()` bir örneği başlatır `Parser` , kodu ayrıştırır ve sonra bir <xref:System.Threading.Tasks.Task> nesnesi döndürür `Task<SyntaxTree>` . Pahalı parça `Parser` örneği ayırarak ve kodu ayrıştırır. Bu işlev, <xref:System.Threading.Tasks.Task> çağıranların ayrıştırma işini bekleme ve kullanıcı girişine yanıt vermek IÇIN UI iş parçacığını serbest verebilmeleri için bir döndürür.
  
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
  
 Önbelleğe alma ile yeni kodun adlı bir alan olduğunu görürsünüz `SyntaxTree` `cachedResult` . Bu alan null olduğunda, `GetSyntaxTreeAsync()` işi yapar ve sonucu önbelleğe kaydeder. `GetSyntaxTreeAsync()`nesneyi döndürür `SyntaxTree` . Bu sorun `async` , türünde bir işleviniz olduğunda `Task<SyntaxTree>` ve türünde bir değer döndürdüğünüzde `SyntaxTree` , derleyicinin sonucu tutmak için bir görev ayırmak üzere kod yayar (kullanarak `Task<SyntaxTree>.FromResult()` ). Görev tamamlandı olarak işaretlenir ve sonuç hemen kullanılabilir. Yeni derleyicilerin kodunda, <xref:System.Threading.Tasks.Task> zaten tamamlanmış olan nesneler, bu ayırmaları düzeltme hızını önemli ölçüde düzeltmeye yönelik olarak oluşmuştur.
  
 **Örnek 6**  
  
 Tamamlanan ayırmayı kaldırmak için <xref:System.Threading.Tasks.Task> , görev nesnesini tamamlanan sonuçla önbelleğe alabilirsiniz:  
  
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
  
 Bu kod, ' nin türünü `cachedResult` olarak değiştirir `Task<SyntaxTree>` ve `async` özgün kodu ' den tutan bir yardımcı işlevi kullanır `GetSyntaxTreeAsync()` . `GetSyntaxTreeAsync()`Şimdi null [birleştirme işlecini](../../csharp/language-reference/operators/null-coalescing-operator.md) kullanarak `cachedResult` null değilse döndürün. `cachedResult`Null ise, `GetSyntaxTreeAsync()` `GetSyntaxTreeUncachedAsync()` sonuçları çağırır ve önbelleğe alır. `GetSyntaxTreeAsync()` `GetSyntaxTreeUncachedAsync()` Genellikle kod olarak yapılan çağrıyı beklemez. Await kullanılması `GetSyntaxTreeUncachedAsync()` <xref:System.Threading.Tasks.Task> , nesnesini döndürdüğünde, hemen öğesini döndüren anlamına gelir `GetSyntaxTreeAsync()` <xref:System.Threading.Tasks.Task> . Şimdi önbelleğe alınmış sonuç bir olduğundan, <xref:System.Threading.Tasks.Task> önbelleğe alınmış sonucu döndürecek bir ayırma yoktur.
  
### <a name="additional-considerations"></a>Diğer konular  
 Büyük uygulamalarda veya çok sayıda veriyi işleyen uygulamalarda olası sorunlar hakkında daha fazla noktaya yer verilmiştir.
  
 **Sözlükler**  
  
 Sözlüklerde çok sayıda programda her ikisi de kullanılır, ancak sözlüklerde çok kullanışlı ve doğal olarak etkilidir. Ancak, bunlar genellikle uygun şekilde kullanılır. Visual Studio ve yeni derleyiciler ' de analiz, sözlüklerin çoğunun tek bir öğe içerdiğini veya boş olduğunu gösterir. Boş, <xref:System.Collections.Generic.Dictionary%602> on alana sahiptir ve bir x86 makinesindeki yığında 48 bayt kaplar. Sözlük, sabit zamanlı arama ile bir eşleme veya ilişkilendirilebilir veri yapısına ihtiyacınız olduğunda harika. Ancak yalnızca birkaç öğe varsa, bir sözlük kullanarak çok fazla alan duydum. Bunun yerine, örneğin, `List<KeyValuePair\<K,V>>` hızlı bir şekilde ' a kadar hızla göz atabilirsiniz. Bir sözlüğü yalnızca verileri kullanarak yüklemek ve bundan sonra (çok yaygın bir düzende) okumak için kullanırsanız, bir N (günlük (N)) arama ile sıralanmış bir diziyi kullanmak, kullanmakta olduğunuz öğelerin sayısına bağlı olarak neredeyse hızlı olabilir.
  
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
- [Performans profili oluşturma için yeni başlayanlar kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Performans](index.md)
- [.NET Performans İpuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Channel 9 PerfView öğreticileri](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [.NET Compiler Platform SDK 'Sı](../../csharp/roslyn-sdk/index.md)
- [GitHub 'da DotNet/Roslyn deposu](https://github.com/dotnet/roslyn)
