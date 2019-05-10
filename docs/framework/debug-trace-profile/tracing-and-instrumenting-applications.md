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
ms.openlocfilehash: ad2c41cc99422217b9f85acbd32f91ac78a9a7c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614235"
---
# <a name="tracing-and-instrumenting-applications"></a>İzleme Uygulamaları
İzleme, çalışırken uygulamanızın yürütmesini izlemek bir yoldur. .NET Framework uygulamanızı izleme ve hata ayıklama araçları, geliştirme ve uygulama geliştirirken hem dağıttıktan sonra bu araçları kullanabilirsiniz ekleyebilirsiniz. Kullanabileceğiniz <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, ve <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> hataları ve uygulama yürütme günlükleri, metin dosyaları veya diğer cihazlar daha sonra çözümlemek için ilgili bilgileri kaydetmek için sınıflar.  
  
 Terim *izleme* izlemek veya bir ürünün performans düzeyini ölçün ve hataları tanılamak için bir yeteneği anlamına gelir. Programlamada, bu özelliği eklemek için bir uygulamanın anlamına gelir:  
  
- **Kod izleme** -çalışma zamanında bir uygulamanın yürütülmesini hakkında bilgi iletileri alma.  
  
- **Hata ayıklama** - izleme ve geliştirme aşamasındaki bir uygulamada programlama hatalarını düzeltiyor. Daha fazla bilgi için [hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
- **Performans sayaçları** -uygulamanızın performansını izlemek bileşenleri. Daha fazla bilgi için [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
- **Olay günlükleri** -bileşenleri almak ve uygulamanızın yürütmesini önemli olayları izleyin. Daha fazla bilgi için <xref:System.Diagnostics.EventLog> sınıfı.  
  
 İzleme deyimleri kodunuzda stratejik konumlara yerleştirerek, uygulamada ölçümlü izleme yapma, dağıtılmış uygulamalar için özellikle yararlıdır. İzleme deyimleri kullanarak bir uygulama yalnızca işler kötüye gittiğinde bilgileri görüntülemek için aynı zamanda uygulamanın ne kadar iyi gerçekleştiriyor izlemek için izleyebilirsiniz.  
  
 <xref:System.Diagnostics.TraceSource> SAX Gelişmiş izleme ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları. Tanıdık <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları hala yaygın olarak kullanılan, ancak <xref:System.Diagnostics.TraceSource> sınıfı önerilir yeni izleme komutları gibi <xref:System.Diagnostics.TraceSource.TraceEvent%2A> ve <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> Ve <xref:System.Diagnostics.Debug> sınıflardır, yordamları ve işlevleri aynı <xref:System.Diagnostics.Trace> sınıfı, varsayılan olarak derlenir, sürüm derlemeleri ancak içeriğiyle <xref:System.Diagnostics.Debug> sınıf değildir.  
  
 <xref:System.Diagnostics.Trace> Ve <xref:System.Diagnostics.Debug> sınıfları izlemek ve uygulama performansını geliştirme sırasında veya dağıtımdan sonra incelemek için gereken araçları sağlar. Örneğin, kullanabileceğiniz <xref:System.Diagnostics.Trace> eylemleri dağıtılan bir uygulamada belirli türlerini (örneğin, yeni veritabanı bağlantıları oluşturulmasını) oluşur ve bu nedenle uygulamanın etkinliğini izleyebilirsiniz izlemek için sınıf.  
  
## <a name="code-tracing-and-debugging"></a>Kod izleme ve hata ayıklama  
 Geliştirme sırasında çıktı yöntemlerini kullanabilirsiniz <xref:System.Diagnostics.Debug> Visual Studio tümleşik geliştirme ortamı (IDE) çıktı penceresinde iletileri görüntülemek için sınıf. Örneğin:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Bu örneklerin her "Hello World!" görüntüler hata ayıklayıcıda uygulamayı çalıştırdığınızda çıktı penceresinde.  
  
 Bu, uygulamalarınızda hata ayıklamak ve test ortamınızdaki davranışlarını göre performanslarını iyileştirmenize olanak sağlar. Hata ayıklama derleme ile uygulamanızın hatalarını <xref:System.Diagnostics.Debug> tüm hata ayıklama çıkış alması için bunları açık olduğundan conditional özniteliği. Uygulamanız yayımlanmaya hazır olduğunda, açma olmadan yayın derleme derleyebilirsiniz <xref:System.Diagnostics.Debug> koşullu öznitelik, böylece derleyici son yürütülebilir dosya hata ayıklama, kod içermez. Daha fazla bilgi için [nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Uygulamanız için farklı bir derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [derleme ve oluşturma](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Yöntemlerini kullanarak yüklü bir uygulama, kod yürütme izleyebilirsiniz <xref:System.Diagnostics.Trace> sınıfı. Yerleştirerek [izleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md) kodunuzda olup izleme gerçekleşir ve ne kadar kapsamlı olduğunu denetleyebilirsiniz. Bu, bir üretim ortamında, uygulamanızın durumunu izlemenize olanak sağlar. Birden çok bilgisayar üzerinde çalışan birden çok bileşen kullanan bir iş uygulaması bu durum özellikle önemlidir. Anahtarlar dağıtım sonrası yapılandırma dosyası aracılığıyla nasıl kullanıldığını kontrol edebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 İzlemeyi kullanmak istediğiniz bir uygulama geliştirirken, genellikle hem izleme ve iletileri uygulama kodunda hata ayıklama içerir. Uygulamayı dağıtmak hazırsanız olmadan açma sürüm derleme derleyebilirsiniz **hata ayıklama** conditional özniteliği. Ancak, etkinleştirebilirsiniz **izleme** koşullu özniteliği derleyici izleme kodunuzu yürütülebilir dosya içerir. Daha fazla bilgi için [nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Kod izleme aşamaları  
 Kod izlemenin üç aşama vardır:  
  
1. **İzleme** — izleme kodu uygulamanıza ekleyin.  
  
2. **İzleme** — izleme kodu, belirtilen hedef bilgilerini yazar.  
  
3. **Analiz** — tanımlamak ve uygulamadaki sorunları anlamak için izleme bilgileri değerlendirin.  
  
 Geliştirme sırasında tüm hata ayıklama ve izleme yöntemleri varsayılan olarak Visual Studio çıkış penceresine yazmak çıktı. Dağıtılan bir uygulamada yöntemleri belirttiğiniz hedeflerini izleme bilgilerini yazın. İzleme veya hata ayıklama için bir çıkış hedefi belirtme hakkında daha fazla bilgi için bkz. [izleme dinleyicilerine](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Ana adımlar çözümlemek ve dağıtılan uygulamalarda olası sorunları düzeltmek için izleme kullanımında genellikle genel bir görünümünü aşağıdadır. Bu adımların nasıl gerçekleştirileceğini hakkında daha fazla bilgi için uygun bağlantıyı bakın.  
  
##### <a name="to-use-tracing-in-an-application"></a>Bir uygulamada izlemeyi kullanmak için  
  
1. Uygulamayı dağıttıktan sonra yerinde almak istediğiniz hangi izleme çıkış göz önünde bulundurun.  
  
2. Anahtarları kümesi oluşturun. Daha fazla bilgi için [nasıl yapılır: İzleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Uygulama koduna izleme deyimleri ekleyin.  
  
4. İzleme çıktısı görüntülenir ve uygun dinleyiciler eklemek için istediğiniz belirleyin. Daha fazla bilgi için [oluşturma ve izleme dinleyicilerini başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5. Test ve uygulamanız ve içerdiği izleme kodu hata ayıklama.  
  
6. Aşağıdaki yordamlardan birini kullanarak yürütülebilir kod uygulamasına derleyin:  
  
    - Kullanım **derleme** menüsü ile birlikte **hata ayıklama** sayfasının **özellik sayfaları** iletişim kutusunda **Çözüm Gezgini**. Bu, Visual Studio'da derleme sırasında kullanın.  
  
         \- veya -  
  
    - Kullanım **izleme** ve **hata ayıklama** derleme komut satırı yöntemi için derleyici yönergeleri. Daha fazla bilgi için [izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Bu komut satırından derleme yapılırken kullanın.  
  
7. Çalışma zamanı sırasında bir sorun meydana gelirse, uygun bir izleme anahtarı etkinleştirin. Daha fazla bilgi için [izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     İzleme kodu izleme iletileri belirtilen hedefe, örneğin, bir ekran, bir metin dosyası veya bir olay günlüğüne yazar. Dinleyici, dahil edilen türünü **Trace.Listeners** koleksiyon hedefini belirler.  
  
8. İzleme iletileri tanımlamak ve uygulama sorunu anlamak için analiz edin.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>İzleme Araçları ve dağıtılmış uygulamalar  
 Dağıtılmış bir uygulama oluşturduğunuzda, onu kullanılacak şekilde uygulama test etmek zor bulabilirsiniz. Birkaç geliştirme ekipleri, işletim sistemleri veya tarayıcılar (tüm yerelleştirilmiş dil seçenekleri dahil) tüm olası eşleştirme birleşimlerini test etmek için ya da çok sayıda uygulamanın aynı anda erişen kullanıcıların benzetimini yapmak için özelliğine sahip. Bu koşullar altında yüksek miktarlarda, farklı ayarlar ve benzersiz bir son kullanıcı davranışları için Dağıtılmış bir uygulamanın nasıl yanıt vereceğini test edilemez. Ayrıca, dağıtılmış bir uygulamanın birçok bölümü, kullanıcı arabirimi ile doğrudan etkileşim kurmak veya bu parçaların etkinliğini görüntüleyin vardır.  
  
 Ancak, bu sistem yöneticileri, özellikle tarafından yanlış şeyler için ilgilendiğiniz belirli olayları tanımlamak dağıtılmış uygulamalar etkinleştirerek dengeleyebilir *izleme* uygulama — diğer bir deyişle, göre yerleştirme izleme deyimleri kodunuzda stratejik konumlarda. Ardından, çalışma zamanında beklenmeyen bir sorun oluşması durumunda (örneğin, aşırı yavaş yanıt süresi), olası nedeni belirleyebilirsiniz.  
  
 İzleme deyimleri ile özgün kaynak kodunu inceleyerek, değiştirmeden, yeniden derlemeden ve hata ayıklama ortamında çalışma zamanı hatasına neden çalışılıyor zor bir görev önleyebilirsiniz. Uygulamanın yalnızca hataları görüntülemek için aynı zamanda performansını izlemek için izleme unutmayın.  
  
## <a name="strategic-placement-of-trace-statements"></a>İzleme deyimleri stratejik yerleşimi  
 Çalışma süresi boyunca kullanım izleme deyimlerinin yerleştirirken özel dikkatli olmanız gerekir. Böylece tüm olası izleme senaryoları yeterince kapsanan hangi izleme bilgilerini dağıtılan bir uygulamada gerekmesi dikkate almanız gerekir. İzleme uygulamalar kullanan farklı yaygın olarak, ancak vardır izleme stratejik yerleşimi için hiçbir genel yönergeleri. İzleme deyimleri yerleştirme daha fazla bilgi için bkz: [nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>İzleme çıktısı  
 İzleme çıktısına adlı nesneler tarafından toplanan *dinleyicileri*. Dinleyici izleme çıkışını alır ve çıktı cihazına (genellikle bir pencere, günlük veya metin dosyası) yazan bir nesnedir. İzleme dinleyicisi oluşturulduğunda, bu genellikle eklenir <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> koleksiyon, tüm izleme çıktısını almak dinleyici izin verme.  
  
 Bilgi izleme her zaman yazılmış en az varsayılan <xref:System.Diagnostics.Trace> Çıkış hedefini <xref:System.Diagnostics.DefaultTraceListener>. Herhangi bir nedenden dolayı sildiyseniz <xref:System.Diagnostics.DefaultTraceListener> diğer dinleyicilere eklemeden <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu, herhangi bir izleme iletisi almaz. Daha fazla bilgi için [izleme dinleyicilerine](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Altı <xref:System.Diagnostics.Debug> üyeleri ve <xref:System.Diagnostics.Trace> izleme bilgilerini yazma yöntemleri, aşağıdaki tabloda listelenmiştir.  
  
|Yöntem|Çıkış|  
|------------|------------|  
|**Assert**|Belirtilen metin; ya da hiçbiri belirtilmezse, çağrı yığını. Çıktı, yalnızca koşul bir bağımsız değişken olarak belirttiyseniz yazılır **Assert** deyimi **false**.|  
|**Başarısız**|Belirtilen metin; ya da hiçbiri belirtilmezse, çağrı yığını.|  
|**Yazma**|Belirtilen metin.|  
|**Writeıf**|Belirtilen metin bağımsız değişkeni olarak bir koşul belirtilmişse, **Writeıf** deyimi karşılandığında.|  
|**WriteLine**|Belirtilen metni ve bir satır başı.|  
|**Writelineıf**|Bir bağımsız değişken olarak bir koşul belirtilmişse belirtilen metin bir satır başı, dönüş ve **Writelineıf** deyimi karşılandığında.|  
  
 İçindeki tüm dinleyicileri <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu yukarıdaki tabloda açıklanan iletileri alırsınız, ancak gerçekleştirilen eylemler ne tür bir dinleyici iletiyi alır bağlı olarak değişebilir. Örneğin, <xref:System.Diagnostics.DefaultTraceListener> aldığında bir onaylama iletişim kutusu görüntüler bir **başarısız** veya başarısız **Assert** bildirim, ancak bir <xref:System.Diagnostics.TextWriterTraceListener> yalnızca çıktı, akışa yazar.  
  
 Kendi dinleyici uygulayarak özel sonuçlara neden olabilir. Özel İzleme dinleyicisi, örneğin, iletileri için bir ileti kutusu görüntülemek veya iletileri bir tabloya eklenecek bir veritabanına bağlanın. Tüm özel dinleyicileri yukarıda belirtilen altı yöntemleri desteklemelidir. Geliştirici tarafından tanımlanan dinleyicileri oluşturma ile ilgili daha fazla bilgi için bkz: <xref:System.Diagnostics.TraceListener> .NET Framework başvurusu.  
  
> [!NOTE]
>  İçinde [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], **Debug.Write**, **Debug.WriteIf**, **Debug.WriteLine**, ve **Debug.WriteLineIf** yöntemleri değiştirildi **Debug.Print** Visual Basic'in önceki sürümlerde kullanılabilir olan yöntem.  
  
 **Yazma** ve **WriteLine** yöntemleri her zaman sizin belirttiğiniz metni yazın. **Assert**, **Writeıf**, ve **Writelineıf** belirtilen metin yazmadan olup olmadığını denetleyen bir Boole bağımsız değişkeni gerektirir; ifadenin olmasıdurumunda,yalnızcabelirtilenmetinyazma**true** (için **Writeıf** ve **Writelineıf**), veya **false** (için **Assert**). **Başarısız** yöntemi, belirtilen metnin her zaman yazar. Daha fazla bilgi için [nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) ve .NET Framework başvurusu.  
  
## <a name="security-concerns"></a>Güvenlik konuları  
 Uygulamanız, izleme ve bir ASP.NET uygulamasını dağıtmadan önce hata ayıklama devre dışı bırakmayın, kötü amaçlı bir program tarafından yararlanılabilir kendisiyle ilgili bilgiler gösterilmesine neden olabilir. Daha fazla bilgi için [nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [derleme ve oluşturma](/visualstudio/ide/compiling-and-building-in-visual-studio), ve [nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md). Hata ayıklama aynı zamanda Internet Information Services (IIS) aracılığıyla yapılandırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Kod Anlaşmaları](../../../docs/framework/debug-trace-profile/code-contracts.md)
- [C#, F# ve Visual Basic Proje Türleri](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [Nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Nasıl yapılır: Oluşturma ve izleme kaynaklarını başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [Nasıl yapılır: İzleme dinleyicileri ile TraceSource ve filtreler kullanma](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
