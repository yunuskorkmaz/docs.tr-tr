---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce23d66f79f94af74250cff137499f6c8b1582ac
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
[!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamaların Windows Mağazası'nda veya geliştiricinin bilgisayarda statik derleme sağlar. Bu Windows mağazası uygulamaları için tam zamanında (JIT) derleyici tarafından gerçekleştirilen dinamik derleme farklıdır veya [yerel Görüntü Oluşturucu (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) cihazda. Farkları rağmen [!INCLUDE[net_native](../../../includes/net-native-md.md)] ile uyumluluğu korumak çalışır [.NET için Windows mağazası uygulamaları](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Çoğunlukla, .NET için Windows mağazası uygulamaları üzerinde çalışır şeyler de çalışmak [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Ancak, bazı durumlarda davranış değişiklikleri karşılaşabilirsiniz. Bu belge standart .NET için Windows mağazası uygulamaları arasındaki bu farklılıkları açıklar ve [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdaki alanlarda:  
  
-   [Genel çalışma zamanı farklar](#Runtime)  
  
-   [Dinamik programlama farkları](#Dynamic)  
  
-   [Yansıma ile ilgili diğer farklar](#Reflection)  
  
-   [Desteklenmeyen senaryolar ve API'leri](#Unsupported)  
  
-   [Visual Studio farklar](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Genel çalışma zamanı farklar  
  
-   Özel durumlar gibi <xref:System.TypeLoadException>, durum JIT Derleyici tarafından üzerinde ortak bir uygulama çalıştırdığında dil çalışma zamanı (CLR) genellikle neden tarafından işlendiğinde derleme zamanı hataları [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Çağrı yok <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> bir uygulamanın kullanıcı Arabirimi iş parçacığı yönteminden. Bu üzerinde bir kilitlenmeyle sonuçlanabilir [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Statik sınıf oluşturucu çağırma sıralama güvenmeyin. İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], çağırma sırası standart çalışma zamanı siparişte farklıdır. (Hatta standart çalışma zamanı ile statik sınıf oluşturucular yürütme terabayt güvenmemelisiniz.)  
  
-   Döngü sonsuz bir çağrı yapmaya gerek olmadan (örneğin, `while(true);`) herhangi bir iş parçacığı üzerinde uygulama durdurmak için getir. Benzer şekilde, büyük ya da sonsuz bekler uygulama getirin ve bu da durdurmak için.  
  
-   Bazı genel başlatma döngüleri özel durumlar oluşturma yok [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Örneğin, aşağıdaki atar kod bir <xref:System.TypeLoadException> standart CLR özel durum. İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], yoktur.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   Bazı durumlarda, [!INCLUDE[net_native](../../../includes/net-native-md.md)] .NET Framework sınıf kitaplıkları farklı uygulamaları sağlar. Bir yönteminden döndürülen nesne her zaman döndürülen tür üyeleri gerçekleştireceksiniz. Yedekleme uygulaması farklı olduğundan, Bununla birlikte, diğer .NET Framework platformlarda de türleri aynı kümesine yayınlanamıyor mümkün olabilir değil. Örneğin, bazı durumlarda, cast mümkün olmayabilir <xref:System.Collections.Generic.IEnumerable%601> gibi yöntemler tarafından döndürülen arabirimi nesnesi <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> veya <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> için `T[]`.  
  
-   WinINet önbellek .NET için Windows mağazası uygulamaları üzerinde varsayılan olarak etkin değildir, ancak açıktır [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Bu performansı artırır ancak kümesi etkileri çalışma sahiptir. Herhangi bir geliştirici eylemi gerekli değildir.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Dinamik programlama farkları  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] kodu en yüksek performans için uygulama yerel kod yapmak için .NET Framework ile statik olarak bağlar. Ancak, ikili boyutları tüm .NET Framework duruma getirilemiyor böylece küçük, kalması gerekir. [!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici kullanılmayan kod başvuruları kaldırır bir bağımlılık reducer kullanarak bu sınırlamaya giderir. Ancak, [!INCLUDE[net_native](../../../includes/net-native-md.md)] korumak veya olmayabilir bu bilgileri derleme zamanında statik olarak çıkarsanamıyor, ancak bunun yerine çalışma zamanında dinamik olarak alınır olduğunda bazı tür bilgilerini ve kod oluşturur.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Yansıma ve dinamik programlama etkinleştirin. Ancak, tüm türleri (özellikle .NET Framework'teki ortak API'ler yansıtacak şekilde desteklendiğinden) bu oluşturulan kod boyutu çok büyük yapmayacağı yansıma için işaretlenebilir. [!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici hangi türlerini yansıma desteklemesi ve meta veriler tutar ve yalnızca bu türleri için kod oluşturur akıllı seçenekler sağlar.  
  
 Örneğin, veri bağlama özellik adları işlevlere Eşle yapabilmek için bir uygulama gerekiyor. .NET için Windows mağazası uygulamalarında ortak dil çalışma zamanı yansıma yönetilen türler ve genel kullanıma açık yerel türleri için bu yeteneği sağlamak için otomatik olarak kullanır. İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], derleyici meta verileri için bağladığınız türleri için otomatik olarak ekler.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici de gibi yaygın olarak kullanılan genel türleri işlemek <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>, hangi herhangi bir ipuçları veya yönergeleri gerektirmeden çalışır. [Dinamik](~/docs/csharp/language-reference/keywords/dynamic.md) anahtar sözcüğü belirli sınırları içinde de desteklenir.  
  
> [!NOTE]
>  Tüm dinamik kod yollarının uygulamanıza bağlantı noktası oluşturma, sınamanız gerekir [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 İçin varsayılan yapılandırmayı [!INCLUDE[net_native](../../../includes/net-native-md.md)] için çoğu geliştirici, ancak bazı geliştiriciler ince yapılandırmalarına çalışma zamanı yönergeleri kullanarak ayarlama isteyebilirsiniz yeterlidir (. rd.xml) dosyası. Ayrıca, bazı durumlarda, [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici hangi meta verilerini yansıma için kullanılabilir olmalıdır ve ipuçları, aşağıdaki durumlarda özellikle dayanır belirlenemiyor:  
  
-   Bazı yapıları ister <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> statik olarak belirlenemez.  
  
-   Derleyici örneklemesi belirleyemediğinden yansıtmak istediğiniz genel bir tür çalışma zamanı yönergeleri tarafından belirtilmiş olması gerekir. Bu, yalnızca tüm kod dahil olması gerektiğinden, ancak genel türlerde yansıma sonsuz bir döngü (örneğin, genel türde bir genel yöntem çağrıldığında) form çünkü değildir.  
  
> [!NOTE]
>  Çalışma zamanı yönergeleri, bir çalışma zamanı yönergeleri tanımlanır (. rd.xml) dosyası. Bu dosyayı kullanma hakkında genel bilgi için bkz: [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md). Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Ayrıca profil varsayılan kümenin dışında hangi tür yansıma desteklemelidir belirlemek Geliştirici yardım araçları içerir.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Yansıma ile ilgili diğer farklar  
 Diğer tek yansıma ilgili arasındaki davranış farklılıkları .NET için Windows mağazası uygulamaları dizi vardır ve [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Özel yansıma türleri ve üyeleri .NET Framework Sınıf Kitaplığı'nda üzerinde desteklenmiyor. Ancak, kendi özel türleri ve üyeleri, yanı sıra türleri ve üçüncü taraf kitaplıklar üyelerinde üzerinden yansıtacak olabilir.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Özelliği doğru döndürür `false` için bir <xref:System.Reflection.ParameterInfo> dönüş değerini temsil eden nesne. .NET için Windows mağazası uygulamalarında döndürdüğü `true`. Ara dile (IL) bu doğrudan desteklemez ve dil yorumlama bırakılır.  
  
-   Ortak üye <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapıları desteklenmez. Bu tür yalnızca LINQ ifade ağaçları ve statik dizi başlatma için desteklenir.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> temel sınıflarda gizli üyeleri Ekle ve bu nedenle açık geçersiz kılmalar geçersiz kılınabilir. Bu ayrıca diğer geçerlidir [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) yöntemleri.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimleri (örneğin, ByRef'ler dizisi) oluşturmayı denediğinizde başarısız yok.  
  
-   İşaretçi parametrelere sahip üyeler çağrılacak yansıma kullanamazsınız.  
  
-   Yansıma almak veya bir işaretçi alanı ayarlamak için kullanamazsınız.  
  
-   Bağımsız değişken sayısı yanlış olduğunda ve bir bağımsız değişken türü geçersiz [!INCLUDE[net_native](../../../includes/net-native-md.md)] oluşturur bir <xref:System.ArgumentException> yerine bir <xref:System.Reflection.TargetParameterCountException>.  
  
-   İkili seri hale getirme özel durumların genellikle desteklenmiyor. Serileştirilebilir olmayan nesneler sonucu olarak eklenebilir <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlük.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Desteklenmeyen senaryolar ve API'leri  
 Aşağıdaki bölümlerde, genel geliştirme, birlikte çalışabilirlik ve HTTPClient ve Windows Communication Foundation (WCF) gibi teknolojileri için desteklenmeyen senaryolar ve API'leri listelenmektedir:  
  
-   [Genel Geliştirme](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [Desteklenmeyen API'leri](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Genel Geliştirme farklar  
 **Değer türleri**  
  
-   Geçersiz kılarsanız <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> ve <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> yöntemleri bir değer türü için temel sınıf uygulamaları çağrısı yok. .NET için Windows mağazası uygulamalarında bu yöntemleri yansıma kullanan. Derleme zamanında [!INCLUDE[net_native](../../../includes/net-native-md.md)] çalışma zamanı yansıma kullanan olmayan bir uygulama oluşturur. Bu iki yöntem geçersiz kılmaz, bunlar beklendiği gibi çünkü çalışmayacak, yani [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleme zamanında uygulaması oluşturur. Ancak, bu yöntemleri geçersiz kılma ancak temel sınıf uygulamasını çağıran bir özel durum oluşur.  
  
-   Bir megabayttan büyük değer türleri desteklenmez.  
  
-   Değer türleri varsayılan bir oluşturucu olamaz [!INCLUDE[net_native](../../../includes/net-native-md.md)]. (C# ve Visual Basic varsayılan oluşturucular değer türleri üzerinde engelliyor. Ancak, bunlar IL içinde oluşturulabilir.)  
  
 **Diziler**  
  
-   Sıfır dışındaki bir alt sınırı ile diziler desteklenmez. Genellikle, bu diziler çağrılarak oluşturulan <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.  
  
-   Çok boyutlu diziler dinamik oluşturulması desteklenmiyor. Bu tür diziler, genellikle bir aşırı yüklemesini çağrılarak oluşturulan <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> içeren yöntem bir `lengths` parametresi veya çağırarak <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi.  
  
-   Dört veya daha fazla boyutlarda çok boyutlu diziler desteklenmez; diğer bir deyişle, kendi <xref:System.Array.Rank%2A?displayProperty=nameWithType> özellik değeri olan dört veya daha büyük. Kullanım [basit dizileri](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (oluşan bir dizi) yerine. Örneğin, `array[x,y,z]` geçersiz, ancak `array[x][y][z]` değil.  
  
-   Çok boyutlu diziler için varyansı desteklenmiyor ve neden olan bir <xref:System.InvalidCastException> çalışma zamanında özel durum.  
  
 **Genel Türler**  
  
-   Sınırsız genel tür genişletme derleyici hataya yol açar. Örneğin, bu kodu derlemek başarısız olur:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **İşaretçiler**  
  
-   İşaretçileri diziler desteklenmez.  
  
-   Yansıma almak veya bir işaretçi alanı ayarlamak için kullanamazsınız.  
  
 **Serileştirme**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Öznitelik desteklenmez. Kullanım <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği.  
  
 **Kaynaklar**  
  
 Yerelleştirilmiş kaynaklar ile kullanımını <xref:System.Diagnostics.Tracing.EventSource> sınıfı desteklenmiyor. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Özellik yerelleştirilmiş kaynaklar tanımlamak değil.  
  
 **Temsilciler**  
  
 `Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.  
  
 **Async**  
  
 Görev IAsync aşırı mantığında iş parçacığı oluşturma desteklenmiyor.  
  
 **Çeşitli API'ler**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Özelliği atar bir <xref:System.PlatformNotSupportedException> özel durum, bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik türü için uygulanan değil. Kullanılan GUID öncelikle COM desteği.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Yöntemi doğru kısa tarihleri içeren dizeleri ayrıştırma [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Ancak, bu değişikliklerle uyumluluk tarih bilgisini korumaz ve ayrıştırma süresi Microsoft Bilgi Bankası makalelerinde açıklandığı [KB2803771](http://support.microsoft.com/kb/2803771) ve [KB2803755](http://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` içinde doğru yuvarlanır [!INCLUDE[net_native](../../../includes/net-native-md.md)]. CLR bazı sürümlerinde yerine Sonuç dizesini kesilir yuvarlanır.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>HttpClient farklar  
 İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> sınıfı WinINet düzenlenmemeli (aracılığıyla [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı) yerine <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> standart .NET için Windows mağazası uygulamalarında kullanılan sınıflar.  WinINet tüm desteklemiyor yapılandırma seçenekleri <xref:System.Net.Http.HttpClientHandler> sınıf destekler.  Sonuç olarak:  
  
-   Yetenek özelliklerinden bazıları <xref:System.Net.Http.HttpClientHandler> dönmek `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], döndürmeleri ancak `true` standart .NET için Windows mağazası uygulamalarında.  
  
-   Bazı yapılandırma özelliği `get` erişimciler her zaman geri sabit bir değer üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)] .NET için Windows mağazası uygulamalarında varsayılan yapılandırılabilir değerinden farklı.  
  
 Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.  
  
 **Proxy**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı, yapılandırma veya istek başına temelinde proxy geçersiz kılma desteklemiyor.  Tüm istekleri üzerinde yani [!INCLUDE[net_native](../../../includes/net-native-md.md)] yapılandırılmış sistemi proxy sunucusu veya değerine bağlı olarak hiçbir Ara sunucunun kullanmak <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> özelliği.  .NET için Windows mağazası uygulamalarında proxy sunucusu tarafından tanımlanan <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özelliği.  Üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayar <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> dışında bir değere `null` oluşturur bir <xref:System.PlatformNotSupportedException> özel durum.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Özelliği döndürür `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], onu verir kullanılabilirken `true` standart Windows mağazası için .NET Framework uygulamalarında.  
  
 **Otomatik yeniden yönlendirme**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı yapılandırılması için otomatik yeniden yönlendirme en fazla izin vermez.  Değeri <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> özelliği varsayılan olarak standart .NET için Windows mağazası uygulamaları 50'dir ve değiştirilebilir. Üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], bu özelliğin değeri 10 ve atar değiştirmeye çalışırken bir <xref:System.PlatformNotSupportedException> özel durum.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Özelliği döndürür `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], onu verir kullanılabilirken `true` .NET için Windows mağazası uygulamalarında.  
  
 **Otomatik açma**  
  
 .NET için Windows mağazası uygulamaları ayarlamanıza olanak tanır <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliğine <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, her iki <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.  [!INCLUDE[net_native](../../../includes/net-native-md.md)] yalnızca destekler <xref:System.Net.DecompressionMethods.Deflate> ile birlikte <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.  Ayarlanmaya çalışılırken <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> ya da özellik <xref:System.Net.DecompressionMethods.Deflate> veya <xref:System.Net.DecompressionMethods.GZip> tek başına sessizce hem de ayarlar <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Çerezler**  
  
 Tanımlama bilgisi işleme ile aynı anda gerçekleştirilen <xref:System.Net.Http.HttpClient> ve WinINet.  Tanımlama bilgilerini <xref:System.Net.CookieContainer> WinINet tanımlama bilgisi önbelleğinde tanımlama bilgisi ile birleştirilir.  Bir tanımlama bilgisinden kaldırma <xref:System.Net.CookieContainer> engeller <xref:System.Net.Http.HttpClient> ancak tanımlama bilgisi zaten WinINet tarafından görülen ve tanımlama bilgileri, kullanıcı tarafından silinmiş doğru tanımlama bilgisi, göndermesinin WinINet gönderir.  Program aracılığıyla kullanarak bir tanımlama bilgisi WinINet kaldırmak kurulamadığı <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, veya <xref:System.Net.CookieContainer> API.  Ayarı <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> özelliğine `false` yalnızca neden <xref:System.Net.Http.HttpClient> tanımlama bilgilerini; gönderilmesini durdurmak için WinINet istekte hala, tanımlama bilgileri içerebilir.  
  
 **kimlik bilgileri**  
  
 .NET için Windows mağazası uygulamalarında <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği kabul uygulayan herhangi bir nesne <xref:System.Net.ICredentials> arabirimi.  İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayar <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliğine `true` neden <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olmasını özelliği `null`.  Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca ayarlanabilir `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya bir nesne türü <xref:System.Net.NetworkCredential>.  Diğer atama <xref:System.Net.ICredentials> en popüler olduğu nesne <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği atar bir <xref:System.PlatformNotSupportedException>.  
  
 **Diğer desteklenmeyen veya unconfigurable özellikleri**  
  
 İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Değeri <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> özelliktir her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic>.  .NET için Windows mağazası uygulamalarında varsayılandır <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Özelliği yapılandırılabilir değildir.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Özelliktir her zaman `true`.  .NET için Windows mağazası uygulamalarında varsayılandır `false`.  
  
-   `SetCookie2` Yanıtları üstbilgisinde geçersiz yoksayılır.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Birlikte çalışma farklar  
 **Kullanım dışı API'leri**  
  
 Yönetilen kod ile birlikte çalışabilirlik için sık kullanılan API'leri sayısı kullanım dışı bırakıldı. İle kullanıldığında [!INCLUDE[net_native](../../../includes/net-native-md.md)], bu API'leri atabilir bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durum ya da bir derleyici hatası sonuçlanır. Derleyici Hatası yerine bir derleyici uyarısı oluşturur, bunları çağırma rağmen .NET için Windows mağazası uygulamalarında bu API'leri kullanılmayan olarak işaretlenir.  
  
 Kullanım dışı API'ler `VARIANT` hazırlama:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak ile kullanıldığında gibi bazı senaryolarda bir özel durum oluşturur [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) veya byref değişkenleri.  
  
 Kullanım dışı API'ler [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) destekler:  
  
|Tür|Üye|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|Öznitelik desteklenmiyor|  
  
 Kullanım dışı API'ler klasik COM olayları için:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 Kullanım dışı API'leri <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> içinde desteklenmeyen arabirimi [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
|Tür|Üye|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|Tüm üyeler.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|Tüm üyeler.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|Tüm üyeler.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 Başka desteklenmeyen birlikte çalışma özellikleri:  
  
|Tür|Üye|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|Tüm üyeler.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|Tüm üyeler.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 Sıralama API'leri nadiren kullanılır:  
  
|Tür|Üye|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **Platform çağırma ve COM birlikte çalışma uyumluluğu**  
  
 Çoğu platform çağırma ve COM birlikte çalışma senaryoları içinde hala desteklenmektedir [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Özellikle, Windows çalışma zamanı (WinRT) API ile tüm birlikte çalışabilirlik ve tüm hazırlama Windows çalışma zamanı için gerekli desteklenir. Bu, sıralama için destek içerir:  
  
-   Diziler (de dahil olmak üzere <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Temsilciler  
  
-   Dizeler (Unicode, ANSI ve HSTRING)  
  
-   Yapılar (`byref` ve `byval`)  
  
-   Birleşimler  
  
-   Win32 tanıtıcıları  
  
-   Tüm WinRT yapıları  
  
-   VARIANT türlerini hazırlama kısmi desteği. Aşağıdakiler desteklenir:  
  
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
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 Ancak, [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdakileri desteklemez:  
  
-   Klasik COM olaylarını kullanma  
  
-   Uygulama <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> yönetilen tür arabirimi  
  
-   Uygulama [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) yoluyla bir yönetilen türü arabirimde <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> özniteliği. Ancak, COM nesneleri aracılığıyla çağrılamıyor unutmayın `IDispatch`, ve yönetilen nesnenizin uygulayamaz `IDispatch`.  
  
 Bir platform çağrılacak yansıma kullanarak yöntem çağırma desteklenmiyor. Yöntem çağrısının içinde başka bir yöntem kaydırma ve bunun yerine sarmalayıcı çağrılacak yansıma kullanarak bu sınırlamaya geçici çalışabilirsiniz.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Diğer .NET API'leri için Windows mağazası uygulamaları arasındaki farklar  
 Bu bölüm içinde desteklenmeyen kalan API'ları listeler [!INCLUDE[net_native](../../../includes/net-native-md.md)]. En büyük desteklenmeyen API kümesidir Windows Communication Foundation (WCF) API'leri.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Türler <xref:System.ComponentModel.DataAnnotations> ve <xref:System.ComponentModel.DataAnnotations.Schema> ad alanları desteklenmeyen [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Bu, Windows 8 için .NET için Windows mağazası uygulamaları yok aşağıdaki türleri şunlardır:  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 **Visual Basic**  
  
 Visual Basic şu anda desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Aşağıdaki türleri <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> kullanılabilir olmayan ad alanlarını [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 **Yansıma bağlam (System.Reflection.Context ad alanı)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Sınıfı desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Sınıfı desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Türler [System.ServiceModel.* ad alanları](http://msdn.microsoft.com/library/gg145010.aspx) içinde desteklenmeyen [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Bunlar aşağıdaki türleri içerir:  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a>Serileştiricileri farklılıkları  
 Aşağıdaki farkları ilgilendiren seri hale getirme ve seri durumundan çıkarma ile <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları:  
  
-   İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serileştirmek veya seri durumdan, türü kök seri hale getirme türü olmayan bir taban sınıfı üyenin türetilmiş bir sınıf başarısız. Örneğin, aşağıdaki kodda serileştirmek veya seri durumdan çalışılırken `Y` hatayla sonuçlanır:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Tür `InnerType` taban sınıfı üyeleri seri hale getirme sırasında geçiş değil çünkü seri hale getirici için bilinen değil.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sınıf veya uygulayan yapısı serileştirmek başarısız <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, aşağıdaki türleri serileştirmek veya serisini kaldırmak başarısız olur:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> serileştirilecek nesnenin tam türü bilmiyor çünkü aşağıdaki nesne değeri serileştirmek başarısız olur:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> serileştirmek veya seri durumdan serileştirilmiş nesne türü buysa başarısız <xref:System.Xml.XmlQualifiedName>.  
  
-   Tüm serileştiricileri (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer>) türü seri hale getirme kodunu oluşturmak başarısız <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya içeren bir türü için <xref:System.Xml.Linq.XElement>. Bunun yerine, derleme zamanı hataları görüntüler.  
  
-   Seri hale getirme türlerinde şu oluşturuculardan beklendiği şekilde çalışması için garanti değil:  
  
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
  
-   <xref:System.Xml.Serialization.XmlSerializer> herhangi bir aşağıdaki özniteliklere öznitelikli yöntemleri olan bir türü için kod oluşturmanın başarısız olur:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> kabul etmez <xref:System.Xml.Serialization.IXmlSerializable> özel seri duruma getirme arabirimi. Bu arabirimi uygulayan bir sınıf varsa <xref:System.Xml.Serialization.XmlSerializer> türü düz bir eski CLR nesnesi (POCO) türü olarak değerlendirir ve yalnızca genel özellikleri serileştirir.  
  
-   Bir düz seri hale getirme <xref:System.Exception> aşağıdaki gibi nesne ile iyi işe yaramazsa <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Visual Studio farklar  
 **Özel durumlar ve hata ayıklama**  
  
 Ne zaman çalıştırdığınız kullanarak derlenmiş uygulamaları [!INCLUDE[net_native](../../../includes/net-native-md.md)] Hata Ayıklayıcısı'ndaki ilk fırsat özel durumlar için aşağıdaki özel durum türleri etkinleştirilir:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Yapı uygulamalar**  
  
 Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın. C:\Program Files (x86)\MSBuild\12.0\bin\amd64; bulunan AMD64 MSBuild araçları kullanarak öneririz yok Bu yapı sorunlara neden olabilir.  
  
 **Profil oluşturucular**  
  
-   Visual Studio CPU profil oluşturucu ve XAML bellek profil oluşturucu sadece kendi-kodumu doğru görüntülemiyor.  
  
-   XAML bellek profil oluşturucu doğru şekilde yönetilen yığın veri görüntülemez.  
  
-   CPU profil oluşturucu doğru modülleri belirlemek değil ve işlev adları görüntüler öneki.  
  
 **Birim testi kitaplık projeleri**  
  
 Etkinleştirme [!INCLUDE[net_native](../../../includes/net-native-md.md)] Birim Test kitaplığının bir Windows mağazası uygulamaları projesi desteklenmiyor ve projeyi oluşturmak başarısız olmasına neden olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [.NET için Windows mağazası uygulamalarına genel bakış](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
