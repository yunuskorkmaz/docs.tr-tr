---
title: İzleme Uygulamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework]
- debugging [.NET Framework], instrumentation
- performance monitoring, instrumentation
- instrumentation, about instrumentation
- tracing [.NET Framework], about tracing
- performance monitoring, tracing code
- Trace class, instrumentation for .NET applications
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42665b3b971f9026bf49aeb081017521eab0117f
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796744"
---
# <a name="tracing-and-instrumenting-applications"></a>İzleme Uygulamaları
İzleme, çalışırken uygulamanızın yürütülmesini izlemenize yönelik bir yoldur. Geliştirme sırasında .NET Framework uygulamanıza izleme ve hata ayıklama araçları ekleyebilirsiniz ve bu araçları, uygulamayı geliştirirken ve dağıttıktan sonra kullanabilirsiniz. <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ,<xref:System.Diagnostics.Debug?displayProperty=nameWithType>Ve sınıflarını<xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> , daha sonra analiz edilmek üzere günlüklerde, metin dosyalarında veya diğer cihazlarda hatalar ve uygulama yürütme bilgilerini kaydetmek için kullanabilirsiniz.  
  
 Dönem *araçları* , bir ürünün performansının düzeyini izleyip ölçmenize ve hataları tanılamaya yönelik bir özellik anlamına gelir. Programlamada, bu, bir uygulamanın bu şekilde dahil olduğu anlamına gelir:  
  
- **Kod izleme** -bir uygulamanın çalışma zamanında yürütülmesi hakkında bilgilendirici mesajlar alma.  
  
- **Hata ayıklama** -geliştirme aşamasındaki bir uygulamada programlama hatalarını izleme ve düzeltme. Daha fazla bilgi için bkz. [hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
- **Performans sayaçları** -uygulamanızın performansını izlemenize imkan tanıyan bileşenler. Daha fazla bilgi için bkz. [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
- **Olay günlükleri** -uygulamanızın yürütülmesinde önemli olayları almanızı ve izlemenizi sağlayan bileşenler. Daha fazla bilgi için, <xref:System.Diagnostics.EventLog> sınıfına bakın.  
  
 Kodunuzda stratejik konumlara izleme deyimleri yerleştirerek uygulamanızı denetlemek, dağıtılmış uygulamalar için özellikle yararlıdır. Trace deyimlerini kullanarak, bir uygulamayı yalnızca bir şeyler yanlış olduğunda ve ayrıca uygulamanın ne kadar iyi çalıştığını izlemek için değil, yalnızca bilgileri görüntülemek için Not alabilirsiniz.  
  
 Sınıfı <xref:System.Diagnostics.TraceSource> , Gelişmiş izleme özellikleri sağlar ve eski <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıflarının statik yöntemlerinin yerine kullanılabilir. <xref:System.Diagnostics.Trace> Tanıdık ve <xref:System.Diagnostics.TraceSource.TraceEvent%2A> <xref:System.Diagnostics.TraceSource.TraceData%2A>sınıflar yaygın olarak kullanılır, ancak sınıfıvegibiyeniizlemekomutlarıiçinönerilir.<xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Debug>  
  
 Ve sınıfları aynıdır, ancak <xref:System.Diagnostics.Trace> sınıfın yordamları ve işlevleri varsayılan olarak yayın yapılarına derlenir, ancak <xref:System.Diagnostics.Debug> sınıfının bu özellikleri değildir. <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace>  
  
 <xref:System.Diagnostics.Trace> Ve<xref:System.Diagnostics.Debug> sınıfları, geliştirme sırasında veya dağıtımdan sonra uygulama performansını izleme ve İnceleme araçlarını sağlar. Örneğin, dağıtılmış bir uygulamadaki belirli eylem <xref:System.Diagnostics.Trace> türlerini (örneğin, yeni veritabanı bağlantıları oluşturma) ve bu nedenle uygulamanın verimliliğini izlemek için sınıfını kullanabilirsiniz.  
  
## <a name="code-tracing-and-debugging"></a>Kod Izleme ve hata ayıklama  
 Geliştirme sırasında, Visual Studio tümleşik geliştirme ortamının (IDE) <xref:System.Diagnostics.Debug> çıkış penceresinde iletileri göstermek için sınıfının çıkış yöntemlerini kullanabilirsiniz. Örneğin:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Bu örneklerin her birinde "Merhaba Dünya!" görüntülenir hata ayıklayıcıda uygulama çalıştırıldığında çıkış penceresinde.  
  
 Bu, uygulamalarınızda hata ayıklamanızı ve test ortamınızdaki davranışlarını temel alarak performanslarını iyileştirmenizi sağlar. Tüm hata ayıklama çıkışını almak için, <xref:System.Diagnostics.Debug> koşullu özniteliği açık olan hata ayıklama derinizdeki uygulamanızda hata ayıklaması yapabilirsiniz. Uygulamanız yayın için hazırsanız, <xref:System.Diagnostics.Debug> koşullu özniteliği açmadan yayın yapınızı derleyebilirsiniz, böylece derleyicinin son yürütülebilir dosyasına hata ayıklama kodunuzu içermemesi gerekir. Daha fazla bilgi için [nasıl yapılır: Trace ve Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)ile koşullu olarak derleyin. Uygulamanıza yönelik farklı derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme ve](/visualstudio/ide/compiling-and-building-in-visual-studio)derleme.  
  
 Kod yürütmeyi, <xref:System.Diagnostics.Trace> sınıfının yöntemlerini kullanarak yüklü bir uygulamada da izleyebilirsiniz. Kodunuzda [Izleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md) yerleştirerek, izlemenin yapılıp yapılmayacağını ve ne kadar geniş olduğunu kontrol edebilirsiniz. Bu, uygulamanızın durumunu bir üretim ortamında izlemenize olanak sağlar. Bu, özellikle birden çok bilgisayarda çalışan birden çok bileşen kullanan bir iş uygulamasında önemlidir. Yapılandırma dosyası aracılığıyla dağıtımdan sonra anahtarların nasıl kullanıldığını kontrol edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)oluşturun, başlatın ve yapılandırın.  
  
 İzlemeyi kullanmayı düşündüğünüz bir uygulama geliştirirken, genellikle uygulama koduna hem izleme hem de hata ayıklama iletileri dahil edersiniz. Uygulamayı dağıtmaya hazırsanız, **hata ayıklama** koşullu özniteliğini açmadan yayın yapınızı derleyebilirsiniz. Ancak, derleyicinin yürütülebilir dosya içinde izleme kodunuzu içermesi için **Trace** Conditional özniteliğini açabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Trace ve Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)ile koşullu olarak derleyin.  
  
