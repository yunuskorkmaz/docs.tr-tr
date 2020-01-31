---
title: Parametre Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 78eb07503810e75d14bcd73740fe429e2f73475e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743669"
---
# <a name="parameter-design"></a>Parametre tasarımı

Bu bölüm, bağımsız değişkenleri denetlemeye yönelik yönergeleri içeren bölümler dahil olmak üzere parametre tasarımı hakkında kapsamlı yönergeler sağlar. Ayrıca, [adlandırma parametrelerinde](../../../docs/standard/design-guidelines/naming-parameters.md)açıklanan yönergelere başvurmalısınız.

 ✔️, üyenin gerektirdiği işlevselliği sağlayan en az türetilmiş parametre türünü kullanır.

 Örneğin, bir koleksiyonu tasarlandıran ve her öğeyi konsola yazdıran bir yöntem tasarlamak istediğinizi varsayalım. Bu tür bir yöntem, örneğin <xref:System.Collections.ArrayList> veya <xref:System.Collections.IList>değil parametre olarak <xref:System.Collections.IEnumerable> almalıdır.

 ❌ ayrılmış parametreleri kullanmayın.

 Daha sonraki bir sürümde bir üyeye daha fazla giriş gerekiyorsa, yeni bir aşırı yükleme eklenebilir.

 ❌, işaretçi, işaretçi dizileri veya çok boyutlu dizileri parametre olarak alan genel kullanıma açık yöntemlere sahip DEĞILDIR.

 İşaretçiler ve çok boyutlu diziler düzgün şekilde kullanılması nispeten zordur. Neredeyse tüm durumlarda, bu türleri parametre olarak almayı önlemek için API 'Ler yeniden dağıtılabilir.

 ✔️, tüm `out` parametrelerini tüm değer ve `ref` parametrelerine (parametre dizileri hariç) izleyerek, aşırı yüklemeler arasındaki parametre sıralaması içinde tutarsızlığa neden olsa bile (bkz. [üye aşırı yüklemesi](../../../docs/standard/design-guidelines/member-overloading.md)).

 `out` parametreler ek dönüş değerleri olarak görülebilir ve bunları birlikte gruplandırmak yöntem imzasının anlaşılması daha kolay hale gelir.

 ✔️, Üyeler geçersiz kılınırken veya arabirim üyeleri uygularken adlandırma parametrelerinde tutarlıdır.

 Bu, Yöntemler arasındaki ilişkiyi daha iyi bir şekilde iletir.

### <a name="choose-between-enum-and-boolean-parameters"></a>Enum ve Boole parametreleri arasında seçim yapın
 ✔️, bir üyenin iki veya daha fazla Boole parametresine sahip olması halinde numaralandırmalar kullanın.

 iki değerden daha fazla değere gerek olmadığından kesinlikle emin olmadığınız müddetçe, ❌ Boolean kullanmayın.

 Numaralandırmalar, daha sonra değerlerin eklenmesi için bir yer sağlar, ancak [enum tasarımında açıklanan numaralandırıcılara](../../../docs/standard/design-guidelines/enum.md)değer eklemenin tüm etkilerine dikkat etmeniz gerekir.

 ✔️, gerçekten iki durumlu değerler olan Oluşturucu parametreleri için Boolean kullanmayı düşünün ve yalnızca Boole özelliklerini başlatmak için kullanılır.

