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
ms.openlocfilehash: 5a0f6e0fab5d0f2fe8574e348fc6b8ae726eeb99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757410"
---
# <a name="parameter-design"></a>Parametre Tasarımı
Bu bölümde parametre tasarımı, bağımsız değişkenleri denetimini yönergeleri ile bölümler dahil olmak üzere geniş yönergeleri sağlar. Ayrıca, açıklanan yönergelere bakabilir [adlandırma parametreleri](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** üyesi tarafından gerekli işlevselliği sağlayan en az türetilen parametre türü kullanın.  
  
 Örneğin, bir koleksiyon numaralandırır ve her öğeyi konsola yazdırır bir yöntem tasarım istediğinizi varsayalım. Bu tür bir yöntem zamanınızı <xref:System.Collections.IEnumerable> parametre olarak değil <xref:System.Collections.ArrayList> veya <xref:System.Collections.IList>, örneğin.  
  
 **X DO NOT** ayrılmış parametrelerini kullanın.  
  
 Daha fazla üye girişe gelecekte yayımlanacak bir sürümde gerekirse, yeni aşırı eklenebilir.  
  
 **X DO NOT** işaretçileri, işaretçileri dizileri ya da parametre olarak çok boyutlu diziler alırken yöntemleri genel olarak kullanıma.  
  
 İşaretçiler ve çok boyutlu diziler düzgün bir şekilde kullanmak oldukça zordur. Bu tür parametreleri olarak almayı önlemek için hemen hemen tüm durumlarda, API'ler tasarlanması.  
  
 **✓ DO** tüm yerleştirin `out` tüm değeri tarafından aşağıdaki parametreleri ve `ref` parametreleri (hariç parametre dizileri) arasında aşırı sıralama parametresinde bir tutarsızlık sonuçlanır olsa bile (bkz [üyesi Aşırı yükleme](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametreleri fazladan dönüş değerleri olarak görülebilir ve Gruplama yoluyla yapar yöntem imzası daha kolay anlaşılır.  
  
 **✓ DO** parametreleri üyeleri geçersiz kılarken adlandırma veya arabirim üyeleri uygulama tutarlı olmalıdır.  
  
 Bu yöntem arasındaki ilişkiyi daha iyi iletişim kurar.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Enum ile Boole parametreleri arasında seçim yapma  
 **✓ DO** üyesi aksi iki veya daha fazla Boolean parametreleri varsa numaralandırmaları kullanın.  
  
 **X DO NOT** ayrıca ikiden fazla değerleri gereksinimini hiçbir zaman olacaktır kesinlikle emin olmadığınız sürece Boole değerlerini kullanın.  
  
 Numaralandırmalar gelecekteki ek değerler için yer sağlar, ancak anlatılan numaralandırmalar değerler ekleme tüm etkileri farkında olmalıdır [sabit listesi tasarımı](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** gerçekten iki durumlu değerleri desteklenir ve yalnızca Boole özellikleri başlatmak için kullanılan Oluşturucu parametreleri Boole değerlerini kullanarak.  
  
### <a name="validating-arguments"></a>Bağımsız değişkenler doğrulanıyor  
 **✓ DO** public, korumalı ya da açıkça gerçekleştirilen üyelerine geçirilen bağımsız değişken doğrulanamıyor. Throw <xref:System.ArgumentException?displayProperty=nameWithType>, veya doğrulama başarısız olursa alt sınıflarından biri.  
  
 Gerçek doğrulama ortak veya korumalı üye kendini olmasını zorunlu yok unutmayın. Bazı özel veya iç yordamında daha düşük bir düzeyde gerçekleşebilir. Son kullanıcılara gösterilen yüzey alanının tamamını bağımsız değişkenler denetler ana noktasıdır.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> null bir bağımsız değişken geçirildi ve üye null bağımsız değişkenler desteklemiyor.  
  
 **✓ DO** enum parametreleri doğrulayın.  
  
 Enum tarafından tanımlanan aralığın Enum bağımsız değişkenler olacak varsaymayın. CLR numaralandırma değeri tanımlanmamış olsa bile herhangi bir tamsayı değeri bir sabit listesi değeri atama sağlar.  
  
 **X DO NOT** kullanmak <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> enum aralığının denetler.  
  
 **✓ DO** bunlar doğrulanan sonra değişebilir bağımsız değişkenleri değişmiş olabilecek unutmayın.  
  
 Güvenlik duyarlı üyesiyse bir kopyasını oluşturun ve ardından doğrulamak ve bağımsız değişken işlemek için önerilir.  
  
### <a name="parameter-passing"></a>Parametre Geçirme  
 Framework Tasarımcısı perspektifinden parametrelerinin üç ana grup vardır: değer tarafından parametreleri `ref` parametreleri ve `out` parametreleri.  
  
 Bir bağımsız değişken değere göre parametresi aracılığıyla geçirilir, üye geçirilen gerçek bağımsız değişkenin bir kopyasını alır. Bağımsız değişken bir değer türü ise, bağımsız değişkenin bir kopyası yığına yerleştirilir. Bağımsız değişken bir başvuru türü ise yığında başvuru bir kopyasını konur. Parametrelerin değere göre geçirme için C#, VB.NET ve C++, varsayılan gibi en popüler CLR diller.  
  
 Ne zaman bir bağımsız değişken geçirilir aracılığıyla bir `ref` parametresi, üye geçirilen gerçek bağımsız değişkenin bir başvuru alır. Bağımsız değişken bir değer türü ise, bir bağımsız değişkene başvuru yığına yerleştirilir. Bağımsız değişken bir başvuru türü ise yığında başvuru başvuru konur. `Ref` Parametreler, üyeyi çağıran tarafından geçirilen bağımsız değişkenler değiştirmek izin vermek için kullanılabilir.  
  
 `Out` parametreleri benzer `ref` parametreleri, bazı küçük farklılıklar vardır. Parametre başlangıçta kabul atanmamış ve bir değer atanmadan önce üye gövdesinde okunamıyor. Ayrıca, üye döndürmeden önce bazı değeri atanacak parametresi vardır.  
  
 **X AVOID** kullanarak `out` veya `ref` parametreleri.  
  
 Kullanarak `out` veya `ref` parametreleri deneyimi işaretçilerle değer türleri ve başvuru türleri farkı anlama ve işleme yöntemi ile birden çok değer gerektirir. Ayrıca, arasındaki farkı `out` ve `ref` parametreleri anlaşılmadı. Genel kitle için tasarlama framework mimarları asıl kullanıcılara değil beklediğiniz `out` veya `ref` parametreleri.  
  
 **X DO NOT** başvuru türleri başvuruya göre geçirin.  
  
 Başvuruları takas etmek için kullanılan bir yöntem gibi kurala, sınırlı bazı özel durumlar vardır.  
  
### <a name="members-with-variable-number-of-parameters"></a>Değişken sayıda parametre ile üyeleri  
 Değişken sayıda bağımsız değişken alabilir üyeleri, bir dizi parametresi sağlayarak ifade edilir. Örneğin, <xref:System.String> aşağıdaki yöntem sağlar:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Bir kullanıcı daha sonra çağırabilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemini aşağıdaki gibi:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 C# params anahtar sözcüğü bir dizi parametresine ekleme sözde params dizisi parametresi parametre değiştirir ve geçici bir dizin oluşturmak için bir kısayol sağlar.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Bunun yapılması, dizi öğeleri doğrudan bağımsız değişken listesinde geçirerek yöntemini çağırmak kullanıcının sağlar.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Params anahtar sözcüğü parametre listesindeki son parametre için yalnızca eklenebilir unutmayın.  
  
 **✓ CONSIDER** az sayıda öğesi dizilerle geçirmek için son kullanıcıların bekliyorsanız params anahtar sözcüğü dizi parametreleri ekleme. Beklenen sayıda ortak senaryolar geçirilir, kullanıcıların bu öğeleri satır içi yine de geçmez büyük olasılıkla ve böylece params anahtar gerekli değildir.  
  
 **X AVOID** çağıran neredeyse her zaman giriş zaten bir dizide isterseniz params dizileri kullanma.  
  
 Örneğin, üyeleri Bayt dizisine parametreli neredeyse hiçbir zaman tek tek bayt geçirerek çağrılır. Bu nedenle, .NET Framework'teki bayt dizisi parametreleri params anahtar sözcüğünü kullanmayın.  
  
 **X DO NOT** dizi params dizisi parametresi alma üyesi tarafından değiştirilirse params diziler kullanın.  
  
 Çoğu derleyici çağrı sitesini geçici bir diziye üye bağımsız değişkenleri dönüştürün olgu nedeniyle geçici bir nesne dizisi olabilir ve bu nedenle dizi yapılan tüm değişiklikler kaybolacak.  
  
 **✓ CONSIDER** daha karmaşık bir aşırı kullanılamadı olsa bile bir basit aşırı params anahtar sözcüğü kullanarak.  
  
 Kendinize tüm aşırı yüklemeler olmasa bile params dizisi içinde aşırı yüklemelerden birine sahip kullanıcılar bildirmenizden durumunda sorun.  
  
 **✓ DO** params anahtar sözcüğü kullanmak mümkün kılmak için sipariş parametreleri deneyin.  
  
 **✓ CONSIDER** küçük sayıda bağımsız değişken son derece performans duyarlı API'lerde aramaları için özel aşırı ve kod yolları sağlama.  
  
 Bu API küçük sayıda bağımsız değişkenle çağrıldığında dizi nesnelerini oluşturmaktan kaçınmak mümkün kılar. Tekil bir dizi parametrenin alma ve sayısal bir sonek ekleyerek parametrelerinin adları oluşturur.  
  
 Özel durum için tüm kod yolu, yalnızca bir dizi oluşturun ve daha genel bir yöntemi çağırmak kullanacaksanız yalnızca bunu yapmanız gerekir.  
  
 **✓ DO** bu null params dizisi bağımsız değişken olarak geçirilen unutmayın.  
  
 Dizi önce işleme null değil doğrulamalıdır.  
  
 **X DO NOT** kullanmak `varargs` yöntemleri, aksi takdirde üç nokta bilinir.  
  
 Adlı değişken parametre listeleri geçirmek için alternatif bir kuralı C++ gibi bazı CLR dilleri destekleyen `varargs` yöntemleri. CLS uyumlu olmadığından kurala çerçeveleri alanında kullanılmamalıdır.  
  
### <a name="pointer-parameters"></a>İşaretçi parametreleri  
 Genel olarak, işaretçiler, iyi tasarlanmış bir yönetilen kod framework'ün genel yüzey alanını görünmemelidir. İşaretçileri, çoğu zaman, kapsüllenmiş. Ancak, bazı durumlarda işaretçileri birlikte çalışabilirlik nedenlerle gereklidir ve bu gibi durumlarda işaretçileri kullanmak uygundur.  
  
 **✓ DO** işaretçileri CLS ile uyumlu olmadığı için bir işaretçi bağımsız değişken herhangi bir üyesi için bir alternatif sunar.  
  
 **X AVOID** pahalı bağımsız değişkeni işaretçi bağımsız denetimi yapılması.  
  
 **✓ DO** işaretçisi ile ilgili genel kurallar işaretçileri üyeleriyle tasarlarken izleyin.  
  
 Örneğin, basit bir işaretçi aritmetik aynı sonuca ulaşmak için kullanılabildiğinden başlangıç dizini geçirilecek gerek yoktur.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