### <a name="phases-of-code-tracing"></a>Kod Izlemenin aşamaları  
 Kod izlemenin üç aşaması vardır:  
  
1. **Araç** — uygulamanıza izleme kodu eklersiniz.  
  
2. **İzleme** — izleme kodu bilgileri belirtilen hedefe yazar.  
  
3. **Analiz** — uygulamadaki sorunları belirlemek ve anlamak için izleme bilgilerini değerlendirmenizi sağlar.  
  
 Geliştirme sırasında, tüm hata ayıklama ve izleme çıkış yöntemleri, varsayılan olarak Visual Studio 'daki çıkış penceresine bilgi yazar. Dağıtılan bir uygulamada, Yöntemler izleme bilgilerini belirttiğiniz hedeflere yazar. İzleme veya hata ayıklama için çıkış hedefi belirtme hakkında daha fazla bilgi için bkz. [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Aşağıda, dağıtılmış uygulamalardaki olası sorunları çözümlemek ve düzeltmek için genellikle izlemenin kullanımı ile ilgili başlıca adımların genel bir görünümü verilmiştir. Bu adımların nasıl gerçekleştirileceği hakkında daha fazla bilgi için ilgili bağlantıya bakın.  
  
##### <a name="to-use-tracing-in-an-application"></a>Bir uygulamada izlemeyi kullanmak için  
  
1. Uygulamayı dağıttıktan sonra yerinde hangi izleme çıktısını almak istediğinizi göz önünde bulundurun.  
  
2. Anahtar kümesi oluşturun. Daha fazla bilgi için [nasıl yapılır: Izleme anahtarlarını](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)yapılandırın.  
  
3. Uygulama koduna Trace deyimlerini ekleyin.  
  
