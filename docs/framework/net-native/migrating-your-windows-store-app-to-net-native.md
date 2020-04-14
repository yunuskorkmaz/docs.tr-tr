---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 36f9ac4647b349ff379869f3415a5fb9e55228e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241951"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a>Windows Mağazası Uygulamanızı .NET Native'e geçirin

.NET Native, Windows Mağazası'ndaki veya geliştiricinin bilgisayarındaki uygulamaların statik derlemesini sağlar. Bu, Windows Mağazası uygulamaları için aygıttaki tam zamanında (JIT) derleyiciveya [Yerel Görüntü Üreteci (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) tarafından gerçekleştirilen dinamik derlemeden farklıdır. Farklılıklara rağmen,.NET Native [Windows Mağazası uygulamaları için .NET](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)ile uyumluluğu korumaya çalışır. Çoğunlukla, Windows Mağazası uygulamaları için .NET'te çalışan şeyler de .NET Native ile çalışır.  Ancak, bazı durumlarda davranış değişiklikleriyle karşılaşabilirsiniz. Bu belgede, Windows Mağazası uygulamaları için standart .NET ile aşağıdaki alanlarda .NET Native arasındaki farklar açıklanmaktadır:

- [Genel çalışma zamanı farkları](#Runtime)

- [Dinamik programlama farklılıkları](#Dynamic)

- [Yansımayla ilgili diğer farklar](#Reflection)

- [Desteklenmeyen senaryolar ve API'ler](#Unsupported)

- [Visual Studio farklılıkları](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>Genel çalışma zamanı farkları

- Bir uygulama ortak <xref:System.TypeLoadException>dil çalışma zamanında (CLR) çalıştığında JIT derleyicisi tarafından atılan , genellikle .NET Native tarafından işlendiğinde derleme zamanı hatalarına neden olur gibi özel durumlar.

- Yöntemi bir uygulamanın <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Ara Birimi iş parçacığından aramayın. Bu, .NET Native'de bir kilitlenmeyle sonuçlanabilir.

- Statik sınıf oluşturucu çağırma siparişine güvenmeyin. .NET Native'de çağırma sırası standart çalışma zamanındaki sıralamadan farklıdır. (Standart çalışma süresinde bile, statik sınıf oluşturucuların yürütme sırasına güvenmemeniz gerekir.)

- Herhangi bir iş parçacığı üzerinde bir `while(true);`arama yapmadan sonsuz döngü (örneğin, ) bir durma noktasına getirebilirsiniz. Benzer şekilde, büyük veya sonsuz beklemeler uygulamayı durdurabilir.

- Bazı genel başlatma döngüleri .NET Native'de özel durumlar belirlemez. Örneğin, aşağıdaki kod standart <xref:System.TypeLoadException> CLR bir özel durum atar. .NET Native'de öyle değil.

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- Bazı durumlarda,.NET Native .NET Framework sınıf kitaplıklarının farklı uygulamalarını sağlar. Yöntemden döndürülen bir nesne her zaman döndürülen türün üyelerini uygular. Ancak, destek uygulaması farklı olduğundan, diğer .NET Framework platformlarında olduğu gibi aynı tür kümesine döküm mümkün olmayabilir. Örneğin, bazı durumlarda, döndürülen arabirim <xref:System.Collections.Generic.IEnumerable%601> nesnesini <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`' gibi yöntemlerle atamayabilirsiniz.

- WinInet önbelleği Windows Mağazası uygulamaları için .NET'te varsayılan olarak etkinleştirilemez, ancak .NET Native'dedir. Bu, performansı artırır, ancak çalışma kümesi etkileri vardır. Geliştirici eylemi gerekmez.

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>Dinamik programlama farklılıkları

.NET Native, maksimum performans için kodu uygulama nın yerel olmasını sağlamak için .NET Framework'den kod olarak statik olarak bağlanır. Ancak, ikili boyutlar küçük kalmak zorunda, bu nedenle tüm .NET Framework getirilemez. .NET Native derleyicisi, kullanılmayan koda yapılan başvuruları kaldıran bir bağımlılık azaltıcısı kullanarak bu sınırlamayı çözer. Ancak,.NET Native, bu bilgiler derleme zamanında statik olarak çıkarılamadıklarında bazı tür bilgilerini ve kodlarını koruyamaz veya oluşturamaz, ancak bunun yerine çalışma zamanında dinamik olarak alınır.

.NET Native yansıma ve dinamik programlama sağlar. Ancak, bu, oluşturulan kod boyutunu çok büyük yapacağından (özellikle .NET Framework'deki genel API'lere yansıtılması desteklendiği için) tüm türler yansıma için işaretlenemez. .NET Native derleyicisi, hangi türlerin yansımayı desteklemesi gerektiği konusunda akıllı seçimler yapar ve meta verileri tutar ve yalnızca bu türler için kod oluşturur.

Örneğin, veri bağlama özelliği adlarını işlevlerle eşlenebilmek için bir uygulama gerekir. Windows Mağazası uygulamaları için .NET'te, yönetilen türler ve genel kullanıma açık yerel türler için bu özelliği sağlamak için ortak dil çalışma süresi otomatik olarak yansımayı kullanır. .NET Native'de derleyici, verileri bağladığınız türler için meta verileri otomatik olarak içerir.

.NET Native derleyicisi, herhangi bir ipucu <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602>veya yönerge gerektirmeden çalışan ve yaygın olarak kullanılan genel türleri de işleyebilir. [Dinamik](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) anahtar kelime de belirli sınırlar içinde desteklenir.

> [!NOTE]
> Uygulamanızı .NET Native'e aktarırken tüm dinamik kod yollarını iyice test etmeniz gerekir.

.NET Native için varsayılan yapılandırma çoğu geliştirici için yeterlidir, ancak bazı geliştiriciler çalışma zamanı yönergeleri (.rd.xml) dosyasını kullanarak yapılandırmalarında ince ayar yapmak isteyebilir. Buna ek olarak, bazı durumlarda ,NET Native derleyicisi hangi meta verilerin yansıtılması için kullanılabilir olması gerektiğini belirleyemiyor ve özellikle aşağıdaki durumlarda ipuçlarına dayanıyor:

- Bazı yapılar <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> statik <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> olarak gibi ve belirlenemez.

- Derleyici anlık açıklamaları belirleyemediğinden, yansıtmak istediğiniz genel bir tür çalışma zamanı yönergeleri tarafından belirtilmelidir. Bunun nedeni yalnızca tüm kodun eklenmesi gerektiği değil, genel türlere yansımanın sonsuz bir döngü oluşturabilmesidir (örneğin, genel bir yöntem genel bir türde çağrıldığında).

> [!NOTE]
> Çalışma zamanı yönergeleri bir çalışma zamanı yönergeleri (.rd.xml) dosyasında tanımlanır. Bu dosyayı kullanma hakkında genel bilgi için [başlarken](getting-started-with-net-native.md)bkz. Çalışma zamanı yönergeleri hakkında bilgi için [Runtime Yönergeleri (rd.xml) Yapılandırma Dosya Başvurusu'na](runtime-directives-rd-xml-configuration-file-reference.md)bakın.

.NET Native, geliştiricinin varsayılan küme dışındaki türlerin yansımayı desteklemesi gerektiğini belirlemesinde yardımcı olan profil oluşturma araçlarını da içerir.

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>Yansımayla ilgili diğer farklar

Windows Mağazası uygulamaları için .NET ile .NET Native arasında yansımayla ilgili diğer bireysel farklar vardır.

.NET Yerel olarak:

- .NET Framework sınıf kitaplığındaki türler ve üyeler üzerinde özel yansıma desteklenmez. Ancak, kendi özel türlerinizi ve üyelerinizi, üçüncü taraf kitaplıklarında türleri ve üyeleri yansıtabilirsiniz.

- Özellik, <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> iade `false` değerini <xref:System.Reflection.ParameterInfo> temsil eden bir nesne için doğru şekilde döndürür. Windows Mağazası uygulamaları için .NET'te geri döner. `true` Ara dil (IL) bunu doğrudan desteklemez ve yorumlama dile bırakılır.

- Kamu üyeleri <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapılar desteklenmez. Bu türler yalnızca LINQ, ifade ağaçları ve statik dizi başlatma için desteklenir.

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> temel sınıflarda gizli üyeleri içerir ve böylece açık geçersiz kılmalar olmadan geçersiz kılınabilir. Bu diğer [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) yöntemleri için de geçerlidir.

- <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli kombinasyonlar (örneğin, byrefs bir dizi) oluşturmaya çalıştığınızda başarısız olmayın.

- İşaretçi parametreleri olan üyeleri çağırmak için yansımayı kullanamazsınız.

- Bir işaretçi alanını almak veya ayarlamak için yansımayı kullanamazsınız.

- Bağımsız değişken sayısı yanlış sayılsa ve bağımsız değişkenlerden birinin <xref:System.ArgumentException> türü yanlışsa, .NET Native bir <xref:System.Reflection.TargetParameterCountException>. yerine bir

- Özel durumların ikili serileştirilmesi genellikle desteklenmez. Sonuç olarak, seri olarak izlenebilir olmayan nesneler <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğe eklenebilir.

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>Desteklenmeyen senaryolar ve API'ler

Aşağıdaki bölümlerde, httpclient ve Windows Communication Foundation (WCF) gibi genel geliştirme, interop ve teknolojiler için desteklenmeyen senaryolar ve API'ler listelenir:

- [Genel Geliştirme](#General)

- [httpİsteC](#HttpClient)

- [Interop](#Interop)

- [Desteklenmeyen API'ler](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>Genel gelişim farklılıkları

**Değer türleri**

- Değer türü için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> yöntemleri ve yöntemleri geçersiz kılarsanız, taban sınıf uygulamalarını aramayın. Windows Mağazası uygulamaları için .NET'te bu yöntemler yansımaya dayanır. Derleme zamanında ,NET Native çalışma zamanı yansımasına dayanmayan bir uygulama oluşturur. Bu, bu iki yöntemi geçersiz kılmazsanız, beklendiği gibi çalışacakları anlamına gelir, çünkü .NET Native uygulamayı derleme zamanında oluşturur. Ancak, bu yöntemleri geçersiz kılmak, ancak taban sınıf uygulamasını çağırmak bir özel durum la sonuçlanır.

- Bir megabayttan büyük değer türleri desteklenmez.

- Değer türlerinin .NET Native'de parametresiz bir oluşturucusu olamaz. (C# ve Visual Basic değer türlerinde parametresiz yapıcıları yasaklar. Ancak, bunlar IL'de oluşturulabilir.)

**Diziler**

- Sıfırdan daha düşük bir sınıra sahip diziler desteklenmez. Genellikle, bu diziler <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme çağırarak oluşturulur.

- Çok boyutlu dizilerin dinamik oluşturulması desteklenmez. Bu tür diziler genellikle bir <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> `lengths` parametre içeren yöntemin aşırı yüklenmesi çağırılarak veya <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi çağırarak oluşturulur.

- Dört veya daha fazla boyutu olan çok boyutlu diziler desteklenmez; diğer bir <xref:System.Array.Rank%2A?displayProperty=nameWithType> şey, onların mülkiyet değeri dört veya daha büyüktür. Bunun yerine [pürüzlü diziler](../../csharp/programming-guide/arrays/jagged-arrays.md) (diziler dizisi) kullanın. Örneğin, `array[x,y,z]` geçersizdir, ancak `array[x][y][z]` değil.

- Çok boyutlu diziler için varyans desteklenmez <xref:System.InvalidCastException> ve çalışma zamanında bir özel durum neden olur.

**Genel Türler**

- Sonsuz genel tür genişletme derleyici hatasıyla sonuçlanır. Örneğin, bu kodu derlemek için başarısız olur:

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**İşaretçiler**

- İşaretçiler dizileri desteklenmez.

- Bir işaretçi alanını almak veya ayarlamak için yansımayı kullanamazsınız.

**Serileştirme**

Öznitelik <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> desteklenmiyor. Bunun <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği kullanın.

**Kaynaklar**

Yerelleştirilmiş kaynakların <xref:System.Diagnostics.Tracing.EventSource> sınıfla kullanımı desteklenmez. Özellik <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> yerelleştirilmiş kaynakları tanımlamaz.

**Temsilciler**

`Delegate.BeginInvoke`ve `Delegate.EndInvoke` desteklenmez.

**Çeşitli API'ler**

- [TypeInfo.GUID](xref:System.Type.GUID) özelliği, türe <xref:System.PlatformNotSupportedException> bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik uygulanmıyorsa bir özel durum oluşturur. GUID öncelikle COM desteği için kullanılır.

- Yöntem, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> .NET Native'de kısa tarihler içeren dizeleri doğru bir şekilde ayrışdırır. Ancak, Microsoft Bilgi Bankası [makaleleri KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755)açıklanan tarih ve saat ayrıştırma değişiklikleri ile uyumluluğu korumaz.

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` .NET Native'de doğru bir şekilde yuvarlanır. CLR'nin bazı sürümlerinde, sonuç dizesi yuvarlatılmalı yerine kesilir.

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>Httpİstek farklılıkları

.NET Native'de <xref:System.Net.Http.HttpClientHandler> sınıf, Windows Mağazası uygulamaları <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> için standart .NET'te kullanılan sınıflar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar yerine dahili olarak WinINet kullanır.  <xref:System.Net.Http.HttpClientHandler> WinINet, sınıfın desteklediği tüm yapılandırma seçeneklerini desteklemez.  Sonuç olarak:

- .NET Native'de <xref:System.Net.Http.HttpClientHandler> `false` iade edilen bazı yetenek özellikleri, windows mağazası uygulamaları için standart .NET'te geri dönerken. `true`

- Yapılandırma özelliği `get` erişimcilerinden bazıları ,.NET Native'de windows mağazası uygulamaları için .NET'teki varsayılan yapılandırılabilir değerden farklı sabit bir değer döndürer.

Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.

**Proxy**

Sınıf, <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> proxy'yi istek başına yapılandırmayı veya geçersiz kılmayı desteklemez.  Bu, .NET Native'deki tüm <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> isteklerin, özelliğin değerine bağlı olarak sistem tarafından yapılandırılmış proxy sunucusunu kullandığı veya proxy sunucusu kullanmadığı anlamına gelir.  Windows Mağazası uygulamaları için .NET'te proxy <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> sunucusu özellik tarafından tanımlanır.  .NET Native'de, <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özel <xref:System.PlatformNotSupportedException> durum `null` atmak dışında bir değer ekidir.  Özellik <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> .NET Native'de döndürürken, `false` Windows Mağazası uygulamaları için standart .NET Framework'de döner. `true`

**Otomatik yeniden yönlendirme**

Sınıf, <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> en fazla otomatik yeniden yönlendirme sayısının yapılandırılmasına izin vermez.  Özelliğin <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> değeri, Windows Mağazası uygulamaları için standart .NET'te varsayılan olarak 50'dir ve değiştirilebilir. .NET Native'de, bu özelliğin değeri 10'dur ve <xref:System.PlatformNotSupportedException> değiştirmeye çalışmak bir özel durum oluşturur.  Özellik <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> .NET Native'de döndürürken, `false` Windows Mağazası uygulamaları için .NET'te döner. `true`

**Otomatik dekompresyon**

.NET Windows Mağazası uygulamaları için <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliği <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>her <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>ikisi <xref:System.Net.DecompressionMethods.None>ve , veya .  .NET Native <xref:System.Net.DecompressionMethods.Deflate> yalnızca <xref:System.Net.DecompressionMethods.GZip>' <xref:System.Net.DecompressionMethods.None>veya .  <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> Ya <xref:System.Net.DecompressionMethods.Deflate> da <xref:System.Net.DecompressionMethods.GZip> tek başına özelliği ayarlamak için çalışırken <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>sessizce hem de ayarlar .

**Çerezler**

Çerez işleme wininet <xref:System.Net.Http.HttpClient> tarafından aynı anda gerçekleştirilir.  <xref:System.Net.CookieContainer> Çerezler WinINet çerez önbelleğindeki çerezlerle birleştirilir.  Çerezin kaldırılması <xref:System.Net.CookieContainer> çerezin <xref:System.Net.Http.HttpClient> gönderilmesini engeller, ancak çerez WinINet tarafından zaten görüldüyse ve tanımlama bilgileri kullanıcı tarafından silinmediyse, WinINet çerezi gönderir.  Bir çerezi , veya <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.CookieContainer> API kullanarak WinINet'ten programlı bir şekilde kaldırmak mümkün değildir.  Özelliği <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> yalnızca `false` tanımlama <xref:System.Net.Http.HttpClient> bilgisi göndermeyi durdurmaya neden olacak şekilde ayarlamak; WinINet yine de istekteki çerezlerini ekleyebilir.

**Kimlik Bilgileri**

Windows Mağazası uygulamaları için .NET'te ve <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özellik <xref:System.Net.ICredentials> arabirimi uygulayan herhangi bir nesneyi kabul eder.  .NET Native'de, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliği `true` <xref:System.Net.Http.HttpClientHandler.Credentials%2A> `null`niçin .  Buna ek <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olarak, özellik yalnızca `null` <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya tür <xref:System.Net.NetworkCredential>bir nesne olarak ayarlanabilir.  Atanherhangi bir <xref:System.Net.ICredentials> nesne, en popüler <xref:System.Net.CredentialCache>olan , <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği ne <xref:System.PlatformNotSupportedException>atar .

**Diğer desteklenmeyen veya yapılandırılamayan özellikler**

.NET Yerel olarak:

- Özelliğin <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> değeri her <xref:System.Net.Http.ClientCertificateOption.Automatic>zaman .  Windows Mağazası uygulamaları için .NET'te varsayılan <xref:System.Net.Http.ClientCertificateOption.Manual>değer.

- Özellik <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> yapılandırılamaz.

- Mülkiyet <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> her `true`zaman .  Windows Mağazası uygulamaları için .NET'te varsayılan `false`değer.

- Yanıtlardaki `SetCookie2` üstbilgi eski olarak yoksayılır.

<a name="Interop"></a>
### <a name="interop-differences"></a>Interop farkları
 **Amortismana UYru'lar**

 Yönetilen kodla birlikte çalışabilirlik için seyrek kullanılan bir dizi API'ler amortismana kaldırıldı. .NET Native ile kullanıldığında, bu API'ler bir <xref:System.NotImplementedException> özel <xref:System.PlatformNotSupportedException> durum veya özel durum atabilir veya derleyici hatasına neden olabilir. Windows Mağazası uygulamaları için .NET'te bu API'ler eski olarak işaretlenir, ancak bunları çağırmak derleyici hatası yerine derleyici uyarısı oluşturur.

 Marshaling için `VARIANT` amortismana küçümsülen API'ler şunlardır:

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>desteklenir, ancak [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya byref türevleri ile kullanıldığında olduğu gibi bazı senaryolarda bir özel durum oluşturur.

 [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteği için amortismana hazır API'ler şunlardır:

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

Klasik COM etkinlikleri için amortismana hazır API'ler şunlardır:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

.NET Native'de desteklenmeyen <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> arabirimdeki amortismana kılmış API'ler şunlardır:

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(tüm üyeler)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(tüm üyeler)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(tüm üyeler)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

Diğer desteklenmeyen interop özellikleri şunlardır:

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(tüm üyeler)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(tüm üyeler)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 Nadiren kullanılan mareşalAP'lar:

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

 **Platform çağırma ve COM interop uyumluluğu**

 Çoğu platform çağrılabilir ve COM interop senaryoları hala .NET Native desteklenir. Özellikle, Windows Runtime (WinRT) API'leri ile birlikte çalışabilirlik ve Windows Runtime için gereken tüm mareşallik desteklenir. Bu, şunlar için mareşal desteği içerir:

- Diziler (dahil) <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>

- `BStr`

- Temsilciler

- Dizeleri (Unicode, Ansi ve HSTRING)

- Structs`byref` ( `byval`ve )

- Birleşimler

- Win32 kulpları

- Tüm WinRT yapıları

- Varyant türlerini mareşalleme için kısmi destek. Aşağıdakiler desteklenir:

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

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> Yönetilen bir türde arabirimi uygulama

- [Öznitelik](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) aracılığıyla yönetilen bir türüzerinde <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> IDispatch arabiriminin uygulanması. Ancak, COM nesnelerini aracılığıyla `IDispatch`çağıramayacağınızı ve yönetilen nesnenizin `IDispatch`uygulayamadığını unutmayın.

Bir platform çağırma yöntemi çağırmak için yansıma kullanma desteklenmez. Yöntem çağrısını başka bir yöntemde sararak ve bunun yerine sarmalayıcıyı aramak için yansımayı kullanarak bu sınırlamayı çözebilirsiniz.

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Windows Mağazası uygulamaları için .NET API'lerinden diğer farklar

Bu bölümde,.NET Native'de desteklenmeyen kalan API'ler listelenir. Desteklenmeyen API'lerin en büyük kümesi Windows Communication Foundation (WCF) API'leridir.

**DataAnnotations (System.ComponentModel.DataAnnotations)**

.NET Native'de ve <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> ad alanlarındaki türler desteklenmez. Bunlar, Windows 8 için Windows Mağazası uygulamaları için .NET'te bulunan aşağıdaki türleri içerir:

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

Visual Basic şu anda .NET Native'de desteklenmiyor. .NET Native'de aşağıdaki türler <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> ad boşlukları bulunmamaktadır:

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

**Yansıma Bağlamı (System.Reflection.Context namespace)**

Sınıf <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> .NET Native'de desteklenmez.

**RTC (System.Net.Http.Rtc)**

Sınıf `System.Net.Http.RtcRequestFactory` .NET Native'de desteklenmez.

**Windows İletişim Vakfı (WCF) (System.ServiceModel.\*)**

[System.ServiceModel.* ad alanlarındaki](xref:System.ServiceModel) türler .NET Native'de desteklenmez. Bunlar aşağıdaki türleri içerir:

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

### <a name="differences-in-serializers"></a>Serializers farklılıklar

Aşağıdaki farklar , <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve sınıflar ile serileştirme ve <xref:System.Xml.Serialization.XmlSerializer> deserialization ile ilgilidir:

- .NET Native'de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve <xref:System.Runtime.Serialization.DataContractSerializer> türü kök serileştirme türü olmayan bir taban sınıf üyesi olan türemiş bir sınıfı serihale getirmek veya deserialize etmek için başarısız. Örneğin, aşağıdaki kodda, bir hatayla sonuçlanırken `Y` sonuçları seri hale getirmeye veya deserialize etmeye çalışmak:

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  Tür `InnerType` serileştirici tarafından bilinmiyor, çünkü taban sınıfın üyeleri serileştirme sırasında geçiş yapmıyor.

- <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> arabirimi uygulayan bir sınıfı veya <xref:System.Collections.Generic.IEnumerable%601> yapıyı seri hale getirmekte başarısız olabilir. Örneğin, aşağıdaki türler serihale veya deserialize başarısız:

- <xref:System.Xml.Serialization.XmlSerializer>serihale edilecek nesnenin tam türünü bilmediğinden, aşağıdaki nesne değerini serihale getiremez:

- <xref:System.Xml.Serialization.XmlSerializer>serileştirilmiş nesnenin <xref:System.Xml.XmlQualifiedName>türü.

- Tüm serializers<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer>, , ve ) türü <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya içeren <xref:System.Xml.Linq.XElement>bir tür için serileştirme kodu oluşturmak için başarısız . Bunun yerine yapı zamanı hatalarını görüntülerler.

- Serileştirme türlerinin aşağıdaki oluşturucularının beklendiği gibi çalışması garanti değildir:

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <xref:System.Xml.Serialization.XmlSerializer>aşağıdaki özniteliklerden herhangi biriyle atfedilen yöntemleri olan bir tür için kod oluşturmak için başarısız olur:

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer>özel serileştirme <xref:System.Xml.Serialization.IXmlSerializable> arabirimini onurlandırmaz. Bu arabirimi uygulayan bir sınıfvarsa, <xref:System.Xml.Serialization.XmlSerializer> türü düz eski CLR nesnesi (POCO) türünü dikkate alır ve yalnızca ortak özelliklerini serileştirir.

- Düz bir <xref:System.Exception> nesneyi seri hale <xref:System.Runtime.Serialization.DataContractSerializer> getirmek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>iyi çalışmaz ve .

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Visual Studio farklılıkları

**Özel durumlar ve hata ayıklama**

Hata ayıklamada .NET Native kullanarak derlenen uygulamaları çalıştırırken, aşağıdaki özel durum türleri için ilk şans özel durumları etkinleştirilir:

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**Uygulama oluşturma**

Visual Studio tarafından varsayılan olarak kullanılan x86 yapı araçlarını kullanın. C:\Program Files (x86)\MSBuild\12.0\bin\amd64 bulunur AMD64 MSBuild araçları, kullanmanızı öneririz; bunlar yapı sorunları yaratabilir.

**Profilleyicilerini**

- Visual Studio CPU Profiler ve XAML Memory Profiler Just-My-Code'u doğru görüntülemez.

- XAML Memory Profiler yönetilen yığın verilerini doğru bir şekilde görüntülemez.

- CPU Profiler modülleri doğru tanımlamaz ve önceden belirlenmiş işlev adlarını görüntüler.

**Ünite Test Kitaplığı projeleri**

Bir Windows Mağazası uygulamaları projesi için Birim Test Kitaplığı'nda .NET Native'i etkinleştirmek desteklenmez ve projenin oluşturulmasında başarısız olması nedeniyle.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [.NET Windows Mağazası uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
