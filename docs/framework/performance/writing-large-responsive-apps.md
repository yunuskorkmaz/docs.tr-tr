---
title: Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180576"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma

Bu makalede, büyük .NET Framework uygulamalarının veya dosya veya veritabanları gibi büyük miktarda veriyi işleyen uygulamaların performansını artırmak için ipuçları verilmektedir. Bu ipuçları yönetilen kodc# ve Visual Basic derleyicilerini yeniden yazmaktan gelir ve bu makalede C# derleyicisinden birkaç gerçek örnek içerir.
  
.NET Framework, uygulama oluşturmak için son derece verimlidir. Güçlü ve güvenli diller ve zengin bir kütüphane koleksiyonu, uygulama oluşturmayı son derece verimli hale getirsin. Ancak, büyük verimlilik ile sorumluluk geliyor. .NET Framework'ün tüm gücünü kullanmalısınız, ancak gerektiğinde kodunuzu izlemeye hazır olmalısınız.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Yeni derleyici performansı uygulamanız için neden geçerlidir?  
 .NET Derleyici Platformu ("Roslyn") ekibi, kodu modellemek ve analiz etmek, araçlar oluşturmak ve Visual Studio'da çok daha zengin, kod bilincine duyarlı deneyimler sağlamak için yeni API'ler sağlamak için yönetilen koddaki C# ve Visual Basic derleyicilerini yeniden yazdı. Derleyicileri yeniden yazmak ve yeni derleyiciler üzerinde Visual Studio deneyimleri oluşturmak, herhangi bir büyük .NET Framework uygulaması veya çok fazla veriyi işleyen herhangi bir uygulama için geçerli olan yararlı performans öngörülerini ortaya çıkardı. C# derleyicisinden gelen kavrayışve örneklerden yararlanmak için derleyiciler hakkında bilgi edinmeniz gerekmez.
  
 Visual Studio, tanımlayıcıların ve anahtar kelimelerin renklendirilmesi, sözdizimi tamamlama listeleri, hatalar için dalgalandırmalar, parametre ipuçları, kod sorunları ve kod eylemleri gibi kullanıcıların sevdiği tüm IntelliSense özelliklerini oluşturmak için derleyici API'lerini kullanır. Visual Studio, geliştiriciler kodlarını yazarken ve değiştirirken bu yardımı sağlar ve derleyici kod geliştiricilerin ini sürekli olarak modellerken Visual Studio'nun yanıt layıcı olarak kalması gerekir.
  
 Son kullanıcılarınız uygulamanızla etkileşimde ne zaman yanıt vermesini beklerler. Yazma veya komut işleme asla engellenmemelidir. Kullanıcı yazmaya devam ederse yardım hızlı bir şekilde açılır veya vazgeçmelidir. Uygulamanız, uygulamanın kendini yavaş hissetmesini sağlayan uzun hesaplamalarla UI iş parçacığının engellenmesini önlemelidir.
  
 Roslyn derleyicileri hakkında daha fazla bilgi için [.NET Derleyici Platformu SDK'ya](../../csharp/roslyn-sdk/index.md)bakın.
  
## <a name="just-the-facts"></a>Sadece Gerçekler  
 Performansı alarken ve duyarlı .NET Framework uygulamaları oluştururken bu gerçekleri göz önünde bulundurun.
  
### <a name="fact-1-dont-prematurely-optimize"></a>Gerçek 1: Zamanından önce optimize etmeyin  
 Olması gerekenden daha karmaşık kod yazma, bakım, hata ayıklama ve parlatma maliyetlerine neden olur. Deneyimli programcılar, kodlama sorunlarını nasıl çözeceklerine ve daha verimli kodlar yazabilmek için sezgisel bir kavrayışa sahiptir. Ancak, bazen kodlarını zamanından önce optimize ederler. Örneğin, basit bir dizi yeterli olduğunda karma tablo kullanırlar veya değerleri yeniden hesaplamak yerine bellek sızdırabilecek karmaşık önbelleğe alma kullanırlar. Deneyim programcısı olsanız bile, performans için test etmeli ve sorunları bulduğunuzda kodunuzu çözümlemelisiniz.
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Gerçek 2: Eğer ölçüm değilseniz, tahmin ediyoruz  
 Profiller ve ölçümler yalan söylemez. Profiller, CPU'nun tam yüklü olup olmadığını veya disk G/Ç'de engellenip engellenmediğinizi gösterir. Profiller, ne tür ve ne kadar bellek ayırdığınızı ve CPU'nuzun [çöp toplamada](../../standard/garbage-collection/index.md) (GC) çok zaman harcayıp harcamadığınızı söyler.
  
 Uygulamanızdaki önemli müşteri deneyimleri veya senaryolar için performans hedefleri belirlemeli ve performansı ölçmek için testler yazmalısınız. Bilimsel yöntemi uygulayarak başarısız testleri araştırın: size rehberlik etmek için profilleri kullanın, sorunun ne olabileceğini varsayılın ve hipotezinizi bir deneme veya kod değişikliğiyle test edin. Düzenli sınama ile zaman içinde temel performans ölçümleri belirleyin, böylece performansta gerilemelere neden olan değişiklikleri yalıtabilirsiniz. Performans çalışmalarına titiz bir şekilde yaklaşarak, gerek duymadığınız kod güncelleştirmeleriyle zaman kaybından kurtulursunuz.
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Gerçek 3: İyi araçlar tüm fark yaratmak  
 İyi araçlar, en büyük performans sorunlarını (CPU, bellek veya disk) hızla çözmenize ve bu darboğazlara neden olan kodu bulmanıza yardımcı olur. Microsoft, [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) ve [PerfView](https://www.microsoft.com/download/details.aspx?id=28567)gibi çeşitli performans araçları ile gönderilmiştir.
  
 PerfView, disk G/Ç, GC olayları ve bellek gibi derin sorunlara odaklanmanıza yardımcı olan ücretsiz ve inanılmaz derecede güçlü bir araçtır. Windows (ETW) olayları için performansla ilgili [Olay İzleme'yi](../wcf/samples/etw-tracing.md) yakalayabilir ve uygulama başına, işlem başına, yığın başına ve iş parçacığı bilgisi başına kolayca görüntüleyebilirsiniz. PerfView, uygulamanızın ne kadar ve ne tür bellek ayırdığını ve hangi işlevlerin veya çağrı yığınlarının bellek ayırmalarına ne kadar katkıda bulunur. Ayrıntılar için, araca dahil olan zengin yardım konularına, demolara ve videolara bakın (Kanal 9'daki [PerfView eğitimleri](https://channel9.msdn.com/Series/PerfView-Tutorial) gibi).
  
### <a name="fact-4-its-all-about-allocations"></a>Gerçek 4: Her şey tahsisatlarla ilgili  
 Duyarlı bir .NET Framework uygulaması oluşturmanın, kabarcık sıralaması yerine hızlı sıralama kullanmak gibi algoritmalarla ilgili olduğunu düşünebilirsiniz, ancak durum böyle değildir. Duyarlı bir uygulama oluşturmanın en büyük nedeni, özellikle uygulamanız çok büyükse veya büyük miktarda veri işlediğinde bellek ayırmaktır.
  
 Yeni derleyici API'leri ile duyarlı IDE deneyimleri oluşturmak için yapılan çalışmaların neredeyse tamamı, tahsisatlardan kaçınmayı ve önbelleğe alma stratejilerini yönetmeyi içeriyordu. PerfView izleri, yeni C# ve Visual Basic derleyicilerinin performansının nadiren CPU'ya bağlı olduğunu gösterir. Derleyiciler yüz binlerce veya milyonlarca kod satırı okurken, meta verileri okurken veya oluşturulan kodu yayırken G/Ç'ye bağlı olabilir. UI iş parçacığı gecikmeleri neredeyse tüm çöp toplama nedeniyle. .NET Framework GC performans için son derece ayarlanmıştır ve uygulama kodu yürütülürken çalışmalarının çoğunu aynı anda yapar. Ancak, tek bir ayırma tüm iş parçacığı durdurarak pahalı bir [gen2](../../standard/garbage-collection/fundamentals.md) toplama tetikleyebilir.
  
## <a name="common-allocations-and-examples"></a>Ortak ayırmalar ve örnekler  
 Bu bölümdeki örnek ifadeler, küçük görünen gizli ayırmalara sahiptir. Ancak, büyük bir uygulama ifadeleri yeterince kez yürütürse, yüzlerce megabayt, hatta gigabayt, ayırmalara neden olabilir. Örneğin, bir geliştiricinin düzenleyicideki yazısını simüle eden bir dakikalık testler gigabaytlarzaman bellek ayırmış ve performans ekibinin senaryo yazmaya odaklanmasına yol açmıştır.
  
### <a name="boxing"></a>Kutulama  
 [Kutulama,](../../csharp/programming-guide/types/boxing-and-unboxing.md) normalde yığında veya veri yapılarında yaşayan değer türleri bir nesneye sarılınca oluşur. Diğer bir tarihte, verileri tutmak için bir nesne ayırırsınız ve ardından bir işaretçiyi nesneye döndürebilirsiniz. .NET Framework bazen bir yöntemin imzası veya depolama konumunun türü nedeniyle değerleri kutular. Bir nesnedeki değer türünü sarma, bellek ayırmaya neden olur. Birçok boks işlemi, uygulamanıza megabaytlarca veya gigabaytlık tahsisatlar sağlayabilir, bu da uygulamanızın daha fazla GC'ye neden olacağı anlamına gelir. .NET Framework ve dil derleyicileri mümkün olduğunda kutulamaktan kaçınır, ancak bazen en az beklediğiniz anda olur.
  
 PerfView'da boksu görmek için bir izleme açın ve uygulamanızın işlem adı altında GC Heap Alloc Yığınları'na bakın (unutmayın, tüm süreçler hakkında PerfView raporları). Tahsisatlar gibi <xref:System.Int32?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> ve altında türleri görüyorsanız, değer türlerini kutulup alasınız. Bu türlerden birini seçmek, kutulu oldukları yığınları ve işlevleri gösterir.
  
 **Örnek 1: dize yöntemleri ve değer türü bağımsız değişkenleri**  
  
 Bu örnek kod, gereksiz ve aşırı kutulama yı göstermektedir:  
  
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
  
 Bu kod günlük işlevselliği sağlar, `Log` böylece bir uygulama işlevi sık sık, belki de milyonlarca kez arayabilir. Sorun şu ki, `string.Format` aşırı yükleme <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> için giderilmesi için çağrı.
  
 Bu aşırı yük, `int` .NET Framework'ün değerleri nesnelere kutulayarak bu yöntem çağrısına geçirmesini gerektirir. Kısmi düzeltme, tüm `id.ToString()` `size.ToString()` dizeleri (nesne olan) `string.Format` aramaya çağırmak ve geçirmektir. Arama `ToString()` bir dize ayırır, ancak bu `string.Format`ayırma zaten içinde olur.
  
 Bu temel çağrının `string.Format` sadece dize biraraya getirin, bu nedenle bu kodu yazabilirsiniz:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Ancak, bu kod satırı bir kutulama ayırma <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>sı derlediği için. .NET Framework, çağrılması için karakter in ivel kutusunu kutulamalıdır`Concat`  
  
 **Örneğin 1'i düzeltme**  
  
 Tam düzeltme basittir. Dizeleri zaten nesneler olduğundan hiçbir kutulama tahakkuk eden bir dize literal ile karakter literal değiştirin:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Örnek 2: enum boks**  
  
 Bu örnek, özellikle sözlük arama işlemlerinde numaralandırma türlerinin sık kullanımı nedeniyle yeni C# ve Visual Basic derleyicilerinde büyük miktarda ayırmadan sorumluydu.
  
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
  
 Bu sorun çok ince. PerfView bunu kutulama olarak <xref:System.Enum.GetHashCode> bildirir, çünkü yöntem, uygulama nedenleriyle numaralandırma türünün temel temsilini kutular. PerfView'e yakından bakarsanız, her arama için iki kutulama <xref:System.Enum.GetHashCode>ayırması görebilirsiniz. Derleyici birini ekler, .NET Framework diğerini ekler.
  
 **Örneğin 2'yi düzeltme**  
  
 Aşağıdakileri aramadan <xref:System.Enum.GetHashCode>önce altta yatan temsile döküm yaparak her iki ayırmayı da kolayca önleyebilirsiniz:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Numaralandırma türlerinde bir diğer yaygın boks <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> kaynağı da yöntemdir. Geçirilen <xref:System.Enum.HasFlag%28System.Enum%29> argüman kutulanmalıdır. Çoğu durumda, çağrıları bitwise testi <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> ile değiştirmek daha basit ve tahsisat gerektirmez.
  
 İlk performans gerçeğini aklınızda tutun (diğer bir deyişle, zamanından önce optimize etmeyin) ve tüm kodunuzu bu şekilde yeniden yazmaya başlamayın. Bu boks maliyetlerine dikkat edin, ancak kodunuzu yalnızca uygulamanızın profilini çıkardıktan ve önemli noktaları bulduktan sonra değiştirin.
  
### <a name="strings"></a>Dizeler  
 Dize manipülasyonları tahsisatların en büyük suçlularından bazılarıdır ve genellikle perfView'da ilk beş ayırmada ortaya çıkar. Programlar serileştirme, JSON ve REST API'leri için dizeleri kullanır. Dizileri, numaralandırma türlerini kullanamadığınızda sistemlerle etkileşim için programlı sabitler olarak kullanabilirsiniz. Profil oluşturmanız dizelerin performansı son derece etkilediğini <xref:System.String> gösterdiğinde, <xref:System.String.Format%2A> <xref:System.String.Concat%2A>, <xref:System.String.Split%2A> <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, , gibi yöntemlere yapılan çağrıları arayın. Birçok <xref:System.Text.StringBuilder> parçadan bir dize oluşturma maliyetini önlemek için kullanarak <xref:System.Text.StringBuilder> yardımcı olur, ancak nesne tahsis bile yönetmek için gereken bir darboğaz haline gelebilir.
  
 **Örnek 3: dize işlemleri**  
  
 C# derleyicisi biçimlendirilmiş bir XML doc yorum metnini yazan bu kodvardı:  
  
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
  
 Bu kodun çok fazla dize manipülasyonu yaptığını görebilirsiniz. Kod, satırları ayrı dizeleri bölmek, beyaz alanı kırpmak, bağımsız `text` değişkenin XML belge yorumu olup olmadığını denetlemek ve satırlardan alt dizeleri ayıklamak için kitaplık yöntemleri kullanır.
  
 İçerideki `WriteFormattedDocComment`ilk satırda, `text.Split` çağrı, her çağrıldığında bağımsız değişken olarak yeni bir üç öğeli dizi ayırır. Derleyici, bu diziyi her seferinde ayırmak için kod yontmak zorundadır. Bunun nedeni, derleyicinin diziyi <xref:System.String.Split%2A> dizinin başka bir kod tarafından değiştirilebileceği bir yerde depolayıp depolar, bu da daha sonraki çağrıları etkileyip etkilemediğini bilmiyor `WriteFormattedDocComment`olmasıdır. Çağrı <xref:System.String.Split%2A> da her satır için bir `text` dize ayırır ve işlemi gerçekleştirmek için diğer bellek ayırır.
  
 `WriteFormattedDocComment`<xref:System.String.TrimStart%2A> yönteme üç çağrı vardır. İki, çalışmayı ve ayırmaları yineleyen iç döngülerdedir. Daha da kötüsü, <xref:System.String.TrimStart%2A> hiçbir bağımsız değişken ile yöntem arama `params` dize sonucu ek olarak boş bir dizi (parametre için) ayırır.
  
 Son olarak, genellikle yeni <xref:System.String.Substring%2A> bir dize ayıran yönteme bir çağrı vardır.
  
 **Örneğin 3'e göre düzeltme**  
  
 Önceki örneklerin aksine, küçük düzeltmeler bu ayırmaları düzeltemez. Geri çekilip, soruna bakmalı ve farklı bir yaklaşım sergilemelisin. Örneğin, bağımsız değişkenin yöntemin `WriteFormattedDocComment()` ihtiyaç duyduğu tüm bilgilere sahip bir dize olduğunu fark edeceksiniz, böylece kod çok sayıda kısmi dize ayırmak yerine daha fazla dizin oluşturma yapabilir.
  
 Derleyicinin performans ekibi tüm bu ayırmaları şu gibi kodla ele almıştır:  
  
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
  
 Bir dizi, `WriteFormattedDocComment()` birkaç alt dizeleri ve boş `params` bir dizi ile birlikte kesilmiş bir alt dize tahsis ilk sürümü. Ayrıca "/"'' diye de kontrol edildi. Gözden geçirilen kod yalnızca dizine ayırma kullanır ve hiçbir şey ayırmaz. Beyaz boşluk olmayan ilk karakteri bulur ve ardından dize "//" ile başlayıp başlamadığını görmek için karakteri karaktere göre denetler. Yeni kod, `IndexOfFirstNonWhiteSpaceChar` beyaz <xref:System.String.TrimStart%2A> olmayan bir alanın oluştuğu ilk dizini (belirli bir başlangıç dizininden sonra) döndürmek yerine kullanır. Düzeltme tamamlanmadı, ancak tam bir çözüm için benzer düzeltmeleri nasıl uygulayacağınızı görebilirsiniz. Bu yaklaşımı kod boyunca uygulayarak, 'deki `WriteFormattedDocComment()`tüm ayırmaları kaldırabilirsiniz.
  
 **Örnek 4: StringBuilder**  
  
 Bu örnekte <xref:System.Text.StringBuilder> bir nesne kullanır. Aşağıdaki işlev genel türleri için tam bir tür adı oluşturur:  
  
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
  
 Odak yeni bir <xref:System.Text.StringBuilder> örnek oluşturur satırüzerindedir. Kod, <xref:System.Text.StringBuilder> uygulama içinde `sb.ToString()` bir ayırma ve iç ayırmalara neden olur, ancak dize sonucunu istiyorsanız bu ayırmaları denetleyemezsiniz.
  
 **Örneğin 4'e göre düzeltme**  
  
 Nesne ayırmayı `StringBuilder` düzeltmek için nesneyi önbelleğe edin. Çöpe atılabilecek tek bir örneği önbelleğe almak bile performansı önemli ölçüde artırabilir. Bu, işlevin yeni ilk ve son satırlar dışında tüm kodu atlayarak yeni uygulamasıdır:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Önemli parçalar yeni `AcquireBuilder()` ve `GetStringAndReleaseBuilder()` fonksiyonlar şunlardır:  
  
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
  
 Yeni derleyiciler iş parçacığı kullandığından, bu uygulamalar bir<xref:System.ThreadStaticAttribute> iş parçacığı statik <xref:System.Text.StringBuilder>alanı (öznitelik) önbellek için kullanır ve büyük olasılıkla `ThreadStatic` bildirimi bırakabilirsiniz. İş parçacığı statik alan, bu kodu çalıştıran her iş parçacığı için benzersiz bir değer tutar.
  
 `AcquireBuilder()`önbelleğe alınan <xref:System.Text.StringBuilder> örneği, temizledikten ve alanı veya önbelleği null'a ayarladıktan sonra döndürür. Aksi `AcquireBuilder()` takdirde, yeni bir örnek oluşturur ve alanı veya önbelleği null olarak bırakarak döndürür.
  
 İşi <xref:System.Text.StringBuilder> bittiğinde, dize `GetStringAndReleaseBuilder()` sonucunu almak için ararsınız, <xref:System.Text.StringBuilder> örneği alana veya önbelleğe kaydedin ve sonra sonucu döndürün. Yürütmenin bu kodu yeniden girmesi ve birden <xref:System.Text.StringBuilder> çok nesne oluşturması mümkündür (ancak bu nadiren olur). Kod, daha sonra kullanılmak <xref:System.Text.StringBuilder> üzere yalnızca son yayımlanan örneği kaydeder. Bu basit önbelleğe alma stratejisi, yeni derleyicilerde ayırmaları önemli ölçüde azalttı. .NET Framework ve MSBuild 'in ("MSBuild") parçaları performansı artırmak için benzer bir teknik kullanır.
  
 Bu basit önbelleğe alma stratejisi, boyut kapağına sahip olduğundan iyi önbellek tasarımına bağlıdır. Ancak, şimdi orijinalinden daha fazla kod var, bu da daha fazla bakım maliyeti anlamına geliyor. Önbelleğe alma stratejisini yalnızca bir performans sorunu bulduysanız ve PerfView <xref:System.Text.StringBuilder> ayırmaların önemli bir katkıda bulunduğunu göstermiştir.
  
### <a name="linq-and-lambdas"></a>LINQ ve lambdas  
Dil-Entegre Sorgu (LINQ), lambda ifadeleri ile birlikte, bir verimlilik özelliği bir örnektir. Ancak, kullanımı zaman içinde performans üzerinde önemli bir etkiye sahip olabilir ve kodunuzu yeniden yazmanız gerektiğini görebilirsiniz.
  
 **Örnek 5: Lambdas, Liste\<T> ve\<Imumerable T>**  
  
 Bu örnek, derleyicinin modelinde bir ad dizesi verilen bir simge bulmak için [LINQ ve işlevsel stil kodunu](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) kullanır:  
  
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
  
 Yeni derleyici ve üzerinde yerleşik IDE `FindMatchingSymbol()` deneyimleri çok sık çağrı ve bu işlevin tek kod satırında birkaç gizli ayırmalar vardır. Bu ayırmaları incelemek için, önce işlevin tek kod satırını iki satıra bölün:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 İlk satırda [lambda ifadesi](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` yerel `name` [değişkenin üzerinde kapanır.](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) Bu, `predicate` bir nesneyi tutan [temsilciye](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) ayırmanın yanı sıra, kodun `name`değerini yakalayan ortamı tutmak için statik bir sınıf ayırdığı anlamına gelir. Derleyici aşağıdaki gibi kod oluşturur:  
  
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
  
 İki `new` ayırma (biri çevre sınıfı için, diğeri temsilci için) şimdi açık.
  
 Şimdi çağrıya `FirstOrDefault`bak. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Türdeki bu uzantı yöntemi de bir ayırmaya neden oluyor. Bir `FirstOrDefault` nesneyi <xref:System.Collections.Generic.IEnumerable%601> ilk bağımsız değişkeni olarak aldığından, aramayı aşağıdaki koda genişletebilirsiniz (tartışma için biraz basitleştirilmiş):  
  
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
  
 Değişkenin `symbols` türü <xref:System.Collections.Generic.List%601>vardır. Koleksiyon <xref:System.Collections.Generic.List%601> türü uygular <xref:System.Collections.Generic.IEnumerable%601> ve akıllıca bir<xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.Generic.List%601> `struct`ile uygulayan bir bir sayısallaştırıcı (arabirim) tanımlar . Sınıf yerine bir yapı kullanmak, genellikle çöp toplama performansını etkileyebilecek yığın ayırmalardan kaçınmanız anlamına gelir. Tümumeratörler genellikle çağrı yığınında `foreach` döndürülür gibi enumerator yapısını kullanan dilin döngü ile kullanılır. Bir nesneye yer açmak için çağrı yığını işaretçisini artımlı yorum, yığın ayırmanın yaptığı gibi GC'yi etkilemez.
  
 Genişletilmiş `FirstOrDefault` arama söz konusu olduğunda, kodun `GetEnumerator()` bir <xref:System.Collections.Generic.IEnumerable%601>. Tür `IEnumerable<Symbol>` `symbols` değişkenine `enumerable` atama, gerçek nesnenin bir <xref:System.Collections.Generic.List%601>. Bu, kod, .NET `enumerable.GetEnumerator()`Framework'ün döndürülen yapıyı `enumerator` değişkene atamak için kutuya takması gerektiği anlamına gelir.
  
 **Örneğin 5'i düzeltme**  
  
 Düzeltme, tek kod `FindMatchingSymbol` satırını hala kısa, okunması ve anlaşılması kolay ve bakımı kolay altı kod satırıyla değiştirerek aşağıdaki gibi yeniden yazmaktır:  
  
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
  
 Bu kod LINQ uzantı yöntemleri, lambdas veya numaralandırıcılar kullanmaz ve hiçbir ayırma ya da yok. Derleyici koleksiyonun `symbols` a <xref:System.Collections.Generic.List%601> olduğunu görebildiği ve elde edilen enumerator'u (yapı) kutulamayı önlemek için doğru türe sahip yerel bir değişkene bağlayabildiği için ayırma yoktur. Bu işlevin özgün sürümü, C#'ın ifade gücünün ve .NET Framework'ün üretkenliğinin harika bir örneğiydi. Bu yeni ve daha verimli sürüm korumak için herhangi bir karmaşık kod eklemeden bu nitelikleri korur.
  
### <a name="async-method-caching"></a>Async yöntemi önbelleğe alma  

Sonraki örnek, önbelleğe alınmış sonuçları bir [async](../../csharp/programming-guide/concepts/async/index.md) yönteminde kullanmaya çalıştığınızda sık karşılaşılan bir sorun gösterir.
  
 **Örnek 6: async yöntemleri önbelleğe alma**  
  
 Visual Studio IDE özellikleri yeni C# ve Visual Basic derleyicileri sık sık sözdizimi ağaçlarını getirir ve derleyiciler Visual Studio'yu duyarlı tutmak için bunu yaparken async kullanır. Sözdizimi ağacı almak için yazabileceğiniz kodun ilk sürümü aşağıda veda edebilirsiniz:  
  
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
  
 Aramanın `GetSyntaxTreeAsync()` kodu `Parser`parlataya verdiğini ve sonra bir <xref:System.Threading.Tasks.Task> nesneyi `Task<SyntaxTree>`döndürttürün, Pahalı kısmı `Parser` örneği tahsis ve kodu ayrıştırma olduğunu. İşlev, <xref:System.Threading.Tasks.Task> arayanların ayrışma çalışmasını bekleyebileceği ve Kullanıcı İçi'nin kullanıcı girişine yanıt verebileceği kullanıcı iş parçacığının serbest bırakılabilmeleri için bir yanıt verir.
  
 Çeşitli Visual Studio özellikleri aynı sözdizimi ağacını almayı deneyebilir, bu nedenle zaman ve ayırmalardan tasarruf etmek için ayrışma sonucunu önbelleğe almak için aşağıdaki kodu yazabilirsiniz. Ancak, bu kod bir ayırma yatiran:  
  
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
  
 Önbelleğe alınmış yeni kodun `SyntaxTree` bir `cachedResult`alanı olduğunu görüyorsunuz. Bu alan null `GetSyntaxTreeAsync()` olduğunda, işi yapar ve önbellekte sonucu kaydeder. `GetSyntaxTreeAsync()`nesneyi `SyntaxTree` döndürür. Sorun şu ki, bir `async` tür `Task<SyntaxTree>`işleviniz olduğunda ve bir `SyntaxTree`tür değeri döndürdüğünde, derleyici sonucu tutmak için bir `Task<SyntaxTree>.FromResult()`Görev ayırmak için kod yayır (kullanarak). Görev tamamlanmış olarak işaretlenir ve sonuç hemen kullanılabilir. Yeni derleyicilerin kodunda, <xref:System.Threading.Tasks.Task> zaten tamamlanmış olan nesneler o kadar sık oluştu ki, bu ayırmaları düzeltme, yanıt verme yeteneğini belirgin şekilde artırdı.
  
 **Örneğin 6'yı düzeltme**  
  
 Tamamlanan <xref:System.Threading.Tasks.Task> ayırmayı kaldırmak için Görev nesnesini tamamlanan sonuçla önbelleğe alabilirsiniz:  
  
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
  
 Bu kod, `cachedResult` 'nin `Task<SyntaxTree>` türünü değiştirir `async` ve özgün kodu ' `GetSyntaxTreeAsync()`dan tutan bir yardımcı işlev kullanır. `GetSyntaxTreeAsync()`null değilse dönmek `cachedResult` için null [coalescing operatör](../../csharp/language-reference/operators/null-coalescing-operator.md) kullanır. Null `cachedResult` ise, `GetSyntaxTreeAsync()` o `GetSyntaxTreeUncachedAsync()` zaman aramaları ve sonucu önbelleğe alın. Kodun `GetSyntaxTreeAsync()` normalde yapacağı `GetSyntaxTreeUncachedAsync()` gibi aramayı beklemediğini unutmayın. Beklemeyi kullanmamak, `GetSyntaxTreeUncachedAsync()` <xref:System.Threading.Tasks.Task> `GetSyntaxTreeAsync()` nesnesini döndürdüğünde <xref:System.Threading.Tasks.Task>hemen 'yi döndürür. Şimdi, önbelleğe alınmış <xref:System.Threading.Tasks.Task>sonuç , önbelleğe alınmış sonucu döndürmek için hiçbir ayırmalar vardır.
  
### <a name="additional-considerations"></a>Diğer konular  
 Burada, çok fazla veriyi işleyen büyük uygulamalarda veya uygulamalarda olası sorunlarla ilgili birkaç nokta daha verilmiştir.
  
 **Sözlükler**  
  
 Sözlükler birçok programda her yerde kullanılır ve sözlükler çok kullanışlı ve doğal olarak verimli olmasına rağmen. Ancak, genellikle uygunsuz kullanılır. Visual Studio ve yeni derleyicilerde, analizler sözlüklerin çoğunun tek bir öğe içerdiğini veya boş olduğunu göstermektedir. Bir <xref:System.Collections.Generic.Dictionary%602> boş on alanları vardır ve bir x86 makine üzerinde yığın üzerinde 48 bayt kaplar. Sözlükler, sabit zamanlı arama ile bir eşleme veya etkieltif veri yapısı gerektiğinde harikadır. Ancak, yalnızca birkaç öğeniz olduğunda, sözlük kullanarak çok fazla yer harcarsınız. Bunun yerine, örneğin, yinelemeli bir `List<KeyValuePair\<K,V>>`üzerinden bakabilirsiniz , gibi hızlı. Bir sözlüğü yalnızca verilerle yüklemek için kullanıyorsanız ve sonra ondan (çok yaygın bir desen) okursanız, kullandığınız öğe sayısına bağlı olarak N(log(N)) araması içeren sıralanmış bir dizi kullanmak neredeyse aynı kadar hızlı olabilir.
  
 **Sınıflar ve yapılar**  
  
 Bir bakıma, sınıflar ve yapılar uygulamalarınızı aparat etmek için klasik bir alan/zaman dengelemesi sağlar. Sınıflar, alanları olmasa bile x86 makinesinde 12 bayt ek yükü nelerdir, ancak yalnızca bir sınıf örneğine başvurmak için bir işaretçi gerektirdiğinden, geçici olarak dolaşmak ucuzdur. Yapılar kutulu değilseniz yığın ayırması yapmaz, ancak işlev bağımsız değişkenleri veya döndürme değerleri olarak büyük yapıları geçtiğizde, yapıların tüm veri üyelerini atomik olarak kopyalamak CPU'nun zaman ını alır. Yapıları döndüren özelliklere yapılan tekrarlanan çağrılara dikkat edin ve aşırı veri kopyalamayı önlemek için özelliğin değerini yerel bir değişkende önbelleğe alın.
  
 **Caches**  
  
 Yaygın bir performans hilesi sonuçları önbelleğe almaktır. Ancak, boyut sınırı veya imha ilkesi olmayan bir önbellek bellek sızıntısı olabilir. Büyük miktarda veriyi işlerken, önbelleklerde çok fazla belleğe tutunursanız, önbelleğe alınan aramalarınızın avantajlarını geçersiz kılmak için çöp toplamaişlemine neden olabilirsiniz.
  
 Bu makalede, özellikle büyük miktarda veriyi işleyen büyük sistemler veya sistemler için uygulamanızın yanıt verme yeteneğini etkileyebilecek performans darboğaz belirtilerine nasıl dikkat edilmesi gerektiğini tartıştık. Ortak suçlular boks, dize manipülasyonları, LINQ ve lambda, async yöntemleri önbelleğe alma, bir boyut sınırı veya bertaraf politikası olmadan önbelleğe alma, sözlüklerin uygunsuz kullanımı ve yapıların etrafında niçin geçilmesidir. Uygulamalarınızı alaişletmeniz için dört gerçek olduğunu unutmayın:  
  
- Erken optimize etmeyin – üretken olun ve sorunları fark ettiğinizde uygulamanızı ayarlayın.
  
- Profiller yalan söylemez – ölçüm yapmıyorsanız tahmin edeyim.
  
- İyi araçlar tüm fark yaratmak - PerfView indirin ve deneyin.
  
- Her şey tahsisatlarla ilgilidir – derleyici platformu ekibinin zamanlarının çoğunu yeni derleyicilerin performansını artırmak için harcadığı yerdir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bu konunun sunumu video](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Yeni Başlayanlar Performans Profilleme Rehberi](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Performans](index.md)
- [.NET Performans İpuçları](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Kanal 9 PerfView eğitimleri](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [.NET Derleyici Platformu SDK](../../csharp/roslyn-sdk/index.md)
- [GitHub üzerinde dotnet/roslyn repo](https://github.com/dotnet/roslyn)