### <a name="validate-arguments"></a>Bağımsız değişkenleri doğrula
 ✔️ ortak, korumalı veya açıkça uygulanmış üyelere geçirilen bağımsız değişkenleri doğrular. Doğrulama başarısız olursa, <xref:System.ArgumentException?displayProperty=nameWithType>veya alt sınıflarından birini oluşturun.

 Gerçek doğrulamanın ortak veya korumalı üyenin kendisinde olması gerekmediğini unutmayın. Bu, bazı özel veya iç bir yordamın daha düşük bir düzeyinde gerçekleşecektir. Ana nokta, son kullanıcılara sunulan tüm yüzey alanının bağımsız değişkenleri denetlemesini sağlar.

 null bir bağımsız değişken geçirilirse ve üye null bağımsız değişkenleri desteklemiyorsa ✔️ <xref:System.ArgumentNullException> throw.

 Enum parametrelerini doğrulamak ✔️.

 Enum bağımsız değişkenlerinin enum tarafından tanımlanan aralıkta olacağını varsaymayın. CLR, değer numaralandırmasında tanımlanmasa bile herhangi bir tamsayı değerini bir sabit listesi değerine dönüştürmeyi sağlar.

 ❌ enum Aralık denetimleri için <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> kullanmayın.

 ✔️, kesilebilir bağımsız değişkenlerin doğrulandıktan sonra değişmiş olabileceğini unutmayın.

 Üye güvenliğe duyarlı ise, bir kopya yapmanız ve sonra bağımsız değişkeni doğrulamanız ve işlemesi önerilir.

### <a name="pass-parameters"></a>Parametreleri geçir
 Bir çerçeve tasarımcısının perspektifinden, üç temel parametre grubu vardır: değere göre parametreler, `ref` parametreleri ve `out` parametreleri.

 Bir bağımsız değişken bir by değeri parametresiyle geçirildiğinde, üye geçirilen gerçek bağımsız değişkenin bir kopyasını alır. Bağımsız değişken bir değer türü ise, bağımsız değişkenin bir kopyası yığına konur. Bağımsız değişken bir başvuru türü ise, başvurunun bir kopyası yığına konur. C#, Visual Basic, ve C++gibi en popüler CLR dilleri değere göre parametreleri geçirmek için varsayılan değer.

 Bir bağımsız değişken bir `ref` parametresi aracılığıyla geçirildiğinde, üye geçirilen gerçek bağımsız değişkene bir başvuru alır. Bağımsız değişken bir değer türü ise, yığına bağımsız değişkene bir başvuru konur. Bağımsız değişken bir başvuru türü ise, bir başvuruya başvuru, yığına konur. `Ref` parametreler, üyenin çağıran tarafından geçirilen bağımsız değişkenleri değiştirmesine izin vermek için kullanılabilir.

 `Out` parametreler, bazı küçük farklılıklar ile `ref` parametrelere benzerdir. Parametre başlangıçta atanmamış olarak kabul edilir ve bir değer atanmadan önce üye gövdesinde okunamaz. Ayrıca, parametreye, üyenin döndürdüğü bir değere atanmalıdır.

 `out` veya `ref` parametreleri kullanmaktan kaçının ❌.

 `out` veya `ref` parametrelerinin kullanılması işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeriyle yöntemleri işleme. Ayrıca, `out` ve `ref` parametreleri arasındaki fark yaygın olarak anlaşılmaz. Genel bir hedef kitle için tasarlayan çerçeve mimarları, kullanıcıların `out` veya `ref` parametreleriyle birlikte çalışmasını beklememelidir.

 ❌ başvuru türlerini başvuruya göre geçirmez.

 Kural için, başvuruları değiştirmek için kullanılabilecek bir yöntem gibi bazı sınırlı özel durumlar vardır.

