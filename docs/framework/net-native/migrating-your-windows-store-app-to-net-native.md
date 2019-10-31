---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 7eea089ef9b492e156758d170394b17d74a60a64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128319"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma

.NET Native, Windows Mağazası 'nda veya geliştiricinin bilgisayarındaki uygulamaların statik derlemesini sağlar. Bu, Windows Mağazası uygulamaları için tek seferlik (JıT) derleyici veya cihazdaki [Yerel Görüntü Oluşturucu (Ngen. exe)](../tools/ngen-exe-native-image-generator.md) tarafından gerçekleştirilen dinamik derlemeden farklıdır. Farklılıklara rağmen .NET Native, [Windows Mağazası uygulamaları için .net](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)ile uyumluluğu sürdürmenize çalışır. Çoğu bölümde, Windows Mağazası uygulamaları için .NET üzerinde çalışan şeyler .NET Native de çalışır.  Ancak bazı durumlarda, davranış değişiklikleriyle karşılaşabilirsiniz. Bu belgede, Windows Mağazası uygulamaları için standart .NET ve aşağıdaki alanlardaki .NET Native arasındaki farklar ele alınmaktadır:

- [Genel çalışma zamanı farklılıkları](#Runtime)

- [Dinamik programlama farkları](#Dynamic)

- [Yansıma ile ilgili diğer farklar](#Reflection)

- [Desteklenmeyen senaryolar ve API 'Ler](#Unsupported)

- [Visual Studio farklılıkları](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>Genel çalışma zamanı farklılıkları

- Bir uygulama ortak dil çalışma zamanı (CLR) üzerinde çalışırken JıT derleyicisi tarafından oluşturulan <xref:System.TypeLoadException>özel durumlar, genellikle .NET Native tarafından işlendiğinde derleme zamanı hatalarına neden oluşur.

- Uygulamanın kullanıcı arabirimi iş parçacığından <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> yöntemini çağırmayın. Bu, .NET Native kilitlenmeye neden olabilir.

- Statik sınıf Oluşturucu çağırma sıralamasına güvenmeyin. .NET Native, çağırma sırası standart çalışma zamanındaki siparişten farklıdır. (Standart çalışma zamanı ile bile, statik sınıf oluşturucuların yürütme sırasına dayanmamanız gerekir.)

- Herhangi bir iş parçacığında çağrı yapma (örneğin, `while(true);`) çağrısı yapılmadan sonsuz döngü, uygulamayı bir durmasına getirebilir. Benzer şekilde, büyük veya sonsuz bir bekleme süresi uygulamayı bir durabilir.

- Belirli genel başlatma döngüleri .NET Native özel durum oluşturmaz. Örneğin, aşağıdaki kod standart CLR üzerinde <xref:System.TypeLoadException> bir özel durum oluşturur. .NET Native, değildir.

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- Bazı durumlarda .NET Native, .NET Framework sınıf kitaplıklarının farklı uygulamalarını sağlar. Bir yöntemden döndürülen bir nesne, döndürülen türün üyelerini her zaman uygular. Ancak, kendi yedekleme uygulamaları farklı olduğundan, diğer .NET Framework platformlarındaki gibi aynı tür kümesine de atama yapamazsınız. Örneğin, bazı durumlarda <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> veya <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> gibi yöntemler tarafından döndürülen <xref:System.Collections.Generic.IEnumerable%601> Interface nesnesini `T[]`olarak çevirebilirsiniz.

- WinInet önbelleği, Windows Mağazası uygulamaları için .NET ' te varsayılan olarak etkinleştirilmez, ancak .NET Native. Bu, performansı artırır ancak çalışma kümesi etkilerine sahiptir. Geliştirici eylemi gerekli değildir.

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>Dinamik programlama farkları

Kod, en yüksek performans için yerel koda .NET Framework kodda statik olarak bağlantı .NET Native. Ancak, ikili boyutların küçük kalması gerekir, bu nedenle tüm .NET Framework alınamaz. .NET Native derleyici, kullanılmayan koda başvuruları kaldıran bir Dependency Reducer kullanarak bu sınırlamayı çözer. Ancak .NET Native, bu bilgiler derleme zamanında statik olarak çıkarsanamıyor, ancak çalışma zamanında dinamik olarak alınırsa, bazı tür bilgileri ve kod üretilemez.

.NET Native, yansıma ve dinamik programlamayı etkinleştirir. Ancak, oluşturulan kod boyutunu çok büyük hale getirmek (özellikle de .NET Framework ortak API 'lerde yansıtma desteklendiğinden) için tüm türler yansıma için işaretlenemez. .NET Native derleyicisi, hangi türlerin yansıma desteklemesi gerektiği konusunda akıllı seçimler yapar ve meta verileri korur ve yalnızca bu türler için kod oluşturur.

Örneğin, veri bağlama bir uygulamanın özellik adlarını işlevlerle eşleştirebilmesini gerektirir. Windows Mağazası uygulamaları için .NET sürümünde ortak dil çalışma zamanı, bu özelliği yönetilen türler ve genel kullanıma açık yerel türler için otomatik olarak yansıma kullanır. .NET Native, derleyici, verileri bağlacağınız türler için otomatik olarak meta veriler içerir.

.NET Native derleyici, <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>gibi yaygın olarak kullanılan genel türleri de işleyebilir ve bu, herhangi bir ipucu veya yönergeler gerekmeden çalışır. [Dynamic](../../csharp/language-reference/keywords/dynamic.md) anahtar sözcüğü belirli sınırlar içinde de desteklenir.

> [!NOTE]
> Uygulamanızı .NET Native taşıma sırasında tüm dinamik kod yollarını iyice test etmelisiniz.

.NET Native için varsayılan yapılandırma çoğu geliştirici için yeterlidir, ancak bazı geliştiriciler çalışma zamanı yönergeleri (. RD. xml) dosyası kullanarak yapılandırmalarını ince ayar yapmak isteyebilir. Ayrıca, bazı durumlarda .NET Native derleyicisi, özellikle aşağıdaki durumlarda, yansıma için hangi meta verilerin kullanılabilir olması gerektiğini belirleyemez ve ipuçlarına dayanır:

- <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> gibi bazı yapılar statik olarak belirlenemez.

- Derleyici örneklemeleri belirleyemediği için, üzerinde yansıtmak istediğiniz genel bir türün çalışma zamanı yönergeleri tarafından belirtilmesi gerekir. Bu, tüm kodun dahil olması gerektiğinden, ancak genel türlerde yansıma bir sonsuz döngüye (örneğin, genel bir tür üzerinde çağrıldığında genel bir yöntem çağrıldığında) sahip olduğu için bu değildir.

> [!NOTE]
> Çalışma zamanı yönergeleri, çalışma zamanı yönergeleri (. RD. xml) dosyasında tanımlanmıştır. Bu dosyayı kullanma hakkında genel bilgi için [bkz. Başlarken](getting-started-with-net-native.md). Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).

.NET Native Ayrıca, geliştiricinin varsayılan küme dışında hangi türlerin yansıma destekleceğini belirlemesine yardımcı olan profil oluşturma araçlarını içerir.

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>Yansıma ile ilgili diğer farklar

Windows Mağazası uygulamaları ve .NET Native için .NET arasındaki davranıştaki farklı yansıma ile ilgili birçok fark vardır.

.NET Native:

- .NET Framework sınıf kitaplığındaki türler ve Üyeler üzerinde özel yansıma desteklenmez. Bununla birlikte, kendi özel türlerinizin ve üyelerinizin yanı sıra üçüncü taraf kitaplıklardaki türler ve Üyeler üzerinde de yansıtma yapabilirsiniz.

- <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> özelliği, bir dönüş değerini temsil eden bir <xref:System.Reflection.ParameterInfo> nesnesi için `false` doğru döndürür. Windows Mağazası uygulamaları için .NET sürümünde `true`döndürür. Ara dil (IL) bunu doğrudan desteklemez ve yorum dile bırakılır.

- <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapılarında ortak Üyeler desteklenmez. Bu türler yalnızca LINQ, ifade ağaçları ve statik dizi başlatma için desteklenir.

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType>, temel sınıflarda gizli üyeleri içerir ve bu nedenle açık geçersiz kılmalar olmadan geçersiz kılınabilir. Bu aynı zamanda diğer [Runtimereftactionextensions. GetRuntime * metotlarından](xref:System.Reflection.RuntimeReflectionExtensions) de geçerlidir.

- <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimler oluşturmaya çalıştığınızda başarısız olmaz (örneğin, bir byrefs dizisi).

- İşaretçi parametrelerine sahip üyeleri çağırmak için yansıma kullanamazsınız.

- Bir işaretçi alanı almak veya ayarlamak için yansıma kullanamazsınız.

- Bağımsız değişken sayısı yanlış olduğunda ve bağımsız değişkenlerden birinin türü yanlış olduğunda .NET Native, <xref:System.Reflection.TargetParameterCountException>yerine bir <xref:System.ArgumentException> oluşturur.

- Özel durumların ikili seri hale getirilmesi genellikle desteklenmez. Sonuç olarak, serileştirilebilir olmayan nesneler <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğüne eklenebilir.

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>Desteklenmeyen senaryolar ve API 'Ler

Aşağıdaki bölümlerde, HTTPClient ve Windows Communication Foundation (WCF) gibi genel geliştirme, birlikte çalışma ve teknolojiler için desteklenmeyen senaryolar ve API 'Ler listelenmektedir:

- [Genel geliştirme](#General)

- [HttpClient](#HttpClient)

- [Interop](#Interop)

- [Desteklenmeyen API 'Ler](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>Genel geliştirme farkları

**Değer türleri**

- Değer türü için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> ve <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> yöntemlerini geçersiz kılarsınız, temel sınıf uygulamalarını çağırmayın. Windows Mağazası uygulamaları için .NET ' te bu yöntemler yansıma kullanır. Derleme zamanında .NET Native, çalışma zamanı Reflection kullanmadığı bir uygulama oluşturur. Yani, bu iki yöntemi geçersiz kılmıyorsanız, .NET Native, derleme zamanında uygulamayı oluşturduğundan, beklendiği gibi çalışır. Ancak, bu yöntemleri geçersiz kılmak ancak temel sınıf uygulamasını çağırmak bir özel durumla sonuçlanır.

- Bir megabayttan büyük değer türleri desteklenmez.

- Değer türlerinde .NET Native parametresiz Oluşturucu olamaz. (C# ve Visual Basic değer türlerinde parametresiz oluşturucuları yasakla. Ancak bunlar Il 'de oluşturulabilir.)

**Diziler**

- Sıfırdan farklı bir alt sınır içeren diziler desteklenmez. Genellikle, bu diziler <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yüklemesi çağırarak oluşturulur.

- Çok boyutlu dizilerin dinamik olarak oluşturulması desteklenmez. Bu tür diziler genellikle `lengths` parametresi içeren <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> yönteminin aşırı yüklemesi çağırarak veya <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemini çağırarak oluşturulur.

- Dört veya daha fazla boyut içeren çok boyutlu diziler desteklenmez; diğer bir deyişle, <xref:System.Array.Rank%2A?displayProperty=nameWithType> Özellik değeri dört veya daha büyüktür. Bunun yerine [pürüzlü dizileri](../../csharp/programming-guide/arrays/jagged-arrays.md) (dizi dizileri) kullanın. Örneğin, `array[x,y,z]` geçersizdir, ancak `array[x][y][z]` değildir.

- Çok boyutlu dizilerin varyansı desteklenmez ve çalışma zamanında <xref:System.InvalidCastException> bir özel duruma neden olur.

**Genel Türler**

- Sonsuz genel tür genişletmesi bir derleyici hatası ile sonuçlanır. Örneğin, bu kod derlenmesi başarısız olur:

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**İşaretçiler**

- İşaretçilerin dizileri desteklenmez.

- Bir işaretçi alanı almak veya ayarlamak için yansıma kullanamazsınız.

**Serileştirme**

<xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> özniteliği desteklenmez. Bunun yerine <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> özniteliğini kullanın.

**Kaynaklar**

Yerelleştirilmiş kaynakların <xref:System.Diagnostics.Tracing.EventSource> sınıfıyla kullanılması desteklenmez. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> özelliği yerelleştirilmiş kaynakları tanımlamaz.

**Temsilciler**

`Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.

**Çeşitli API'ler**

- Tür için bir <xref:System.Runtime.InteropServices.GuidAttribute> özniteliği uygulanmazsa [TypeInfo. GUID](xref:System.Type.GUID) özelliği <xref:System.PlatformNotSupportedException> bir özel durum oluşturur. GUID öncelikle COM desteği için kullanılır.

- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> yöntemi, .NET Native kısa tarihleri içeren dizeleri doğru şekilde ayrıştırır. Ancak, Microsoft Bilgi Bankası makalelerinde [KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755)'de açıklanan tarih ve saat ayrıştırılırken yapılan değişikliklerle uyumluluğu korumaz.

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` .NET Native doğru şekilde yuvarlanır. CLR 'nin bazı sürümlerinde, sonuç dizesi yuvarlatılmış yerine kesilir.

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>HttpClient farkları

.NET Native, <xref:System.Net.Http.HttpClientHandler> sınıfı, Windows Mağazası uygulamaları için standart .NET içinde kullanılan <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları yerine WinINet (<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> sınıfı aracılığıyla) kullanır.  WinINet, <xref:System.Net.Http.HttpClientHandler> sınıfının desteklediği tüm yapılandırma seçeneklerini desteklemez.  Sonuç olarak:

- <xref:System.Net.Http.HttpClientHandler> Özellik özelliklerinden bazıları .NET Native `false` döndürülür, ancak Windows Mağazası uygulamaları için standart .NET içindeki `true` geri dönirler.

- `get` erişimcileri bazı yapılandırma özelliği, Windows Mağazası uygulamaları için .NET 'teki varsayılan yapılandırılabilir değerden farklı .NET Native her zaman sabit bir değer döndürür.

Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.

**Proxy**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> sınıfı, istek temelinde proxy 'nin yapılandırılmasını veya geçersiz kılınmasını desteklemez.  Bu, .NET Native üzerindeki tüm isteklerin, <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> özelliğinin değerine bağlı olarak sistem tarafından yapılandırılan proxy sunucusunu veya proxy sunucu olmadığını kullandığı anlamına gelir.  Windows Mağazası uygulamaları için .NET ' te, proxy sunucusu <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özelliği tarafından tanımlanır.  .NET Native, <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> `null` dışında bir değere ayarlamak <xref:System.PlatformNotSupportedException> özel durumu oluşturur.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> özelliği .NET Native `false` döndürür, ancak Windows Mağazası uygulamaları için standart .NET Framework `true` döndürür.

**Otomatik yeniden yönlendirme**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> sınıfı, en fazla otomatik yeniden yönlendirme sayısının yapılandırılmasına izin vermez.  <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> özelliğinin değeri, Windows Mağazası uygulamaları için standart .NET ' de varsayılan olarak 50 ' dir ve değiştirilebilir. .NET Native, bu özelliğin değeri 10 ' dur ve değiştirme girişimi bir <xref:System.PlatformNotSupportedException> özel durumu oluşturur.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> özelliği .NET Native `false` döndürür, ancak Windows Mağazası uygulamaları için .NET 'te `true` döndürür.

**Otomatik açma**

Windows Mağazası uygulamaları için .NET, <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, hem <xref:System.Net.DecompressionMethods.Deflate> hem <xref:System.Net.DecompressionMethods.GZip>veya <xref:System.Net.DecompressionMethods.None>olarak ayarlamanıza olanak tanır.  .NET Native yalnızca <xref:System.Net.DecompressionMethods.GZip>veya <xref:System.Net.DecompressionMethods.None>birlikte <xref:System.Net.DecompressionMethods.Deflate> destekler.  <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> özelliği <xref:System.Net.DecompressionMethods.Deflate> veya <xref:System.Net.DecompressionMethods.GZip> tek başına sessizce, hem <xref:System.Net.DecompressionMethods.Deflate> hem de <xref:System.Net.DecompressionMethods.GZip>olarak ayarlar.

**Çerezler**

Tanımlama bilgisi işleme <xref:System.Net.Http.HttpClient> ve WinINet tarafından eşzamanlı olarak gerçekleştirilir.  <xref:System.Net.CookieContainer> tanımlama bilgileri, Winınet tanımlama bilgisi önbelleğindeki tanımlama bilgileriyle birleştirilir.  <xref:System.Net.CookieContainer> bir tanımlama bilgisinin kaldırılması, <xref:System.Net.Http.HttpClient> tanımlama bilgisinin gönderilmesini engeller, ancak tanımlama bilgisi zaten WinINet tarafından görülmüştür ve tanımlama bilgileri Kullanıcı tarafından silinmemekte ise WinINet tarafından gönderilir.  <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>veya <xref:System.Net.CookieContainer> API 'sini kullanarak bir tanımlama bilgisinin WinINet 'den program aracılığıyla kaldırılması mümkün değildir.  <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> özelliğinin `false` olarak ayarlanması yalnızca <xref:System.Net.Http.HttpClient> tanımlama bilgilerinin gönderilmesini durdurmasına neden olur; WinINet, isteğe tanımlama bilgilerini yine de dahil edebilir.

**Credentials**

Windows Mağazası uygulamaları için .NET ' te, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği <xref:System.Net.ICredentials> arabirimini uygulayan tüm nesneleri kabul eder.  .NET Native, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliğinin `true` olarak ayarlanması <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliğinin `null`hale gelmesine neden olur.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>veya <xref:System.Net.NetworkCredential>türündeki bir nesneye ayarlanabilir.  Diğer <xref:System.Net.ICredentials> nesneleri atama, en popüler olan <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliğine <xref:System.Net.CredentialCache>bir <xref:System.PlatformNotSupportedException>oluşturur.

**Desteklenmeyen diğer veya yapılandırılamayan Özellikler**

.NET Native:

- <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> özelliğinin değeri her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic>.  Windows Mağazası uygulamaları için .NET ' te varsayılan değer <xref:System.Net.Http.ClientCertificateOption.Manual>.

- <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> özelliği yapılandırılabilir değildir.

- <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> özelliği her zaman `true`.  Windows Mağazası uygulamaları için .NET ' te varsayılan değer `false`.

- Yanıtlarındaki `SetCookie2` üst bilgisi artık kullanılmıyor olarak yoksayılır.

<a name="Interop"></a>
### <a name="interop-differences"></a>Birlikte çalışma farklılıkları
 **Kullanım dışı API 'Ler**

 Yönetilen kodla birlikte çalışabilirlik için sık kullanılan birçok API kullanım dışı bırakılmıştır. .NET Native ile kullanıldığında, bu API 'Ler bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durumu oluşturabilir ya da bir derleyici hatasına neden olabilir. Windows Mağazası uygulamaları için .NET sürümünde, bu API 'Ler, bir derleyici hatası yerine bir derleyici uyarısı üretse de eski olarak işaretlenir.

 `VARIANT` sıralaması için kullanım dışı olan API 'Ler şunları içerir:

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya ByRef türevlerinde kullanılması gibi bazı senaryolarda bir özel durum oluşturur.

 [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteği için kullanım dışı API 'ler şunlardır:

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

Klasik COM olayları için kullanım dışı API 'Ler şunlardır:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> arabirimindeki kullanım dışı API 'Ler, .NET Native desteklenmeyen, şunları içerir:

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (tüm Üyeler)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (tüm Üyeler)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (tüm Üyeler)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

Desteklenmeyen diğer birlikte çalışma özellikleri şunlardır:

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (tüm Üyeler)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (tüm Üyeler)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 Nadiren kullanılan sıralama API 'Leri:

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **Platform çağırma ve COM birlikte çalışma uyumluluğu**

 Çoğu platform çağırma ve COM birlikte çalışma senaryosu hala .NET Native desteklenmektedir. Özellikle, Windows Çalışma Zamanı (WinRT) API 'Leriyle birlikte çalışabilirlik ve Windows Çalışma Zamanı için gereken tüm sıralama desteklenir. Bu, için sıralama desteğini içerir:

- Diziler (<xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>dahil)

- `BStr`

- Temsilciler

- Dizeler (Unicode, ANSI ve HSTRıNG)

- Yapılar (`byref` ve `byval`)

- Birleşimler

- Win32 tutamaçları

- Tüm WinRT yapıları

- Değişken türlerini hazırlama için kısmi destek. Aşağıdakiler desteklenir:

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

Ancak, .NET Native aşağıdakileri desteklemez:

- Klasik COM olaylarını kullanma

- Yönetilen bir tür üzerinde <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> arabirimini uygulama

- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> özniteliği aracılığıyla bir yönetilen tür üzerinde [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini uygulama. Ancak, COM nesnelerini `IDispatch`aracılığıyla çağıramayacağınızı ve yönetilen nesnenizin `IDispatch`uygulayamadığını unutmayın.

Bir platform çağırma yöntemi çağırmak için yansıma kullanılması desteklenmez. Yöntem çağrısını başka bir yöntemde sarmalayarak ve bunun yerine sarmalayıcı çağırmak için yansıma kullanarak bu sınırlamaya geçici bir çözüm bulabilirsiniz.

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Windows Mağazası uygulamaları için .NET API 'Lerinden diğer farklılıklar

Bu bölümde, .NET Native desteklenmeyen kalan API 'Ler listelenir. Desteklenmeyen API 'lerin en büyük kümesi Windows Communication Foundation (WCF) API 'lardır.

**Dataaçıklamalarda (System. ComponentModel. Dataaçıklamalarda)**

<xref:System.ComponentModel.DataAnnotations> ve <xref:System.ComponentModel.DataAnnotations.Schema> ad alanlarındaki türler .NET Native desteklenmez. Bunlar, Windows 8 için Windows Mağazası uygulamaları için .NET sürümünde mevcut olan aşağıdaki türleri içerir:

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

Visual Basic şu anda .NET Native desteklenmiyor. <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> ad alanlarında bulunan aşağıdaki türler .NET Native kullanılamaz:

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**Yansıma bağlamı (System. Reflection. Context ad alanı)**

<xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> sınıfı .NET Native desteklenmez.

**RTC (System .net. http. rtc)**

`System.Net.Http.RtcRequestFactory` sınıfı .NET Native desteklenmez.

**Windows Communication Foundation (WCF) (System. ServiceModel.\*)**

[System. ServiceModel. * ad](xref:System.ServiceModel) alanlarındaki türler .NET Native desteklenmez. Bunlar aşağıdaki türleri içerir:

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>Serileştiricilerle farklılıklar

Aşağıdaki farklar <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve <xref:System.Xml.Serialization.XmlSerializer> sınıflarıyla serileştirme ve seri durumdan çıkarma ile ilgili bir konudur:

- .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> türü bir kök serileştirme türü olmayan bir temel sınıf üyesine sahip türetilmiş bir sınıfı seri hale getirme veya serisini kaldırma başarısız. Örneğin, aşağıdaki kodda `Y` seri hale getirme veya serisini kaldırma girişimi bir hata ile sonuçlanır:

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  Tür `InnerType` seri hale getirici tarafından bilinmediği için, temel sınıfın üyelerine serileştirme sırasında çapraz aktarılmaz.

- <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan bir sınıf veya yapıyı serileştirmek için başarısız olur. Örneğin, aşağıdaki türler seri hale getirilemez veya seri durumdan çıkarılamıyor:

- <xref:System.Xml.Serialization.XmlSerializer>, seri hale getirilecek nesnenin tam türünü bilmez olduğundan, aşağıdaki nesne değerini seri hale getiremedi:

- seri hale getirilen nesnenin türü <xref:System.Xml.XmlQualifiedName><xref:System.Xml.Serialization.XmlSerializer> seri hale getirilemez veya seri durumdan çıkarılamıyor.

- Tüm serileştiriciler (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve <xref:System.Xml.Serialization.XmlSerializer>), tür <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya <xref:System.Xml.Linq.XElement>içeren bir tür için serileştirme kodu oluşturamıyor. Bunun yerine derleme zamanı hatalarını görüntüler.

- Serileştirme türlerinin aşağıdaki oluşturucuların beklenen şekilde çalışması garanti edilmez:

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>

- <xref:System.Xml.Serialization.XmlSerializer>, aşağıdaki özniteliklerden herhangi biriyle öznitelikli yöntemlere sahip olan bir tür için kod üretemiyor:

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Xml.Serialization.IXmlSerializable> özel serileştirme arabirimine uymuyor. Bu arabirimi uygulayan bir sınıfınız varsa <xref:System.Xml.Serialization.XmlSerializer>, türü düz eski bir CLR nesnesi (POCO) türü olarak değerlendirir ve yalnızca ortak özelliklerini serileştirir.

- Düz bir <xref:System.Exception> nesnenin serileştirilmesi <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ile iyi çalışmaz.

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Visual Studio farklılıkları

**Özel durumlar ve hata ayıklama**

Hata ayıklayıcıda .NET Native kullanılarak derlenen uygulamalar çalıştırırken, ilk fırsat özel durumları aşağıdaki özel durum türleri için etkinleştirilir:

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**Uygulama oluşturma**

Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın. C:\Program Files (x86) \MSBuild\12.0\bin\amd64; dizininde bulunan AMD64 MSBuild araçlarının kullanılmasını önermiyoruz. Bunlar, derleme sorunları oluşturabilir.

**Profil oluşturucular**

- Visual Studio CPU Profiler ve XAML Memory Profiler yalnızca-Code 'u doğru bir şekilde görüntülemiyor.

- XAML bellek profili Oluşturucu yönetilen yığın verilerini doğru şekilde görüntülemez.

- CPU Profiler, modülleri doğru şekilde tanımlamaz ve önekli işlev adlarını görüntüler.

**Birim test kitaplığı projeleri**

Windows Mağazası uygulamaları projesi için bir birim testi kitaplığı üzerinde .NET Native etkinleştirme desteklenmez ve projenin derlenmesine neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Windows Mağazası uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
