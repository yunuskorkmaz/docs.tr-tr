---
title: Parametre tasarım
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e39b38fd72f9f3b9ce76aa6f7e96e44841daabb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578280"
---
# <a name="parameter-design"></a>Parametre tasarım
Bu bölümde parametre tasarım bağımsız değişkenleri denetleme yönergeleri bölümlerle dahil olmak üzere, geniş açıklamalar sağlar. Ayrıca, açıklanan yönergeleri için başvurmalıdır [adlandırma parametrelerini](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ YAPMAK** üyesi tarafından gerekli işlevselliği sağlayan en az türetilen parametre türü kullanın.  
  
 Örneğin, bir koleksiyon numaralandırır ve her öğeyi konsola yazdırır bir yöntem tasarım istediğinizi varsayalım. Bu tür bir yöntem gerçekleştirmesi gereken <xref:System.Collections.IEnumerable> parametre olarak değil <xref:System.Collections.ArrayList> veya <xref:System.Collections.IList>, örneğin.  
  
 **X yok** ayrılmış parametrelerini kullanın.  
  
 Bazı gelecek sürümünde üyesi için daha fazla giriş gerekirse, yeni bir aşırı eklenebilir.  
  
 **X yok** işaretçileri, işaretçileri dizileri ya da parametre olarak çok boyutlu diziler alırken yöntemleri genel olarak kullanıma.  
  
 İşaretçiler ve çok boyutlu diziler düzgün bir şekilde kullanmak görece zordur. Bu tür parametre olarak almayı önlemek için neredeyse her durumda, API tasarlanması.  
  
 **✓ YAPMAK** tüm yerleştirin `out` tüm değeri tarafından aşağıdaki parametreleri ve `ref` parametreleri (hariç parametre dizileri) arasında aşırı sıralama parametresinde bir tutarsızlık sonuçlanır olsa bile (bkz [üyesi Aşırı yükleme](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametreleri fazladan dönüş değerleri olarak görülen ve bir arada gruplandırma yapar yöntem imzası anlamak daha kolay.  
  
 **✓ YAPMAK** parametreleri üyeleri geçersiz kılarken adlandırma veya arabirim üyeleri uygulama tutarlı olmalıdır.  
  
 Bu daha iyi yöntemleri arasındaki ilişkiyi iletişim kurar.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Enum ve Boolean parametreleri arasında seçim yapma  
 **✓ YAPMAK** üyesi aksi iki veya daha fazla Boolean parametreleri varsa numaralandırmaları kullanın.  
  
 **X yok** ayrıca ikiden fazla değerleri gereksinimini hiçbir zaman olacaktır kesinlikle emin olmadığınız sürece Boole değerlerini kullanın.  
  
 Numaralandırmalar size gelecekteki değerleri eklenmesi için bazı yeri ancak açıklanan Enum değerleri için değerleri ekleyerek tüm etkilerini bilmeniz [Enum tasarım](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ DÜŞÜNÜN** gerçekten iki durumlu değerleri desteklenir ve yalnızca Boole özellikleri başlatmak için kullanılan Oluşturucu parametreleri Boole değerlerini kullanarak.  
  
### <a name="validating-arguments"></a>Bağımsız değişkenler doğrulanıyor  
 **✓ YAPMAK** public, korumalı ya da açıkça gerçekleştirilen üyelerine geçirilen bağımsız değişken doğrulanamıyor. Throw <xref:System.ArgumentException?displayProperty=nameWithType>, veya doğrulama başarısız olursa, alt sınıfların, biri.  
  
 Gerçek doğrulama mutlaka genel ya da korumalı üye kendisini olmasını sahip olup olmadığını unutmayın. Bazı özel veya dahili yordamında daha düşük düzeydeki meydana gelebilir. Son kullanıcılara sunulan tüm yüzey alanını bağımsız değişkenler denetler ana noktasıdır.  
  
 **✓ YAPMAK** throw <xref:System.ArgumentNullException> null bir bağımsız değişken geçirildi ve üye null bağımsız değişkenler desteklemiyor.  
  
 **✓ YAPMAK** enum parametreleri doğrulayın.  
  
 Enum bağımsız değişkenleri enum tarafından tanımlanan aralığın olacak varsayalım değil. CLR enum değeri tanımlanmamış olsa bile herhangi bir tamsayıyla bir enum değeri atama sağlar.  
  
 **X yok** kullanmak <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> enum aralığının denetler.  
  
 **✓ YAPMAK** bunlar doğrulanan sonra değişebilir bağımsız değişkenleri değişmiş olabilecek unutmayın.  
  
 Güvenlik hassas üyesiyse bir kopyasını oluşturun ve ardından doğrulamak ve bağımsız değişkeni işlemek için önerilir.  
  
### <a name="parameter-passing"></a>Parametre Geçirme  
 Framework Tasarımcısı perspektifinden parametrelerinin üç ana grubu vardır: değer tarafından parametreleri `ref` parametreleri ve `out` parametreleri.  
  
 Bağımsız değişken değeri tarafından parametresi üzerinden geçirildiğinde üye geçirilen gerçek bağımsız değişken bir kopyasını alır. Bağımsız değişken bir değer türü ise, bağımsız değişkeni bir kopyasını yığında yerleştirilir. Bağımsız değişkeni bir başvuru türü ise, başvuru kopyası yığında konur. Parametreleri değere göre geçirme için C#, VB.NET ve C++, varsayılan gibi en popüler CLR dilleri.  
  
 Ne zaman bir bağımsız değişken geçirilir aracılığıyla bir `ref` parametresi, üye geçirilen gerçek bağımsız değişkeni bir başvuru alır. Bağımsız değişken bir değer türü ise, bağımsız değişkeni bir başvuru yığında yerleştirilir. Bağımsız değişkeni bir başvuru türü ise, başvuru başvuru yığında yerleştirilir. `Ref` Parametreler, çağıran tarafından geçirilen bağımsız değişken değiştirmek üye izin vermek için kullanılabilir.  
  
 `Out` parametreleri benzer `ref` parametrelerle bazı küçük farklar. Parametre başlangıçta kabul atanmamış ve bazı değer atanmadan önce üye gövdesinde okunamıyor. Ayrıca, parametre üye döndürmeden önce bir değer atanması gerekir.  
  
 **KAÇININ x** kullanarak `out` veya `ref` parametreleri.  
  
 Kullanarak `out` veya `ref` parametreleri değer türleri ve başvuru türleri nasıl farklı anlama ve birden çok dönüş değerleri yöntemleriyle işleme işaretçileri deneyimiyle gerektirir. Ayrıca, arasındaki farkı `out` ve `ref` parametreleri değil yaygın anladım. Genel kitleye tasarlama framework mimarları ana çalışmak kullanıcılara değil beklediğiniz `out` veya `ref` parametreleri.  
  
 **X yok** başvuru türleri başvuruya göre geçirin.  
  
 Başvuruları takas etmek için kullanılan bir yöntem gibi kuralına sınırlı bazı özel durumlar vardır.  
  
### <a name="members-with-variable-number-of-parameters"></a>Değişken sayıda parametre ile üyeleri  
 Değişken sayıda bağımsız değişken sürebilir üyeleri bir dizi parametre sağlayarak ifade edilir. Örneğin, <xref:System.String> aşağıdaki yöntemi sağlar:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Bir kullanıcı ardından çağırabilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithType> şekilde yöntemi:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 C# params anahtar sözcüğü bir dizi parametre ekleme parametresi sözde params dizisi parametresi değiştirir ve geçici bir dizi oluşturma için bir kısayol sağlar.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Bunun yapılması, doğrudan bağımsız değişken listesinde dizi öğeleri geçirerek yöntemini çağırmak kullanıcının sağlar.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Params anahtar sözcüğü yalnızca parametre listesindeki son parametre eklenebilir olduğunu unutmayın.  
  
 **✓ DÜŞÜNÜN** az sayıda öğesi dizilerle geçirmek için son kullanıcıların bekliyorsanız params anahtar sözcüğü dizi parametreleri ekleme. Öğeleri çok sayıda ortak senaryolar geçirilir bekleniyorsa kullanıcılar bu öğeleri satır içi yine de geçmez büyük olasılıkla ve bu nedenle params anahtar sözcüğü gerekli değildir.  
  
 **KAÇININ x** çağıran neredeyse her zaman giriş zaten bir dizide isterseniz params dizileri kullanma.  
  
 Örneğin, bayt dizisi parametreleri üyeleriyle neredeyse hiçbir zaman tek tek bayt geçirerek çağrılması. Bu nedenle, .NET Framework'teki bayt dizisi parametreleri params anahtar sözcüğü kullanmayın.  
  
 **X yok** dizi params dizisi parametresi alma üyesi tarafından değiştirilirse params diziler kullanın.  
  
 Birçok derleyicileri çağrısı sitede geçici bir dizi içine üye değişkenleri kapatma olgu nedeniyle dizisi geçici bir nesne olabilir ve bu nedenle dizi yapılan tüm değişiklikler kaybolacak.  
  
 **✓ DÜŞÜNÜN** daha karmaşık bir aşırı kullanılamadı olsa bile bir basit aşırı params anahtar sözcüğü kullanarak.  
  
 Kendinizi kullanıcıların içinde tüm aşırı olmasa bile bir aşırı params dizisi sahip değer, isteyin.  
  
 **✓ YAPMAK** params anahtar sözcüğü kullanmak mümkün kılmak için sipariş parametreleri deneyin.  
  
 **✓ DÜŞÜNÜN** küçük sayıda bağımsız değişken son derece performans duyarlı API'lerde aramaları için özel aşırı ve kod yolları sağlama.  
  
 Küçük sayıda bağımsız değişken API'nin çağrıldığında array nesneleri oluşturmamak mümkün kılar. Parametrelerinin adları tekil dizi parametresi alma ve sayısal bir sonek ekleyerek oluşturur.  
  
 Özel durum için tüm kod yolu, yalnızca bir dizi oluşturun ve daha fazla genel yöntemini çağırın kullanacaksanız yalnızca bunu yapmanız gerekir.  
  
 **✓ YAPMAK** bu null params dizisi bağımsız değişken olarak geçirilen unutmayın.  
  
 Dizi önce işlem null olmayan doğrulamalıdır.  
  
 **X yok** kullanmak `varargs` yöntemleri, aksi takdirde üç nokta bilinir.  
  
 Adlı değişken parametre listeleri geçirmek için alternatif bir kural C++ gibi bazı CLR dilleri desteği `varargs` yöntemleri. CLS uyumlu olmadığından kuralı içinde çerçeve, kullanılmamalıdır.  
  
### <a name="pointer-parameters"></a>İşaretçi parametreleri  
 Genel olarak, iyi tasarlanmış yönetilen kod framework'ün ortak yüzey alanını işaretçileri görünmemelidir. Çoğu zaman, işaretçileri kapsüllenmiş. Ancak, bazı durumlarda işaretçileri birlikte çalışabilirlik nedenlerle gereklidir ve bu gibi durumlarda işaretçileri kullanarak uygundur.  
  
 **✓ YAPMAK** işaretçileri CLS ile uyumlu olmadığı için bir işaretçi bağımsız değişken herhangi bir üyesi için bir alternatif sunar.  
  
 **KAÇININ x** pahalı bağımsız değişkeni işaretçi bağımsız denetimi yapılması.  
  
 **✓ YAPMAK** işaretçisi ile ilgili genel kurallar işaretçileri üyeleriyle tasarlarken izleyin.  
  
 Örneğin, çünkü basit işaretçi aritmetiği aynı sonucu gerçekleştirmek için kullanılabilir başlangıç dizini geçirmek için gerek yoktur.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
