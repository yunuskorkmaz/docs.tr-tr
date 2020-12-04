---
title: Performans kuralları (kod analizi)
description: Kod Analizi performans kuralları hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- rules, performance
- performance rules
- performance, rules
- managed code analysis rules, performance rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 4409cc46eb73f13f8e59d7a51899da27035bb6af
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96588818"
---
# <a name="performance-rules"></a>Performans kuralları

Performans kuralları yüksek performanslı kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Açıklama |
| - | - |
| [CA1802: Uygun yerlerde sabitleri kullanın](ca1802.md) | Bir alan statik ve salt okunur olarak tanımlanır (Visual Basic paylaşılan ve salt okunur) ve derleme zamanında oluşturulabilir bir değer ile başlatılır. Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, değeri bir const (const Visual Basic) alanı olarak değiştirin, böylece değer çalışma zamanı yerine derleme zamanında hesaplanır. |
| [CA1805: Gerekmediği durumlarda başlatmayın](ca1805.md) | .NET çalışma zamanı, oluşturucuyu çalıştırmadan önce, başvuru türlerindeki tüm alanları varsayılan değerlerine başlatır. Çoğu durumda, bir alanı varsayılan değerine açıkça başlatmak, bakım maliyetlerine eklenen ve performansı düşürebilir (örneğin, daha fazla derleme boyutuyla). |
| [CA1806: Metot sonuçlarını yoksaymayın](ca1806.md) | Yeni bir nesne oluşturulur, ancak hiçbir zaman kullanılmaz veya yeni bir dize oluşturan ve döndüren bir yöntem çağrılır ve yeni dize hiçbir zaman kullanılmaz veya bir bileşen nesne modeli (COM) ya da P/Invoke yöntemi hiçbir zaman kullanılmayan bir HRESULT veya hata kodu döndürür. |
| [CA1810: Başvuru türü statik alanları satır içinden başlatın](ca1810.md) | Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik oluşturucu denetimleri performansı düşürebilir. |
| [CA1812: Örneklenmemiş iç sınıflardan kaçının](ca1812.md) | Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz. |
| [CA1813: Mühürsüz özniteliklerden kaçının](ca1813.md) | .NET özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemleri öznitelik devralma hiyerarşisinde arar. Öznitelik mühürleme kalıtım hiyerarşisi aracılığıyla aramayı ortadan kaldırır ve performansı artırabilir. |
| [CA1814: Çok boyutlu diziler yerine basit dizileri tercih edin](ca1814.md) | Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri oluşturan diziler farklı boyutlarda olabilir ve bu da bazı veri kümeleri için daha az alana yol açabilir. |
| [CA1815: Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın](ca1815.md) | Değer türleri için, Equals'ın devralınmış uygulaması Reflection kitaplığını kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals'ı uygulamalıdır. |
| [CA1819: Özellikler diziler döndürmemelidir](ca1819.md) | Özellik salt okunurdur olsa bile, Özellikler tarafından döndürülen diziler yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. |
| [CA1820: Dize uzunluğunu kullanarak boş dizeleri test edin](ca1820.md) | String.Length özelliği veya String.IsNullOrEmpty yöntemi, Equals kullanılmasından önemli ölçüde daha hızlıdır. |
| [CA1821: Boş sonlandırıcıları kaldırın](ca1821.md) | Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Boş bir Sonlandırıcı, hiçbir avantaj olmadan ek yüke neden olur. |
| [CA1822: Üyeleri static olarak işaretleyin](ca1822.md) | Örnek verilerine veya çağrı örnek yöntemlerine erişmeyen Üyeler statik olarak işaretlenebilir (Visual Basic içinde paylaşılır). Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için verebilir. |
| [CA1823: Kullanılmayan özel alanlardan kaçının](ca1823.md) | Derlemede erişimi görülmeyen özel alanlar algılandı. |
| [CA1824: Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin](ca1824.md) | NeutralResourcesLanguage özniteliği, bir derleme için nötr kültürün kaynaklarını göstermek için kullanılan dilin Kaynak Yöneticisi bildirir. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir. |
| [CA1825: Sıfır uzunluklu dizi ayırmalarından kaçının](ca1825.md) | Sıfır uzunluklu bir diziyi başlatmak gereksiz bellek ayırmaya yol açar. Bunun yerine, çağırarak statik olarak ayrılan boş dizi örneğini kullanın <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Bellek ayırma, bu yöntemin tüm etkinleştirmeleri genelinde paylaşılır. |
| [CA1826: Linq Numaralandırma metodu yerine property kullan](ca1826.md) | <xref:System.Linq.Enumerable> LINQ yöntemi eşdeğer, daha verimli bir özelliği destekleyen bir tür üzerinde kullanıldı. |
| [CA1827: Any kullanılabiliyorsa Count/LongCount kullanma](ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> ya da yöntemi <xref:System.Linq.Enumerable.LongCount%2A> , <xref:System.Linq.Enumerable.Any%2A> yöntemin daha verimli olacağı yerde kullanılmıştır. |
| [CA1828: AnyAsync kullanılabiliyorsa CountAsync/LongCountAsync kullanma](ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> ya da yöntemi <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> , <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> yöntemin daha verimli olacağı yerde kullanılmıştır. |
| [CA1829: Enumerable.Count metodu yerine Length/Count özelliğini kullan](ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> LINQ yöntemi eşdeğer, daha etkin veya özelliği destekleyen bir tür üzerinde kullanıldı `Length` `Count` . |
| [CA1830: StringBuilder'da kesin tür belirtilmiş Append ve Insert metodu aşırı yüklemelerini tercih et](ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> ve <xref:System.Text.StringBuilder.Insert%2A> System. String 'in ötesinde birden çok tür için aşırı yüklemeler sağlar.  Mümkün olduğunda, ToString () ve dize tabanlı aşırı yüklemeyi kullanarak türü kesin belirlenmiş aşırı yüklemeleri tercih edin. |
| [CA1831: Uygun olduğunda dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın](ca1831.md) | Bir dizede Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak ReadOnlySpan &lt; char &gt; türüne atandığında, yöntemi <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizenin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| [CA1832: Bir dizinin ReadOnlySpan veya ReadOnlyMemory kısmını almak için Aralık tabanlı dizin oluşturucular yerine AsSpan ya da AsMemory kullanın](ca1832.md) | Bir dizide Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak bir <xref:System.ReadOnlySpan%601> veya <xref:System.ReadOnlyMemory%601> türüne atandığında, yöntemi <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizinin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| [CA1833: Bir dizinin Span veya Memory kısmını almak için Aralık tabanlı dizin oluşturucular yerine AsSpan ya da AsMemory kullanın](ca1833.md) | Bir dizide Aralık Dizin Oluşturucu kullanırken ve değeri örtük olarak bir <xref:System.Span%601> veya <xref:System.Memory%601> türüne atandığında, yöntemi <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , dizinin istenen bölümünün bir kopyasını üreten yerine kullanılır. |
| [CA1834: Tek karakterli dizeler için StringBuilder.Append(char) kullanın](ca1834.md) | <xref:System.Text.StringBuilder> , `Append` bağımsız değişkeni olarak bir olan aşırı yüküne sahiptir `char` . `char`Performansı artırmak için aşırı yüklemeyi çağırmayı tercih edin. |
| [CA1835: ' ReadAsync ' ve ' WriteAsync ' için ' Memory' tabanlı aşırı yüklemeleri tercih et](ca1835.md) | ' Stream ', &lt; &gt; ilk bağımsız değişken olarak ' bellek baytı ' ve &lt; &gt; ilk bağımsız değişken olarak ' readonlymemory byte ' olan bir ' WriteAsync ' aşırı yüklemesi olan ' ReadAsync ' aşırı yüklemesine sahip. Daha verimli olan bellek tabanlı aşırı yüklemeleri çağırmayı tercih edin. |
| [CA1836: `IsEmpty` `Count` kullanılabilir olduğunda tercih et](ca1836.md) | `IsEmpty` `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> Nesnenin bir öğe içerip içermediğini ya da olmadığını anlamak için, veya ' den daha verimli bir özellik tercih edin. |
| [CA1837: `Environment.ProcessId` yerine kullanın `Process.GetCurrentProcess().Id`](ca1837.md) | `Environment.ProcessId` daha basit ve daha hızlıdır `Process.GetCurrentProcess().Id` . |
| [CA1838: `StringBuilder` P/Invoke için parametrelerden kaçının](ca1838.md) | ' Nin sıralaması `StringBuilder` her zaman bir sıralama işlemi için birden çok ayırmaya neden olan yerel bir arabellek kopyası oluşturur. |
