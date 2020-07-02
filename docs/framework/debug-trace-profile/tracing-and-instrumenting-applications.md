---
title: İzleme Uygulamaları
description: .NET ' te uygulamaları izleyin ve işaretleyin. İzleme, çalışırken uygulama yürütmeyi izlemenizi sağlar. İşaretleme, performans düzeyini ölçmenize olanak tanır.
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
ms.openlocfilehash: d5484129ac17ee20aafe305bea5599f85903dfa2
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803553"
---
# <a name="tracing-and-instrumenting-applications"></a>İzleme Uygulamaları
İzleme, çalışırken uygulamanızın yürütülmesini izlemenize yönelik bir yoldur. Geliştirme sırasında .NET Framework uygulamanıza izleme ve hata ayıklama araçları ekleyebilirsiniz ve bu araçları, uygulamayı geliştirirken ve dağıttıktan sonra kullanabilirsiniz. <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> Ve <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> sınıflarını, daha sonra analiz edilmek üzere günlüklerde, metin dosyalarında veya diğer cihazlarda hatalar ve uygulama yürütme bilgilerini kaydetmek için kullanabilirsiniz.  
  
 Dönem *araçları* , bir ürünün performansının düzeyini izleyip ölçmenize ve hataları tanılamaya yönelik bir özellik anlamına gelir. Programlamada, bu, bir uygulamanın bu şekilde dahil olduğu anlamına gelir:  
  
- **Kod izleme** -bir uygulamanın çalışma zamanında yürütülmesi hakkında bilgilendirici mesajlar alma.  
  
- **Hata ayıklama** -geliştirme aşamasındaki bir uygulamada programlama hatalarını izleme ve düzeltme. Daha fazla bilgi için bkz. [hata ayıklama](/visualstudio/debugger/debugger-feature-tour).  
  
- **Performans sayaçları** -uygulamanızın performansını izlemenize imkan tanıyan bileşenler. Daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).  
  
- **Olay günlükleri** -uygulamanızın yürütülmesinde önemli olayları almanızı ve izlemenizi sağlayan bileşenler. Daha fazla bilgi için, <xref:System.Diagnostics.EventLog> sınıfına bakın.  
  
 Kodunuzda stratejik konumlara izleme deyimleri yerleştirerek uygulamanızı denetlemek, dağıtılmış uygulamalar için özellikle yararlıdır. Trace deyimlerini kullanarak, bir uygulamayı yalnızca bir şeyler yanlış olduğunda ve ayrıca uygulamanın ne kadar iyi çalıştığını izlemek için değil, yalnızca bilgileri görüntülemek için Not alabilirsiniz.  
  
 <xref:System.Diagnostics.TraceSource>Sınıfı, Gelişmiş izleme özellikleri sağlar ve eski <xref:System.Diagnostics.Trace> ve izleme sınıflarının statik yöntemlerinin yerine kullanılabilir <xref:System.Diagnostics.Debug> . Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıflar yaygın olarak kullanılır, ancak <xref:System.Diagnostics.TraceSource> sınıfı ve gibi yeni izleme komutları için önerilir <xref:System.Diagnostics.TraceSource.TraceEvent%2A> <xref:System.Diagnostics.TraceSource.TraceData%2A> .  
  
 <xref:System.Diagnostics.Trace>Ve <xref:System.Diagnostics.Debug> sınıfları aynıdır, ancak sınıfın yordamları ve işlevleri <xref:System.Diagnostics.Trace> Varsayılan olarak yayın yapılarına derlenir, ancak sınıfının bu özellikleri <xref:System.Diagnostics.Debug> değildir.  
  
 <xref:System.Diagnostics.Trace>Ve <xref:System.Diagnostics.Debug> sınıfları, geliştirme sırasında veya dağıtımdan sonra uygulama performansını izleme ve İnceleme araçlarını sağlar. Örneğin, <xref:System.Diagnostics.Trace> Dağıtılmış bir uygulamadaki belirli eylem türlerini (örneğin, yeni veritabanı bağlantıları oluşturma) ve bu nedenle uygulamanın verimliliğini izlemek için sınıfını kullanabilirsiniz.  
  