4. İzleme çıktısının görünmesini istediğiniz yeri belirleme ve uygun dinleyicileri ekleme. Daha fazla bilgi için bkz. [Izleme dinleyicileri oluşturma ve başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5. Uygulamanızı ve içerdiği izleme kodunu test edin ve hatalarını ayıklayın.  
  
6. Aşağıdaki yordamlardan birini kullanarak uygulamayı yürütülebilir kodda derleyin:  
  
    - **Yapı** menüsünü, **Çözüm Gezgini** **Özellik sayfaları** iletişim kutusunun **hata ayıklama** sayfasıyla birlikte kullanın. Visual Studio 'da derlerken bunu kullanın.  
  
         \- veya -  
  
    - Derleme komut satırı yöntemi için **Trace** ve **Debug** derleyici yönergelerini kullanın. Daha fazla bilgi için bkz. [izleme ve hata ayıklama Ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Komut satırından derlerken bunu kullanın.  
  
7. Çalışma zamanı sırasında bir sorun oluşursa, uygun izleme anahtarını açın. Daha fazla bilgi için bkz. [Izleme anahtarlarını yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     İzleme kodu, izleme iletilerini belirli bir hedefe Yazar; Örneğin, bir ekran, metin dosyası veya olay günlüğü. **Trace. Listeners** koleksiyonuna eklediğiniz dinleyicinin türü hedefi belirler.  
  
8. Uygulamadaki sorunu tanımlamak ve anlamak için izleme iletilerini çözümleyin.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>İzleme araçları ve dağıtılmış uygulamalar  
 Dağıtılmış bir uygulama oluşturduğunuzda, uygulamayı kullanılacağı şekilde test etmek zor olabilir. Birkaç geliştirme ekibinin, tüm olası işletim sistemleri veya Web tarayıcıları kombinasyonlarını (tüm yerelleştirilmiş dil seçenekleri dahil) veya aynı anda uygulamaya erişecek yüksek sayıda kullanıcının benzetimini yapma özelliği vardır. Bu koşullarda, dağıtılmış bir uygulamanın yüksek hacime, farklı kurulumlardan ve benzersiz Son Kullanıcı davranışlarına nasıl yanıt vereceğini test edemez. Ayrıca, dağıtılmış bir uygulamanın pek çok bölümünün, doğrudan etkileşime girebilmeniz veya bu parçaların etkinliklerini görüntülemek için Kullanıcı arabirimi yoktur.  
  
 Bununla birlikte, Dağıtılmış uygulamaların sistem yöneticilerine ilgili belirli olayları, özellikle de yanlış gitmeleri, uygulamayı işaretleyerek (yani, izleme deyimlerini kodunuzda stratejik konumlar. Daha sonra çalışma zamanında beklenmeyen bir şey oluşursa (örneğin, aşırı yavaş yanıt süresi), olası nedeni belirleyebilirsiniz.  
  
 Trace deyimleriyle, özgün kaynak kodu İnceleme, bunu değiştirme, yeniden derleme ve hata ayıklama ortamında çalışma zamanı hatasını üretmeye çalışırken zor görevi önleyebilirsiniz. Bir uygulamayı yalnızca hataları görüntülemek için değil, aynı zamanda performansı izlemek için de değiştirebileceğinizi unutmayın.  
  
## <a name="strategic-placement-of-trace-statements"></a>Trace deyimlerinin stratejik yerleşimi  
 Çalışma zamanında kullanım için izleme deyimlerinizi yerleştirirken özel dikkatli olmanız gerekir. Büyük olasılıkla tüm izleme senaryolarının yeterince kapsanmasını sağlamak için, dağıtılan bir uygulamada hangi izleme bilgilerinin gerekli olduğunu göz önünde bulundurmanız gerekir. Ancak izlemeyi kullanan uygulamalar yaygın farklılık gösterdiğinden, izlemenin stratejik yerleşimi için genel bir yönerge yoktur. Trace deyimlerini yerleştirme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Uygulama koduna](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)Trace deyimlerini ekleyin.  
  
## <a name="output-from-tracing"></a>Izlemenin çıktısı  
 İzleme çıktısı, *dinleyiciler*adlı nesneler tarafından toplanır. Dinleyici, izleme çıkışını alan ve bunu çıkış cihazına (genellikle bir pencere, günlük veya metin dosyası) yazan bir nesnedir. Bir izleme dinleyicisi oluşturulduğunda, genellikle <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> koleksiyona eklenir ve dinleyicinin tüm izleme çıkışını almasına izin verir.  
  
 İzleme bilgileri her zaman en azından varsayılan <xref:System.Diagnostics.Trace> çıktı hedefine <xref:System.Diagnostics.DefaultTraceListener>yazılır. Herhangi bir nedenden dolayı <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyona başka bir dinleyici eklemeden sildiyseniz, hiçbir izleme iletisi almazsınız. Daha fazla bilgi için bkz. [Trace dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 İzleme bilgilerini <xref:System.Diagnostics.Debug> yazan altı <xref:System.Diagnostics.Trace> üye ve yöntem aşağıdaki tabloda listelenmiştir.  
  
|Yöntem|Çıkış|  
|------------|------------|  
|**Vermediğini**|Belirtilen metin; ya da hiçbiri belirtilmemişse, çağrı yığını. Çıkış yalnızca, onay deyimindeki bir bağımsız değişken olarak belirtilen koşul **false**olduğunda yazılır .|  
|**Neden**|Belirtilen metin; ya da hiçbiri belirtilmemişse, çağrı yığını.|  
|**Yazarken**|Belirtilen metin.|  
|**WriteIf**|Belirtilen metin, **WriteIf** ifadesinde bağımsız değişken olarak belirtilen koşul karşılandığında.|  
|**WriteLine**|Belirtilen metin ve bir satır başı.|  
|**WriteLineIf**|Belirtilen metin ve bir satır başı, **WriteLineIf** ifadesinde bağımsız değişken olarak belirtilen koşul karşılandığında.|  
  
 <xref:System.Diagnostics.Trace.Listeners%2A> Koleksiyondaki tüm dinleyiciler yukarıdaki tabloda açıklanan iletileri alır, ancak alınan eylemler iletiyi hangi tür dinleyiciye aldığına bağlı olarak farklılık gösterebilir. Örneğin <xref:System.Diagnostics.DefaultTraceListener> , bir **başarısızlık** veya başarısız <xref:System.Diagnostics.TextWriterTraceListener> **onaylama** bildirimi aldığında bir onaylama iletişim kutusu görüntüler, ancak yalnızca çıktıyı akışa yazar.  
  
 Kendi dinleyicinizi uygulayarak özel sonuçlar elde edebilirsiniz. Özel bir izleme dinleyicisi Örneğin, iletileri bir ileti kutusuna görüntüleyebilir veya bir tabloya ileti eklemek için bir veritabanına bağlanabilir. Tüm özel dinleyiciler yukarıda bahsedilen altı yöntemi desteklemelidir. Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için .NET Framework başvuru <xref:System.Diagnostics.TraceListener> içindeki bölümüne bakın.  
  
 **Write** ve **WriteLine** yöntemleri her zaman belirttiğiniz metni yazar. **Onaylama**, **Writeif**ve **WriteLineIf** , belirtilen metni yazıp yazmadığını denetleyen bir Boole bağımsız değişkeni gerektirir; yalnızca ifade **true** Ise ( **WriteIf** ve **WriteLineIf**için) veya **false** (onay için) ise, belirtilen metni yazar. **Fail** yöntemi her zaman belirtilen metni yazar. Daha fazla bilgi için [nasıl yapılır: Uygulama koduna](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) ve .NET Framework başvuruya Trace deyimleri ekleyin.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
 Bir ASP.NET uygulamasını dağıtımdan önce izlemeyi ve hata ayıklamayı devre dışı bırakmayın, uygulamanız kötü amaçlı bir program tarafından yararlanılabilen hakkında bilgi açığa çıkabilir. Daha fazla bilgi için [nasıl yapılır: İzleme ve hata ayıklama](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [derleme ve derleme](/visualstudio/ide/compiling-and-building-in-visual-studio)ile koşullu olarak derleyin [ve şunları yapın: Izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)oluşturun, başlatın ve yapılandırın. Hata ayıklama Ayrıca Internet Information Services (IIS) aracılığıyla yapılandırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kod Anlaşmaları](../../../docs/framework/debug-trace-profile/code-contracts.md)
- [C#, F# ve Visual Basic Proje Türleri](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Nasıl yapılır: Uygulama koduna Izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [Nasıl yapılır: Izleme anahtarları oluşturma, başlatma ve yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Nasıl yapılır: Izleme kaynakları oluşturma ve başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Nasıl yapılır: Izleme dinleyicileri ile TraceSource ve filtreler kullanma](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
