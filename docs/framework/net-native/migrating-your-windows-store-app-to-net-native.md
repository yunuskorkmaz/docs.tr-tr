---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 126276840ee12bdba99f5ce1c164762340bb580c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155281"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
.NET yerel uygulamaları Windows Store veya Geliştirici bilgisayara statik derlenmesini sağlar. Bu Windows Store uygulamaları için tam zamanında (JIT) derleyici tarafından gerçekleştirilen dinamik derlemeden farklıdır veya [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) cihazda. Farklar rağmen .NET Native ile uyumluluğu korumak çalışır [.NET için Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29). Çoğunlukla, .NET için Windows Store uygulamaları iş öğeleri de .NET Native ile çalışır.  Ancak, bazı durumlarda, davranış değişiklikleri karşılaşabilirsiniz. Bu belge aşağıdaki alanlarda standart .NET için Windows Store uygulamaları ve .NET Native arasındaki farklar açıklanır:  
  
-   [Genel çalışma zamanı farkları](#Runtime)  
  
-   [Dinamik programlama farkları](#Dynamic)  
  
-   [Yansıma ile ilgili diğer farklar](#Reflection)  
  
-   [Desteklenmeyen senaryolar ve API'ler](#Unsupported)  
  
-   [Visual Studio farkları](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Genel çalışma zamanı farkları  
  
-   Özel durumlar gibi <xref:System.TypeLoadException>, durum JIT derleyicisi tarafından üzerinde ortak bir uygulama çalıştırdığında dil çalışma zamanı (CLR) .NET Native tarafından işlendiğinde derleme zamanı hatalarına genellikle sonuçlanır.  
  
-   Remove() çağırmayın <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> uygulamanın UI iş parçacığından yöntemi. Bu karşılıklı bir kilitlenme .NET Native neden olabilir.  
  
-   Statik sınıf oluşturucu çağrı sırası güvenmeyin. .NET Native çağırma farklı standart çalışma zamanı üzerinde sırasıdır. (Hatta standart çalışma zamanıyla statik sınıf oluşturucuları yürütülmesini bazında güvenmemelisiniz.)  
  
-   Döngü sonsuz bir çağrı yapmadan (örneğin, `while(true);`) herhangi bir iş parçacığı üzerinde bir durdurmak için uygulamayı getir. Benzer şekilde, büyük ya da sonsuz bekler, bir durdurmak için uygulamayı getiriyor.  
  
-   Bazı genel başlatma döngüleri özel .NET Native durumlar yok. Örneğin, aşağıdaki oluşturur kod bir <xref:System.TypeLoadException> standart CLR özel durum. .NET Native içinde bu değil.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   Bazı durumlarda, .NET Framework sınıf kitaplıkları farklı uygulamaları .NET Native sağlar. Yöntemi tarafından döndürülen bir nesne, döndürülen tür üyelerinin her zaman uygular. Yedekleme uygulaması farklı olduğundan, ancak, diğer .NET Framework platformunda çalışan de aynı türleri kümesi için tür dönüştürme mümkün olmayabilir. Örneğin, bazı durumlarda, size bir şekilde yayınlanabilirler olmayabilir <xref:System.Collections.Generic.IEnumerable%601> arabirimi nesnesi gibi yöntemler tarafından döndürülen <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> veya <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> için `T[]`.  
  
-   Varsayılan olarak .NET için Windows Store apps WinInet önbelleğinde etkin değil ancak .NET Native üzerinde olacaktır. Bu durum peformansı artırmasına karşın çalışma kümesi etkileri vardır. Herhangi bir geliştirici eylemi gerekli değildir.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Dinamik programlama farkları  
 .NET native statik olarak en yüksek performans için uygulama yerel kod yapmak için .NET Framework kodundaki bağlar. Ancak, ikili boyutları küçük kalır. böylece, tüm .NET Framework yapılamıyor gerekir. .NET yerel derleyici, kullanılmayan kod başvurularını kaldırır bir bağımlılık Azaltıcı kullanarak bu sınırlama çözümler. Ancak, .NET Native korumak veya olmayabilir bu bilgiler, statik olarak derleme zamanında çıkarsanamıyor, ancak bunun yerine çalışma zamanında dinamik olarak alınır olduğunda bazı tür bilgilerini ve kod oluşturur.  
  
 .NET native yansıtma ve dinamik programlama etkinleştirmez. Ancak, tüm türleri (özellikle .NET Framework'teki ortak API'lerde yansıtan desteklendiğinden) bu oluşturulan kod boyutu çok büyük yapacağı için yansıma için işaretlenebilir. .NET yerel derleyici, yansıma türlerini desteklemesi ve hakkında meta veriler tutar ve yalnızca bu türleri için kod oluşturur akıllı seçimlerini yapar.  
  
 Örneğin, veri bağlama işlevleri için özellik adlarını eşleştirmek için uygulama gerektiriyor. .NET için Windows Store uygulamalarında ortak dil çalışma zamanı yansıma yönetilen türleri ve genel kullanıma açık yerel türler için bu yeteneği vermek otomatik olarak kullanır. .NET Native, derleyici, otomatik olarak veri bağlama türleri için meta verileri içerir.  
  
 .NET derleyici ayrıca işleyebilir genellikle yerel genel türler gibi kullanılan <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>, hangi ipuçlarının ya da yönergeleri gerektirmeden çalışır. [Dinamik](~/docs/csharp/language-reference/keywords/dynamic.md) anahtar sözcüğü de bazı sınırlar içinde desteklenir.  
  
> [!NOTE]
>  Tüm dinamik kod yolları .NET Native uygulamanıza taşırken sınamanız gerekir.  
  
 .NET Native için varsayılan yapılandırma Çoğu geliştirici için yeterli olmakla birlikte, bazı geliştiriciler ince yapılandırmalarına bir çalışma zamanı yönergeleri kullanarak ayarlama isteyebilirsiniz (. rd.xml) dosyası. Ayrıca, bazı durumlarda, .NET yerel derleyici hangi meta verilerini yansıma için kullanılabilir olmalıdır ve ipuçları, özellikle aşağıdaki durumlarda dayanan belirlenemiyor:  
  
-   Bazı yapıları ister <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> statik olarak belirlenemez.  
  
-   Derleyici örneklemeleri belirleyemediğinden yansıtmak istediğiniz genel bir tür tarafından çalışma zamanı yönergeleri belirtilmelidir. Bu, yalnızca tüm kod dahil olması gerektiğinden, ancak genel türlerde yansıma (örneğin, genel türde bir genel yöntem çağrıldığında) sonsuz bir döngü oluşturur çünkü değildir.  
  
> [!NOTE]
>  Çalışma zamanı yönergeleri, bir çalışma zamanı yönergeleri tanımlanır (. rd.xml) dosyası. Bu dosyayı kullanma hakkında genel bilgi için bkz. [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md). Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 .NET native ayrıca profil varsayılan dışındaki hangi tür yansıma desteklemelidir belirlemek geliştiricilere araçları içerir.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Yansıma ile ilgili diğer farklar  
 Diğer tek tek yansıma ilgili arasındaki davranış farklılıkları .NET için Windows Store uygulamaları ve .NET Native vardır.  
  
 .NET yerel:  
  
-   Özel yansıma üzerinden türler ve üyeler .NET Framework Sınıf Kitaplığı'nda desteklenmiyor. Ancak, kendi özel türler ve üyeler, hem de türler ve üyeler üçüncü taraf kitaplıklarındaki üzerinden yansıtacak olabilir.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Özelliği doğru bir şekilde döndürür `false` için bir <xref:System.Reflection.ParameterInfo> dönüş değeri temsil eden nesne. .NET için Windows Store uygulamalarında döndürür `true`. Ara dil (IL) bu doğrudan desteklemez ve dil yorumu kaldı.  
  
-   Ortak üyelerde <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapıları desteklenmez. Bu tür, yalnızca LINQ ifade ağaçları ve statik dizi başlatma için desteklenir.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> taban sınıflardaki gizli üyeleri içerir ve bu nedenle açık geçersiz kılmalar geçersiz kılınabilir. Bu ayrıca diğer true [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) yöntemleri.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimleri (örneğin, zkratka dizisi) oluşturmaya çalıştığınızda başarısız yok.  
  
-   Yansıma, işaretçi parametrelere sahip bir üye çağırmak için kullanamazsınız.  
  
-   Alınacak veya ayarlanacak bir işaretçi alan yansıma kullanamazsınız.  
  
-   .NET Native oluşturur, bağımsız değişken sayısı yanlış olduğunda ve bağımsız değişkenler birinin türü yanlış bir <xref:System.ArgumentException> yerine bir <xref:System.Reflection.TargetParameterCountException>.  
  
-   İkili serileştirme özel durumlar genellikle desteklenmiyor. Seri hale getirilemeyen nesneleri sonucu olarak eklenebilir <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğü.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Desteklenmeyen senaryolar ve API'ler  
 Aşağıdaki bölümlerde, genel geliştirme, birlikte çalışabilirlik ve HTTPClient ve Windows Communication Foundation (WCF) gibi teknolojiler için desteklenmeyen senaryolar ve API'leri listelenmektedir:  
  
-   [Genel Geliştirme](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [Desteklenmeyen API'leri](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Genel Geliştirme farkları  
 **Değer türleri**  
  
-   Kılarsanız <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> ve <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> bir değer türü için yöntemleri taban sınıf uygulamaları çağrı yok. .NET için Windows Store uygulamalarında yansıma bu yöntemleri kullanan. Derleme zamanında .NET yerel çalışma zamanı yansıma kullanan olmayan bir uygulama oluşturur. Bu, bu iki yöntem geçersiz kılmazsanız .NET yerel derleme zamanında bir uygulama oluşturur çünkü bunlar beklendiği gibi çalışmasını anlamına gelir. Ancak, bu yöntemleri geçersiz ancak taban sınıf uygulamasını çağırmak bir özel durum oluşur.  
  
-   Bir megabayttan büyük değer türleri desteklenmez.  
  
-   Değer türleri, varsayılan bir oluşturucu .NET Native sahip olamaz. (C# ve Visual Basic değer türleri üzerinde varsayılan oluşturucular yasaktır. Ancak, bunlar IL içinde oluşturulabilir.)  
  
 **Diziler**  
  
-   Alt sınırı sıfır dışındaki dizilerle desteklenmez. Genellikle, bu dizileri çağrılarak oluşturulmuş <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.  
  
-   Dinamik oluşturulmasını çok boyutlu diziler desteklenmiyor. Bu tür diziler, genellikle bir aşırı yüklemesini çağırarak oluşturulan <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> içeren yöntem bir `lengths` parametresi veya çağırarak <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi.  
  
-   Dört veya daha fazla boyuta sahip çok boyutlu diziler desteklenmez; diğer bir deyişle, kendi <xref:System.Array.Rank%2A?displayProperty=nameWithType> özellik değeri, dört veya daha büyük. Kullanım [basit dizileri](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (dizi) bunun yerine. Örneğin, `array[x,y,z]` geçersiz, ancak `array[x][y][z]` değil.  
  
-   Çok boyutlu diziler için varyans desteklenmiyor ve neden olan bir <xref:System.InvalidCastException> çalışma zamanında özel durum.  
  
 **Genel Türler**  
  
-   Sınırsız genel tür genişletme bir derleyici hatasına neden olur. Örneğin, bu kodu derlemek başarısız olur:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **İşaretçiler**  
  
-   İşaretçileri dizilerini desteklenmez.  
  
-   Alınacak veya ayarlanacak bir işaretçi alan yansıma kullanamazsınız.  
  
 **Serileştirme**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Özniteliği desteklenmiyor. Kullanım <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği.  
  
 **Kaynaklar**  
  
 Yerelleştirilmiş kaynaklar ile kullanımını <xref:System.Diagnostics.Tracing.EventSource> sınıfı desteklenmiyor. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Özelliği, yerelleştirilmiş kaynaklar tanımlamıyor.  
  
 **Temsilciler**  
  
 `Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.  
  
 **Çeşitli API'ler**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Özelliği oluşturur bir <xref:System.PlatformNotSupportedException> özel durum, bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik türü için uygulanan değil. GUID kullanılan birincil COM desteği.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Yöntemi .NET Native kısa tarihler içeren dizeleri doğru bir şekilde ayrıştırılır. Ancak, tarih değişikliği uyumluluk saklamaz ve zaman ayrıştırma Microsoft Bilgi Bankası makalelerinde açıklandığı [KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` doğru .NET Native yuvarlanır. CLR'nin bazı sürümleri, sonuç dizesine yerine kesilmiş yuvarlanır.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>HttpClient farkları  
 .NET Native içinde <xref:System.Net.Http.HttpClientHandler> sınıfı dahili olarak, WinINet kullanır (aracılığıyla <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> sınıfı) yerine <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> standart .NET için Windows Store uygulamalarında kullanılan sınıflar.  WinINet tüm desteklemiyor yapılandırma seçeneklerini <xref:System.Net.Http.HttpClientHandler> sınıfı destekler.  Sonuç olarak:  
  
-   Özellik özellikleri bazıları <xref:System.Net.Http.HttpClientHandler> dönüş `false` .NET Native üzerinde döndürmeleri ise `true` standart .NET için Windows Store uygulamalarında.  
  
-   Bazı yapılandırma özelliği `get` erişimcileri her zaman bir sabit değer döndürür üzerinde .NET, .NET için Windows Store apps varsayılan yapılandırılabilir değeri farklı olan yerel.  
  
 Bazı ek davranış farklılıklarının aşağıdaki alt bölümlerde ele alınmıştır.  
  
 **Proxy**  
  
 <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Sınıfı, yapılandırma veya istek başına temelinde proxy geçersiz kılmayı desteklemez.  Bu .NET Native tüm istekleri sistem yapılandırılmış bir proxy sunucusu veya değerine bağlı olarak, proxy sunucusu kullanmak anlamına gelir <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> özelliği.  .NET için Windows Store uygulamalarında proxy sunucusu tarafından tanımlanan <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özelliği.  Ayarı .NET Native üzerinde <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> dışında bir değere `null` oluşturur bir <xref:System.PlatformNotSupportedException> özel durum.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Özelliği döndürür `false` .NET Native üzerinde döndürür ancak `true` standart .NET Framework için Windows Store uygulamalarında.  
  
 **Otomatik yeniden yönlendirme**  
  
 <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Sınıfı yapılandırılması için otomatik yeniden yönlendirmeleri sayısı izin vermez.  Değerini <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> özelliği varsayılan olarak standart .NET için Windows Store apps 50'dir ve değiştirilebilir. .NET Native üzerinde bu özelliğin değeri 10 ve atar değiştirmeye çalışırken bir <xref:System.PlatformNotSupportedException> özel durum.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Özelliği döndürür `false` .NET Native üzerinde döndürür ancak `true` .NET için Windows Store uygulamalarında.  
  
 **Otomatik Sıkıştırma**  
  
 .NET için Windows Store apps ayarlamanıza olanak tanır <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>hem <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.  Yalnızca .NET native destekler <xref:System.Net.DecompressionMethods.Deflate> ile birlikte <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.  Ayarlanmaya çalışılırken <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> ya da özellik <xref:System.Net.DecompressionMethods.Deflate> veya <xref:System.Net.DecompressionMethods.GZip> tek başına sessizce hem de ayarlar <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Çerezler**  
  
 Tanımlama bilgisi işleme ile aynı anda gerçekleştirilen <xref:System.Net.Http.HttpClient> ve WinINet.  Tanımlama bilgilerine <xref:System.Net.CookieContainer> WinINet tanımlama bilgisi önbelleğinde tanımlama bilgileri ile birleştirilir.  Tanımlama bilgisinden kaldırma <xref:System.Net.CookieContainer> engeller <xref:System.Net.Http.HttpClient> tanımlama bilgisi, zaten WinINet tarafından görülen ve tanımlama bilgileri, kullanıcı tarafından silinmiş olmayan ancak tanımlama bilgisi göndermesini WinINet gönderir.  Program aracılığıyla kullanarak bir tanımlama bilgisi WinINet kaldırmak mümkün değildir <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, veya <xref:System.Net.CookieContainer> API.  Ayarı <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> özelliğini `false` yalnızca neden <xref:System.Net.Http.HttpClient> tanımlama bilgileri göndermeyi durdurun WinINet, yine de isteğinde, tanımlama bilgileri içerebilir.  
  
 **Kimlik bilgileri**  
  
 .NET için Windows Store uygulamalarında <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği uygulayan nesne kabul eden <xref:System.Net.ICredentials> arabirimi.  Ayarı .NET Native içinde <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliğini `true` neden <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olacak özelliği `null`.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca ayarlanabilir `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya bir nesne türü <xref:System.Net.NetworkCredential>.  Diğer atama <xref:System.Net.ICredentials> en popüler olan nesne, <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği oluşturur bir <xref:System.PlatformNotSupportedException>.  
  
 **Diğer desteklenmeyen veya unconfigurable özellikleri**  
  
 .NET yerel:  
  
-   Değerini <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> özelliği her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic>.  .NET için Windows Store uygulamalarında varsayılandır <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Özelliği yapılandırılabilir değildir.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Özelliği her zaman `true`.  .NET için Windows Store uygulamalarında varsayılandır `false`.  
  
-   `SetCookie2` Yanıtları üstbilgisinde eski olarak sayılır.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Birlikte çalışma farkları  
 **Kaldırılmış API'ler**  
  
 Yönetilen kod ile birlikte çalışabilirlik için sık kullanılan API'ler birkaç kullanım dışı bırakıldı. Bu API'ler .NET Native ile kullanıldığında, oluşturabilecek bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durum ya da bir derleyici hatası sonuçlanır. Bunların çağrılması bir derleyici hatası yerine derleyici uyarısı oluşturur ancak .NET için Windows Store uygulamalarında bu API'leri eski işaretlendi.  
  
 API'ler için kullanım dışı `VARIANT` hazırlamayı içerir:  

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak bir özel durum ile kullanıldığında gibi bazı senaryolarda oluşturur [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya türevleri byref.  
  
 API'ler için kullanım dışı [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteğini içerir:  
  
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName> 
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>  

Kaldırılmış API'ler klasik COM olayları için şunları içerir:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>
  
Kullanım dışı API'leri <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> .NET Native desteklenmiyor, arabirim gösterilebilir:  
  
- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (tüm üyeler)  
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (tüm üyeler)  
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (tüm üyeler)  
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>  
  
Diğer desteklenmeyen birlikte çalışma özellikleri şunlardır:  
  
- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (tüm üyeler)  
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (tüm üyeler)  
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>  
  
 Hazırlama API nadiren kullanılır:  
  
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
  
 Çoğu platform çağırma ve COM birlikte çalışma senaryolar hala .NET Native desteklenir. Özellikle, Windows çalışma zamanı (WinRT) API'leri ile tüm birlikte çalışabilirlik ve Windows çalışma zamanı için gerekli tüm hazırlama desteklenir. Bu, sıralama için destek içerir:  
  
-   Diziler (dahil olmak üzere <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Temsilciler  
  
-   Dizeler (Unicode, ANSI ve HSTRING)  
  
-   Yapılar (`byref` ve `byval`)  
  
-   Birleşimler  
  
-   Win32 tanıtıcıları  
  
-   Tüm WinRT yapıları  
  
-   VARIANT türlerini hazırlama için kısmi destek. Aşağıdakiler desteklenir:  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 Ancak, .NET Native aşağıdakileri desteklemez:  
  
-   Kullanarak klasik COM olayları  
  
-   Uygulama <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> yönetilen tür arabirimi  
  
-   Uygulama [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimi yönetilen türe göre <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> özniteliği. Ancak, COM nesneleri aracılığıyla çağrılamıyor unutmayın `IDispatch`, ve yönetilen nesnenizin uygulayamaz `IDispatch`.  
  
 Yansıma kullanarak bir platform çağırma yöntemi çağırma desteklenmiyor. Başka bir yöntem yöntem çağrısının sarmalama ve bunun yerine sarmalayıcı çağırmak için yansıma kullanarak bu sınırlandırma çerçevesinde çalışabilirsiniz.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>.NET API için Windows Store uygulamalarından diğer farklar  
 Bu bölüm .NET Native desteklenmeyen kalan API'ları listeler. Windows Communication Foundation (WCF) API'leri en büyük dizi desteklenmeyen API var.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Türlerinde <xref:System.ComponentModel.DataAnnotations> ve <xref:System.ComponentModel.DataAnnotations.Schema> ad alanları .NET Native desteklenmez. Bu, Windows 8 için .NET için Windows Store apps bulunan aşağıdaki türleri şunlardır:  
  
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
  
 Visual Basic .NET Native şu anda desteklenmemektedir. Aşağıdaki türleri içinde <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> ad alanları .NET Native kullanıma sunulmaz:  

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
  
 **Yansıma bağlam (System.Reflection.Context ad alanı)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Sınıfı .NET Native desteklenmez.  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Sınıfı .NET Native desteklenmez.  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Türlerinde [System.ServiceModel.* ad alanları](xref:System.ServiceModel) .NET Native desteklenmez. Bunlar aşağıdaki türleri içerir:  
  
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
  
### <a name="differences-in-serializers"></a>Seri hale getiricileri genişletme farklılıkları  
 Aşağıdaki farklar ilgilendiriyor serileştirme ve seri durumdan çıkarma ile <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıflar:  
  
-   .NET Native içinde <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serileştirmek veya seri durumdan türü olmayan bir kök serileştirme türü bir temel sınıf üyesinin türetilmiş bir sınıf başarısız. Örneğin, aşağıdaki kodda, serileştirmek veya seri durumdan çalışılırken `Y` hatayla sonuçlanır:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Tür `InnerType` seri hale getirici için temel sınıf üyelerini serileştirme sırasında geçiş değildir çünkü bilinen değil.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sınıf veya yapı uygulayan serileştirmek başarısız <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, aşağıdaki türleri serileştirmek veya seri durumdan çıkarmak başarısız:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> serileştirilecek nesnenin tam tür bilmediği aşağıdaki nesne değeri serileştirmek başarısız olur:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> serileştirmek veya seri hale getirilmiş nesne türü ise seri durumdan başaramıyor <xref:System.Xml.XmlQualifiedName>.  
  
-   Tüm seri hale getiricileri genişletme (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer>) tür için serileştirme kod oluşturmak başarısız <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ya da içeren bir tür için <xref:System.Xml.Linq.XElement>. Bunlar bunun yerine derleme zamanı hataları görüntüleyin.  
  
-   Seri hale getirme türlerinde şu oluşturuculardan beklendiği şekilde çalışması için garantili değildir:  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Aşağıdaki özniteliklerden birini öznitelikli yöntem olan bir türü için kod oluşturmak üzere başarısız olur:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> ne uygun olmayan <xref:System.Xml.Serialization.IXmlSerializable> özel seri hale getirme arabirimi. Bu arabirimi uygulayan bir sınıf varsa <xref:System.Xml.Serialization.XmlSerializer> türü düz eski bir CLR nesnesi (POCO) türü olarak değerlendirir ve yalnızca genel özelliklerini serileştirir.  
  
-   Düz bir'seri hale getirme <xref:System.Exception> aşağıdaki gibi bir nesne ile iyi çalışmaz <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Visual Studio farkları  
 **Özel durumlar ve hata ayıklama**  
  
 .NET yerel hata ayıklayıcıda kullanılarak derlenmiş uygulamalar çalıştırırken, ilk şans özel durumlar aşağıdaki özel durum türleri için etkinleştirilir:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Uygulamaları oluşturma**  
  
 Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın. C:\Program Files (x86)\MSBuild\12.0\bin\amd64; bulunan AMD64 MSBuild araçları kullanımı önerilmemektedir Bu derleme sorunlara neden olabilir.  
  
 **Profil oluşturucular**  
  
-   Visual Studio CPU Profiler ve XAML bellek Profiler Just My-kod düzgün görüntülemez.  
  
-   XAML bellek Profiler, yönetilen yığın verileri doğru bir şekilde görüntülemez.  
  
-   CPU Profiler doğru modülleri belirlemek değil ve işlev adlarını görüntüler öneki.  
  
 **Birim testi kitaplığı projeleri**  
  
 .NET yerel bir Windows Store uygulamaları projesi için bir birim testi kitaplığı üzerindeki etkinleştirme desteklenmez ve projeyi oluşturmak başarısız olmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)  
 [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