## <a name="code-tracing-and-debugging"></a>Kod Izleme ve hata ayıklama  
 Geliştirme sırasında, <xref:System.Diagnostics.Debug> Visual Studio tümleşik geliştirme ortamının (IDE) çıkış penceresinde iletileri göstermek için sınıfının çıkış yöntemlerini kullanabilirsiniz. Örneğin:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Bu örneklerin her birinde "Merhaba Dünya!" görüntülenir hata ayıklayıcıda uygulama çalıştırıldığında çıkış penceresinde.  
  
 Bu, uygulamalarınızda hata ayıklamanızı ve test ortamınızdaki davranışlarını temel alarak performanslarını iyileştirmenizi sağlar. <xref:System.Diagnostics.Debug>Tüm hata ayıklama çıkışını almak için, koşullu özniteliği açık olan hata ayıklama derinizdeki uygulamanızda hata ayıklaması yapabilirsiniz. Uygulamanız yayın için hazırsanız, koşullu özniteliği açmadan yayın yapınızı derleyebilirsiniz <xref:System.Diagnostics.Debug> , böylece derleyicinin son yürütülebilir dosyasına hata ayıklama kodunuzu içermemesi gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: izleme ve hata ayıklama Ile koşullu derleme](how-to-compile-conditionally-with-trace-and-debug.md). Uygulamanıza yönelik farklı derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme ve](/visualstudio/ide/compiling-and-building-in-visual-studio)derleme.  
  
 Kod yürütmeyi, sınıfının yöntemlerini kullanarak yüklü bir uygulamada da izleyebilirsiniz <xref:System.Diagnostics.Trace> . Kodunuzda [Izleme anahtarları](trace-switches.md) yerleştirerek, izlemenin yapılıp yapılmayacağını ve ne kadar geniş olduğunu kontrol edebilirsiniz. Bu, uygulamanızın durumunu bir üretim ortamında izlemenize olanak sağlar. Bu, özellikle birden çok bilgisayarda çalışan birden çok bileşen kullanan bir iş uygulamasında önemlidir. Yapılandırma dosyası aracılığıyla dağıtımdan sonra anahtarların nasıl kullanıldığını kontrol edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: oluşturma, başlatma ve yapılandırma Izleme anahtarları](how-to-create-initialize-and-configure-trace-switches.md).  
  
 İzlemeyi kullanmayı düşündüğünüz bir uygulama geliştirirken, genellikle uygulama koduna hem izleme hem de hata ayıklama iletileri dahil edersiniz. Uygulamayı dağıtmaya hazırsanız, **hata ayıklama** koşullu özniteliğini açmadan yayın yapınızı derleyebilirsiniz. Ancak, derleyicinin yürütülebilir dosya içinde izleme kodunuzu içermesi için **Trace** Conditional özniteliğini açabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: izleme ve hata ayıklama Ile koşullu derleme](how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Kod Izlemenin aşamaları  
 Kod izlemenin üç aşaması vardır:  
  
1. **Araç** — uygulamanıza izleme kodu eklersiniz.  
  
2. **İzleme** — izleme kodu bilgileri belirtilen hedefe yazar.  
  
3. **Analiz** — uygulamadaki sorunları belirlemek ve anlamak için izleme bilgilerini değerlendirmenizi sağlar.  
  
 Geliştirme sırasında, tüm hata ayıklama ve izleme çıkış yöntemleri, varsayılan olarak Visual Studio 'daki çıkış penceresine bilgi yazar. Dağıtılan bir uygulamada, Yöntemler izleme bilgilerini belirttiğiniz hedeflere yazar. İzleme veya hata ayıklama için çıkış hedefi belirtme hakkında daha fazla bilgi için bkz. [Trace Listeners](trace-listeners.md).  
  
 Aşağıda, dağıtılmış uygulamalardaki olası sorunları çözümlemek ve düzeltmek için genellikle izlemenin kullanımı ile ilgili başlıca adımların genel bir görünümü verilmiştir. Bu adımların nasıl gerçekleştirileceği hakkında daha fazla bilgi için ilgili bağlantıya bakın.  
  
##### <a name="to-use-tracing-in-an-application"></a>Bir uygulamada izlemeyi kullanmak için  
  
1. Uygulamayı dağıttıktan sonra yerinde hangi izleme çıktısını almak istediğinizi göz önünde bulundurun.  
  
2. Anahtar kümesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Izleme anahtarlarını yapılandırma](how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Uygulama koduna Trace deyimlerini ekleyin.  
  
4. İzleme çıktısının görünmesini istediğiniz yeri belirleme ve uygun dinleyicileri ekleme. Daha fazla bilgi için bkz. [Izleme dinleyicileri oluşturma ve başlatma](how-to-create-and-initialize-trace-listeners.md).  
  
5. Uygulamanızı ve içerdiği izleme kodunu test edin ve hatalarını ayıklayın.  
  
6. Aşağıdaki yordamlardan birini kullanarak uygulamayı yürütülebilir kodda derleyin:  
  
    - **Yapı** menüsünü, **Çözüm Gezgini** **Özellik sayfaları** iletişim kutusunun **hata ayıklama** sayfasıyla birlikte kullanın. Visual Studio 'da derlerken bunu kullanın.  
  
         \-veya  
  
    - Derleme komut satırı yöntemi için **Trace** ve **Debug** derleyici yönergelerini kullanın. Daha fazla bilgi için bkz. [izleme ve hata ayıklama Ile koşullu derleme](how-to-compile-conditionally-with-trace-and-debug.md). Komut satırından derlerken bunu kullanın.  
  
7. Çalışma zamanı sırasında bir sorun oluşursa, uygun izleme anahtarını açın. Daha fazla bilgi için bkz. [Izleme anahtarlarını yapılandırma](how-to-create-initialize-and-configure-trace-switches.md).  
  
     İzleme kodu, izleme iletilerini belirli bir hedefe Yazar; Örneğin, bir ekran, metin dosyası veya olay günlüğü. Koleksiyona eklediğiniz dinleyicinin türü <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> hedefi belirler.  
  
8. Uygulamadaki sorunu tanımlamak ve anlamak için izleme iletilerini çözümleyin.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>İzleme araçları ve dağıtılmış uygulamalar  
 Dağıtılmış bir uygulama oluşturduğunuzda, uygulamayı kullanılacağı şekilde test etmek zor olabilir. Birkaç geliştirme ekibinin, tüm olası işletim sistemleri veya Web tarayıcıları kombinasyonlarını (tüm yerelleştirilmiş dil seçenekleri dahil) veya aynı anda uygulamaya erişecek yüksek sayıda kullanıcının benzetimini yapma özelliği vardır. Bu koşullarda, dağıtılmış bir uygulamanın yüksek hacime, farklı kurulumlardan ve benzersiz Son Kullanıcı davranışlarına nasıl yanıt vereceğini test edemez. Ayrıca, dağıtılmış bir uygulamanın pek çok bölümünün, doğrudan etkileşime girebilmeniz veya bu parçaların etkinliklerini görüntülemek için Kullanıcı arabirimi yoktur.  
  
 Bununla birlikte, Dağıtılmış uygulamaların sistem yöneticilerine ilgili belirli olayları, özellikle de yanlış gitmeyen şeyleri ( *Örneğin, kodunuzun* stratejik konumlarında izleme bildirimleri yerleştirerek), bu işlemi telafi edebilirsiniz. Daha sonra çalışma zamanında beklenmeyen bir şey oluşursa (örneğin, aşırı yavaş yanıt süresi), olası nedeni belirleyebilirsiniz.  
  
 Trace deyimleriyle, özgün kaynak kodu İnceleme, bunu değiştirme, yeniden derleme ve hata ayıklama ortamında çalışma zamanı hatasını üretmeye çalışırken zor görevi önleyebilirsiniz. Bir uygulamayı yalnızca hataları görüntülemek için değil, aynı zamanda performansı izlemek için de değiştirebileceğinizi unutmayın.  
  
## <a name="strategic-placement-of-trace-statements"></a>Trace deyimlerinin stratejik yerleşimi  
 Çalışma zamanında kullanım için izleme deyimlerinizi yerleştirirken özel dikkatli olmanız gerekir. Büyük olasılıkla tüm izleme senaryolarının yeterince kapsanmasını sağlamak için, dağıtılan bir uygulamada hangi izleme bilgilerinin gerekli olduğunu göz önünde bulundurmanız gerekir. Ancak izlemeyi kullanan uygulamalar yaygın farklılık gösterdiğinden, izlemenin stratejik yerleşimi için genel bir yönerge yoktur. Trace deyimlerini yerleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Trace deyimlerini uygulama koduna ekleme](how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Izlemenin çıktısı  
 İzleme çıktısı, *dinleyiciler*adlı nesneler tarafından toplanır. Dinleyici, izleme çıkışını alan ve bunu çıkış cihazına (genellikle bir pencere, günlük veya metin dosyası) yazan bir nesnedir. Bir izleme dinleyicisi oluşturulduğunda, genellikle <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> koleksiyona eklenir ve dinleyicinin tüm izleme çıkışını almasına izin verir.  
  
 İzleme bilgileri her zaman en azından varsayılan <xref:System.Diagnostics.Trace> çıktı hedefine yazılır <xref:System.Diagnostics.DefaultTraceListener> . Herhangi bir nedenden dolayı <xref:System.Diagnostics.DefaultTraceListener> koleksiyona başka bir dinleyici eklemeden sildiyseniz <xref:System.Diagnostics.Trace.Listeners%2A> , hiçbir izleme iletisi almazsınız. Daha fazla bilgi için bkz. [Trace dinleyicileri](trace-listeners.md).  
  
 <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> İzleme bilgilerini yazan altı üye ve yöntem aşağıdaki tabloda listelenmiştir.  
  
|Yöntem|Çıktı|  
|------------|------------|  
|`Assert`|Belirtilen metin; ya da hiçbiri belirtilmemişse, çağrı yığını. Çıktı yalnızca, deyimde bir bağımsız değişken olarak belirtilen koşul `Assert` **false**olduğunda yazılır.|  
|`Fail`|Belirtilen metin; ya da hiçbiri belirtilmemişse, çağrı yığını.|  
|`Write`|Belirtilen metin.|  
|`WriteIf`|Deyimdeki bir bağımsız değişken olarak belirtilen koşul karşılandığında, belirtilen metin `WriteIf` .|  
|`WriteLine`|Belirtilen metin ve bir satır başı.|  
|`WriteLineIf`|Deyimdeki bir bağımsız değişken olarak belirtilen koşul karşılandığında, belirtilen metin ve bir satır başı `WriteLineIf` .|  
  
 Koleksiyondaki tüm dinleyiciler <xref:System.Diagnostics.Trace.Listeners%2A> Yukarıdaki tabloda açıklanan iletileri alır, ancak alınan eylemler iletiyi hangi tür dinleyiciye aldığına bağlı olarak farklılık gösterebilir. Örneğin, ya da <xref:System.Diagnostics.DefaultTraceListener> başarısız bildirimi aldığında bir onaylama iletişim kutusu görüntüler `Fail` `Assert` , ancak <xref:System.Diagnostics.TextWriterTraceListener> yalnızca çıktıyı akışa yazar.  
  
 Kendi dinleyicinizi uygulayarak özel sonuçlar elde edebilirsiniz. Özel bir izleme dinleyicisi Örneğin, iletileri bir ileti kutusuna görüntüleyebilir veya bir tabloya ileti eklemek için bir veritabanına bağlanabilir. Tüm özel dinleyiciler yukarıda bahsedilen altı yöntemi desteklemelidir. Geliştirici tanımlı dinleyiciler oluşturma hakkında daha fazla bilgi için <xref:System.Diagnostics.TraceListener> .NET Framework başvuru içindeki bölümüne bakın.  
  
 `Write`Ve `WriteLine` yöntemleri her zaman belirttiğiniz metni yazar. `Assert`, `WriteIf` ve, `WriteLineIf` belirtilen metni yazıp yazmadığını denetleyen bir Boole bağımsız değişkeni gerektirir; yalnızca ifade **true** ( `WriteIf` ve için `WriteLineIf` ) veya **false** (için) ise, belirtilen metni yazar `Assert` . `Fail`Yöntemi her zaman belirtilen metni yazar. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama koduna Izleme deyimleri ekleme](how-to-add-trace-statements-to-application-code.md) ve .NET Framework başvurusu.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
 Bir ASP.NET uygulamasını dağıtımdan önce izlemeyi ve hata ayıklamayı devre dışı bırakmayın, uygulamanız kötü amaçlı bir program tarafından yararlanılabilen hakkında bilgi açığa çıkabilir. Daha fazla bilgi için bkz. [nasıl yapılır: izleme ve hata ayıklama Ile koşullu derleme](how-to-compile-conditionally-with-trace-and-debug.md), [derleme ve derleme](/visualstudio/ide/compiling-and-building-in-visual-studio)ve [nasıl yapılır: izleme anahtarları oluşturma, başlatma ve yapılandırma](how-to-create-initialize-and-configure-trace-switches.md). Hata ayıklama Ayrıca Internet Information Services (IIS) aracılığıyla yapılandırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kod Anlaşmaları](code-contracts.md)
- [C#, F# ve Visual Basic Proje Türleri](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](how-to-compile-conditionally-with-trace-and-debug.md)
- [Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma](how-to-create-initialize-and-configure-trace-switches.md)
- [Nasıl yapılır: İzleme Kaynakları Oluşturma ve Başlatma](how-to-create-and-initialize-trace-sources.md)
- [Nasıl yapılır: İzleme Dinleyicileri ile TraceSource ve Filtreler Kullanma](how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [İz Dinleyicileri](trace-listeners.md)
- [İzleme Anahtarları](trace-switches.md)