### <a name="members-with-variable-number-of-parameters"></a>Değişken parametre sayısı olan Üyeler
 Değişken sayıda bağımsız değişken alan Üyeler, bir dizi parametresi sağlayarak ifade edilir. Örneğin, <xref:System.String> aşağıdaki yöntemi sağlar:

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 Daha sonra bir Kullanıcı <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemini aşağıdaki şekilde çağırabilir:

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 C# Params anahtar sözcüğünü bir dizi parametresine eklemek, parametreyi bir so adlı params dizi parametresine değiştirir ve geçici bir dizi oluşturmak için bir kısayol sağlar.

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 Bunu yapmak, kullanıcının dizi öğelerini doğrudan bağımsız değişken listesinde geçirerek yöntemi çağırmasını sağlar.

 `String.Format("File {0} not found in {1}",filename,directory);`

 Params anahtar sözcüğünün yalnızca parametre listesindeki son parametreye eklenebileceğini unutmayın.

 Son kullanıcıların dizileri az sayıda öğe ile geçmesini bekleseniz, dizi parametrelerine params anahtar sözcüğünü eklemeyi düşünün ✔️. Yaygın senaryolarda çok sayıda öğenin geçirilmesi bekleniyorsa, kullanıcılar muhtemelen bu öğeleri de satır içine geçirmeyecektir ve bu nedenle params anahtar sözcüğü gerekli değildir.

 ❌, arayan girişi neredeyse her zaman bir dizide zaten olacaksa params dizilerini kullanmaktan kaçının.

 Örneğin, bayt dizi parametrelerine sahip Üyeler tek tek baytlar ileterek neredeyse hiçbir şekilde çağrılmaz. Bu nedenle, .NET Framework bayt dizi parametreleri params anahtar sözcüğünü kullanmaz.

 ❌, dizi params dizi parametresini alan üye tarafından değiştirilmişse params dizilerini kullanmayın.

 Birçok derleyicilerin bağımsız değişkenlerini çağrı sitesinde geçici bir diziye değiştirdiğinden, dizi geçici bir nesne olabilir ve bu nedenle dizideki tüm değişiklikler kaybedilir.

 daha karmaşık bir aşırı yükleme bunu kullanmasa bile, bir basit aşırı yüklemede params anahtar sözcüğünü kullanmayı düşünün ✔️.

 Tüm aşırı yüklerde olmasa bile kullanıcılar bir aşırı yüklemede params dizisine sahip olacaksa kendinize sorun.

 ✔️ params anahtar sözcüğünü kullanmayı olanaklı kılmak için parametreleri sipariş etmek için deneyin.

 ✔️ Son derece performans duyarlı API 'lerde çok sayıda bağımsız değişkene sahip çağrılar için özel aşırı yüklemeler ve kod yolları sağlamayı düşünün.

 Bu, API, az sayıda bağımsız değişkenle çağrıldığında dizi nesneleri oluşturmaktan kaçınılmasını mümkün kılar. Parametre adlarını, dizi parametresinin tekil bir biçimini alarak ve sayısal bir sonek ekleyerek oluşturur.

 Bunu yalnızca bir dizi oluşturun ve daha genel yöntemi çağırmak için kod yolunun tamamına özel durum oluşturacaksanız yapmanız gerekir.

 ✔️, null bir params Array bağımsız değişkeni olarak geçirilebileceğini unutmayın.

 İşlemeden önce dizinin null olduğunu doğrulamanız gerekir.

 ❌, üç nokta olarak da bilinen `varargs` yöntemlerini kullanmaz.

 Gibi bazı CLR dilleri C++, `varargs` Yöntemler adlı değişken parametre listelerinin geçirilmesi için alternatif bir kural destekler. Bu kural, CLS uyumlu olmadığından çerçeve içinde kullanılmamalıdır.

### <a name="pointer-parameters"></a>İşaretçi parametreleri
 Genel olarak, işaretçiler iyi tasarlanmış bir yönetilen kod çerçevesinin genel yüzey alanında görünmemelidir. Çoğu zaman işaretçiler kapsüllenmelidir. Ancak bazı durumlarda, birlikte çalışabilirlik nedenleriyle işaretçiler gereklidir ve bu gibi durumlarda işaretçiler kullanılması uygundur.

 ✔️, işaretçiler CLS uyumlu olmadığından, işaretçi bağımsız değişkeni alan tüm Üyeler için bir alternatif sağlar.

 ❌ işaretçi bağımsız değişkenlerinin pahalı bağımsız değişken denetimini yapmaktan KAÇıNıN.

 ✔️ işaretçileri olan üyeleri tasarlarken, işaretçiyle ilgili genel kuralları izleyin.

 Örneğin, başlangıç dizinini geçirmeniz gerekmez, çünkü basit işaretçi aritmetiği aynı sonucu elde etmek için kullanılabilir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
