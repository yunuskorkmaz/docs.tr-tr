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
author: KrzysztofCwalina
ms.openlocfilehash: 28b00f5911bb47536ec44b96f284e47b6c671149
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353736"
---
# <a name="parameter-design"></a>Parametre Tasarımı
Bu bölüm, bağımsız değişkenleri denetlemeye yönelik yönergeleri içeren bölümler dahil olmak üzere parametre tasarımı hakkında kapsamlı yönergeler sağlar. Ayrıca, [adlandırma parametrelerinde](../../../docs/standard/design-guidelines/naming-parameters.md)açıklanan yönergelere başvurmalısınız.  
  
 **✓ DO** üyesi tarafından gerekli işlevselliği sağlayan en az türetilen parametre türü kullanın.  
  
 Örneğin, bir koleksiyonu tasarlandıran ve her öğeyi konsola yazdıran bir yöntem tasarlamak istediğinizi varsayalım. Bu tür bir yöntem, örneğin <xref:System.Collections.ArrayList> veya <xref:System.Collections.IList>değil parametre olarak <xref:System.Collections.IEnumerable> almalıdır.  
  
 **X DO NOT** ayrılmış parametrelerini kullanın.  
  
 Daha sonraki bir sürümde bir üyeye daha fazla giriş gerekiyorsa, yeni bir aşırı yükleme eklenebilir.  
  
 **X DO NOT** işaretçileri, işaretçileri dizileri ya da parametre olarak çok boyutlu diziler alırken yöntemleri genel olarak kullanıma.  
  
 İşaretçiler ve çok boyutlu diziler düzgün şekilde kullanılması nispeten zordur. Neredeyse tüm durumlarda, bu türleri parametre olarak almayı önlemek için API 'Ler yeniden dağıtılabilir.  
  
 **✓ DO** tüm yerleştirin `out` tüm değeri tarafından aşağıdaki parametreleri ve `ref` parametreleri (hariç parametre dizileri) arasında aşırı sıralama parametresinde bir tutarsızlık sonuçlanır olsa bile (bkz [üyesi Aşırı yükleme](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` parametreler ek dönüş değerleri olarak görülebilir ve bunları birlikte gruplandırmak yöntem imzasının anlaşılması daha kolay hale gelir.  
  
 **✓ DO** parametreleri üyeleri geçersiz kılarken adlandırma veya arabirim üyeleri uygulama tutarlı olmalıdır.  
  
 Bu, Yöntemler arasındaki ilişkiyi daha iyi bir şekilde iletir.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Enum ve Boole parametreleri arasında seçim yapma  
 **✓ DO** üyesi aksi iki veya daha fazla Boolean parametreleri varsa numaralandırmaları kullanın.  
  
 **X DO NOT** ayrıca ikiden fazla değerleri gereksinimini hiçbir zaman olacaktır kesinlikle emin olmadığınız sürece Boole değerlerini kullanın.  
  
 Numaralandırmalar, daha sonra değerlerin eklenmesi için bir yer sağlar, ancak [enum tasarımında açıklanan numaralandırıcılara](../../../docs/standard/design-guidelines/enum.md)değer eklemenin tüm etkilerine dikkat etmeniz gerekir.  
  
 **✓ CONSIDER** gerçekten iki durumlu değerleri desteklenir ve yalnızca Boole özellikleri başlatmak için kullanılan Oluşturucu parametreleri Boole değerlerini kullanarak.  
  
### <a name="validating-arguments"></a>Bağımsız değişkenler doğrulanıyor  
 **✓ DO** public, korumalı ya da açıkça gerçekleştirilen üyelerine geçirilen bağımsız değişken doğrulanamıyor. Doğrulama başarısız olursa, <xref:System.ArgumentException?displayProperty=nameWithType>veya alt sınıflarından birini oluşturun.  
  
 Gerçek doğrulamanın ortak veya korumalı üyenin kendisinde olması gerekmediğini unutmayın. Bu, bazı özel veya iç bir yordamın daha düşük bir düzeyinde gerçekleşecektir. Ana nokta, son kullanıcılara sunulan tüm yüzey alanının bağımsız değişkenleri denetlemesini sağlar.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> null bir bağımsız değişken geçirildi ve üye null bağımsız değişkenler desteklemiyor.  
  
 **✓ DO** enum parametreleri doğrulayın.  
  
 Enum bağımsız değişkenlerinin enum tarafından tanımlanan aralıkta olacağını varsaymayın. CLR, değer numaralandırmasında tanımlanmasa bile herhangi bir tamsayı değerini bir sabit listesi değerine dönüştürmeyi sağlar.  
  
 **X DO NOT** kullanmak <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> enum aralığının denetler.  
  
 **✓ DO** bunlar doğrulanan sonra değişebilir bağımsız değişkenleri değişmiş olabilecek unutmayın.  
  
 Üye güvenliğe duyarlı ise, bir kopya yapmanız ve sonra bağımsız değişkeni doğrulamanız ve işlemesi önerilir.  
  
### <a name="parameter-passing"></a>Parametre Geçirme  
 Bir çerçeve tasarımcısının perspektifinden, üç temel parametre grubu vardır: değere göre parametreler, `ref` parametreleri ve `out` parametreleri.  
  
 Bir bağımsız değişken bir by değeri parametresiyle geçirildiğinde, üye geçirilen gerçek bağımsız değişkenin bir kopyasını alır. Bağımsız değişken bir değer türü ise, bağımsız değişkenin bir kopyası yığına konur. Bağımsız değişken bir başvuru türü ise, başvurunun bir kopyası yığına konur. C#, Vb.net ve C++gibi en popüler CLR dilleri değere göre parametreleri geçirmek için varsayılan değer.  
  
 Bir bağımsız değişken bir `ref` parametresi aracılığıyla geçirildiğinde, üye geçirilen gerçek bağımsız değişkene bir başvuru alır. Bağımsız değişken bir değer türü ise, yığına bağımsız değişkene bir başvuru konur. Bağımsız değişken bir başvuru türü ise, bir başvuruya başvuru, yığına konur. `Ref` parametreler, üyenin çağıran tarafından geçirilen bağımsız değişkenleri değiştirmesine izin vermek için kullanılabilir.  
  
 `Out` parametreler, bazı küçük farklılıklar ile `ref` parametrelere benzerdir. Parametre başlangıçta atanmamış olarak kabul edilir ve bir değer atanmadan önce üye gövdesinde okunamaz. Ayrıca, parametreye, üyenin döndürdüğü bir değere atanmalıdır.  
  
 **X AVOID** kullanarak `out` veya `ref` parametreleri.  
  
 `out` veya `ref` parametrelerinin kullanılması işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeriyle yöntemleri işleme. Ayrıca, `out` ve `ref` parametreleri arasındaki fark yaygın olarak anlaşılmaz. Genel bir hedef kitle için tasarlayan çerçeve mimarları, kullanıcıların `out` veya `ref` parametreleriyle birlikte çalışmasını beklememelidir.  
  
 **X DO NOT** başvuru türleri başvuruya göre geçirin.  
  
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
  
 **✓ CONSIDER** az sayıda öğesi dizilerle geçirmek için son kullanıcıların bekliyorsanız params anahtar sözcüğü dizi parametreleri ekleme. Yaygın senaryolarda çok sayıda öğenin geçirilmesi bekleniyorsa, kullanıcılar muhtemelen bu öğeleri de satır içine geçirmeyecektir ve bu nedenle params anahtar sözcüğü gerekli değildir.  
  
 **X AVOID** çağıran neredeyse her zaman giriş zaten bir dizide isterseniz params dizileri kullanma.  
  
 Örneğin, bayt dizi parametrelerine sahip Üyeler tek tek baytlar ileterek neredeyse hiçbir şekilde çağrılmaz. Bu nedenle, .NET Framework bayt dizi parametreleri params anahtar sözcüğünü kullanmaz.  
  
 **X DO NOT** dizi params dizisi parametresi alma üyesi tarafından değiştirilirse params diziler kullanın.  
  
 Birçok derleyicilerin bağımsız değişkenlerini çağrı sitesinde geçici bir diziye değiştirdiğinden, dizi geçici bir nesne olabilir ve bu nedenle dizideki tüm değişiklikler kaybedilir.  
  
 **✓ CONSIDER** daha karmaşık bir aşırı kullanılamadı olsa bile bir basit aşırı params anahtar sözcüğü kullanarak.  
  
 Tüm aşırı yüklerde olmasa bile kullanıcılar bir aşırı yüklemede params dizisine sahip olacaksa kendinize sorun.  
  
 **✓ DO** params anahtar sözcüğü kullanmak mümkün kılmak için sipariş parametreleri deneyin.  
  
 **✓ CONSIDER** küçük sayıda bağımsız değişken son derece performans duyarlı API'lerde aramaları için özel aşırı ve kod yolları sağlama.  
  
 Bu, API, az sayıda bağımsız değişkenle çağrıldığında dizi nesneleri oluşturmaktan kaçınılmasını mümkün kılar. Parametre adlarını, dizi parametresinin tekil bir biçimini alarak ve sayısal bir sonek ekleyerek oluşturur.  
  
 Bunu yalnızca bir dizi oluşturun ve daha genel yöntemi çağırmak için kod yolunun tamamına özel durum oluşturacaksanız yapmanız gerekir.  
  
 **✓ DO** bu null params dizisi bağımsız değişken olarak geçirilen unutmayın.  
  
 İşlemeden önce dizinin null olduğunu doğrulamanız gerekir.  
  
 **X DO NOT** kullanmak `varargs` yöntemleri, aksi takdirde üç nokta bilinir.  
  
 Gibi bazı CLR dilleri C++, `varargs` Yöntemler adlı değişken parametre listelerinin geçirilmesi için alternatif bir kural destekler. Bu kural, CLS uyumlu olmadığından çerçeve içinde kullanılmamalıdır.  
  
### <a name="pointer-parameters"></a>İşaretçi parametreleri  
 Genel olarak, işaretçiler iyi tasarlanmış bir yönetilen kod çerçevesinin genel yüzey alanında görünmemelidir. Çoğu zaman işaretçiler kapsüllenmelidir. Ancak bazı durumlarda, birlikte çalışabilirlik nedenleriyle işaretçiler gereklidir ve bu gibi durumlarda işaretçiler kullanılması uygundur.  
  
 **✓ DO** işaretçileri CLS ile uyumlu olmadığı için bir işaretçi bağımsız değişken herhangi bir üyesi için bir alternatif sunar.  
  
 **X AVOID** pahalı bağımsız değişkeni işaretçi bağımsız denetimi yapılması.  
  
 **✓ DO** işaretçisi ile ilgili genel kurallar işaretçileri üyeleriyle tasarlarken izleyin.  
  
 Örneğin, başlangıç dizinini geçirmeniz gerekmez, çünkü basit işaretçi aritmetiği aynı sonucu elde etmek için kullanılabilir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
