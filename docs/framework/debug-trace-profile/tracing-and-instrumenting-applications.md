---
title: "İzleme Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 932fef22681aeb2a68d7852884127155757e4099
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tracing-and-instrumenting-applications"></a>İzleme Uygulamaları
İzleme, çalışırken, uygulamanızın yürütülmesini izlemek bir yoldur. Bunu geliştirmek ve uygulama geliştirirken hem dağıttıktan sonra bu araçları kullanabilirsiniz, .NET Framework uygulamasını izleme ve hata ayıklama araçları ekleyebilirsiniz. Kullanabileceğiniz <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType>, ve <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> hatalar ve uygulama yürütme günlükleri, metin dosyaları veya daha sonraki analizler için diğer aygıtlar hakkındaki bilgileri kaydetmek için sınıflar.  
  
 Terim *Araçları* bir yeteneği izlemek veya bir ürünün performans düzeyini ölçmek için ve hataları tanılamak için başvuruyor. Programlamada bu birleştirmek için bir uygulama yeteneği anlamına gelir:  
  
-   **Kod izleme** -uygulamanın çalışma zamanında yürütülmesi hakkında bilgilendirici iletileri alma.  
  
-   **Hata ayıklama** - izleme ve geliştirme altında bir uygulamada programlama hataları düzelttikten. Daha fazla bilgi için bkz: [hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
-   **Performans sayaçları** -bileşenleri, uygulamanızın performansını izlemenize olanak tanır. Daha fazla bilgi için bkz: [performans sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
-   **Olay günlükleri** -izin bileşenleri almak ve uygulamanızın yürütülmesini önde gelen olayları izlemek. Daha fazla bilgi için bkz: <xref:System.Diagnostics.EventLog> sınıfı.  
  
 Uygulamanızı stratejik konumlara kodunuzda izleme deyimleri koyarak düzenleme, dağıtılmış uygulamalar için özellikle yararlıdır. İzleme deyimleri kullanarak bir uygulama değil yalnızca şeyler ters gittiğinde bilgileri görüntülemek için aynı zamanda uygulama ne kadar iyi gerçekleştiriyor izlemek için işaretleyebilir.  
  
 <xref:System.Diagnostics.TraceSource> SAX Gelişmiş izleme ve eski yerine statik yöntemleri kullanılabilir <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> izleme sınıfları. Bilinen <xref:System.Diagnostics.Trace> ve <xref:System.Diagnostics.Debug> sınıfları hala yaygın olarak kullanılan, ancak <xref:System.Diagnostics.TraceSource> sınıfı önerilir yeni izleme komutları gibi <xref:System.Diagnostics.TraceSource.TraceEvent%2A> ve <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 <xref:System.Diagnostics.Trace> Ve <xref:System.Diagnostics.Debug> sınıflar bu yordamları ve işlevleri dışında aynı <xref:System.Diagnostics.Trace> sınıfı, varsayılan olarak derlenen, sürüm derlemeleri, ancak bu <xref:System.Diagnostics.Debug> sınıfı değildir.  
  
 <xref:System.Diagnostics.Trace> Ve <xref:System.Diagnostics.Debug> sınıfları izlemek ve uygulama performansı geliştirme sırasında veya dağıtımdan sonra incelemek için araçlar sağlar. Örneğin, kullanabileceğiniz <xref:System.Diagnostics.Trace> (örneğin, yeni veritabanı bağlantıları oluşturma) oluşur ve bu nedenle uygulamanın verimliliği izleyebilirsiniz olarak dağıtılan bir uygulama eylemleri belirli türlerini izlemek için sınıf.  
  
## <a name="code-tracing-and-debugging"></a>Kod izleme ve hata ayıklama  
 Geliştirme sırasında çıkış yöntemlerini kullanabilirsiniz <xref:System.Diagnostics.Debug> Visual Studio tümleşik geliştirme ortamı (IDE) çıktı penceresinde iletileri görüntülemek için sınıf. Örneğin:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Bu örneklerin herbiri "Hello World!" görüntülenir hata ayıklayıcıda uygulamayı çalıştırdığınızda çıktı penceresinde.  
  
 Uygulamalarınızda hata ayıklamak ve davranışlarını test ortamınızdaki göre kendi performansını iyileştirmek sağlar. Hata ayıklama yapı ile uygulamanızı ayıklayabilirsiniz <xref:System.Diagnostics.Debug> tüm hata ayıklama çıktı alması için bunları açık koşullu öznitelik. Uygulamanızı sürüm için hazır olduğunda, açma olmadan, yayın derlemesi derleyebilirsiniz <xref:System.Diagnostics.Debug> koşullu öznitelik, böylece derleyici hata ayıklama kodunuzu son yürütülebilir dosya dahil edilmez. Daha fazla bilgi için bkz: [nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Uygulamanız için farklı derleme yapılandırmaları hakkında daha fazla bilgi için bkz: [derlemek ve oluşturmak](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Yöntemlerini kullanarak yüklü bir uygulama kodu yürütme izleyebilirsiniz <xref:System.Diagnostics.Trace> sınıfı. Yerleştirerek [izleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md) kodunuzda izleme olup oluşur ve ne kadar kapsamlı olduğunu denetleyebilirsiniz. Uygulamanızı bir üretim ortamında durumunu izlemenize izin verir. Birden çok bilgisayar üzerinde çalışan birden çok bileşenleri kullanan bir iş uygulaması bu durum özellikle önemlidir. Anahtarlar dağıtımdan sonra yapılandırma dosyası aracılığıyla nasıl kullanıldığını kontrol edebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: oluşturma, başlatma ve yapılandırma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 İzleme kullanmayı düşündüğünüz bir uygulama geliştirirken, hem izleme ve iletileri uygulama kodunda hata ayıklama genellikle içerir. Uygulamayı dağıtmak hazır olduğunuzda açma olmadan, yayın derlemesi derleyebilirsiniz **hata ayıklama** koşullu öznitelik. Ancak, siz açabilirsiniz **izleme** koşullu özniteliğine derleyici izleme kodunuzu yürütülebilir dosya içerir. Daha fazla bilgi için bkz: [nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Kod izleme aşamaları  
 Kod izlemenin üç aşama vardır:  
  
1.  **İzleme** — izleme kodu uygulamanıza ekleyin.  
  
2.  **İzleme** — izleme kodu, belirtilen hedef bilgi yazar.  
  
3.  **Analiz** — tanımlamak ve uygulama sorunları anlamak için izleme bilgileri değerlendirin.  
  
 Geliştirme sırasında tüm hata ayıklama ve izleme yöntemleri Visual Studio çıktı penceresinde varsayılan bilgi yazmak çıktı. Dağıtılan bir uygulama yöntemleri belirttiğiniz hedefleri izleme bilgilerini yazın. İzleme veya hata ayıklama için Çıkış hedefini belirtme hakkında daha fazla bilgi için bkz: [izleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Ana adımlar çözümlemek ve dağıtılan uygulamalar olası sorunları düzeltmek için izleme kullanımında genellikle bir genel görünümünü verilmiştir. Bu adımların nasıl gerçekleştirileceğini hakkında daha fazla bilgi için uygun bağlantıyı bakın.  
  
##### <a name="to-use-tracing-in-an-application"></a>Bir uygulamada izlemeyi kullanmak için  
  
1.  Uygulamayı dağıttıktan sonra yerinde almak istediğiniz hangi izleme çıktısını göz önünde bulundurun.  
  
2.  Anahtar kümesi oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3.  Uygulama koduna izleme deyimleri ekleme.  
  
4.  İzleme çıktısı görüntülenir ve uygun dinleyiciler eklemek için istediğiniz belirler. Daha fazla bilgi için bkz: [oluşturma ve izleme dinleyicilerini başlatma](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5.  Test ve uygulamanız ve içerdiği izleme kodu hata ayıklama.  
  
6.  Aşağıdaki yordamlardan birini kullanarak yürütülebilir kod uygulamasına derleyin:  
  
    -   Kullanım **yapı** menüsü ile birlikte **hata ayıklama** sayfasında **özellik sayfaları** iletişim kutusunda **Çözüm Gezgini**. Bu, Visual Studio'da derlerken kullanın.  
  
         \-veya -  
  
    -   Kullanım **izleme** ve **hata ayıklama** derleyici yönergeleri derleme komut satırı yöntemi için. Daha fazla bilgi için bkz: [izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Bu komut satırından derlerken kullanın.  
  
7.  Çalışma zamanı sırasında bir sorun ortaya çıkarsa, uygun izleme anahtarı etkinleştirin. Daha fazla bilgi için bkz: [yapılandırma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     İzleme kodu izleme iletileri bir belirtilen hedef, örneğin, bir ekran, bir metin dosyası veya bir olay günlüğüne yazar. İçerdiği dinleyici türü **Trace.Listeners** koleksiyonu hedef belirler.  
  
8.  İzleme iletileri tanımlamak ve uygulama sorunu anlamak için analiz edin.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>İzleme Araçları ve dağıtılmış uygulamalar  
 Dağıtılmış bir uygulama oluşturduğunuzda, onu kullanılacak şekilde uygulamayı test zor bulabilirsiniz. Birkaç geliştirme ekiplerinin işletim sistemleri veya Web tarayıcıları (tüm yerelleştirilmiş dil seçenekleri dahil) tüm olası birleşimlerini test ya da aynı zamanda uygulama erişecek kullanıcılar yüksek sayısı benzetimini yapmak için özelliğine sahip. Bu koşullar altında yüksek hacim rakamlarına, farklı kurulumları ve benzersiz bir son kullanıcı davranışları için Dağıtılmış bir uygulamanın nasıl yanıt vereceğini test edilemez. Ayrıca, dağıtılmış uygulamanın pek çok bölümü ile doğrudan etkileşim veya bu bölümleri etkinliğini görüntülemek hiçbir kullanıcı arabirimine sahip olursunuz.  
  
 Ancak, bunun için sistem yöneticileri, özellikle tarafından yanlış Git şeyler ilgilendiren belirli olaylar açıklamak dağıtılmış uygulamaları etkinleştirerek dengeleyebilirsiniz *düzenleme* uygulama — diğer bir deyişle, göre yerleştirme izleme deyimleri kodunuzda stratejik konumlara. Beklenmeyen bir şey çalışma zamanında gerçekleşir varsa (örneğin, aşırı yavaş yanıt süresi), olası nedeni belirleyebilirsiniz.  
  
 İzleme deyimleri ile özgün kaynak kodunu inceleyerek, değiştirmeye, yeniden derlenmesi ve hata ayıklama ortamında çalışma zamanı hataya çalışılıyor zor görevini önleyebilirsiniz. Yalnızca hataları görüntülemek için aynı zamanda performansını izlemek için bir uygulama işaretleyebilir unutmayın.  
  
## <a name="strategic-placement-of-trace-statements"></a>İzleme deyimleri stratejik yerleşimi  
 Çalışma zamanı sırasında kullanmak için izleme deyimleri yerleştirirken özel dikkatli olmanız gerekir. Tüm olası izleme senaryoları yeterli kapsanan hangi izleme bilgilerini dağıtılan bir uygulama gerekli büyük olasılıkla, böylelikle dikkate almanız gerekir. Uygulamalar, kullandığından izleme farklılık yaygın olarak, ancak vardır izlemenin stratejik yerleştirme için hiçbir genel yönergeleri. İzleme deyimleri yerleştirme daha fazla bilgi için bkz: [nasıl yapılır: uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>İzleme çıktısı  
 İzleme çıkışının adlı nesneler tarafından toplanan *dinleyicileri*. Dinleyici izleme çıktısını alır ve çıktı cihazına (genellikle bir pencere, günlük veya metin dosyası) yazan bir nesnedir. İzleme dinleyicisi oluşturulduğunda, genellikle eklendiğinden <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> koleksiyon, tüm izleme çıktısı almak dinleyici izin verme.  
  
 Bilgi izleme her zaman yazılmış en az varsayılan <xref:System.Diagnostics.Trace> Çıkış hedefini <xref:System.Diagnostics.DefaultTraceListener>. Herhangi bir nedenden dolayı sildiyseniz <xref:System.Diagnostics.DefaultTraceListener> başka bir dinleyici eklemeden <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu, herhangi bir izleme iletisi almaz. Daha fazla bilgi için bkz: [izleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Altı <xref:System.Diagnostics.Debug> üyeleri ve <xref:System.Diagnostics.Trace> izleme bilgilerini yazma yöntemleri aşağıdaki tabloda listelenmiştir.  
  
|Yöntem|Çıkış|  
|------------|------------|  
|**Assert**|Belirtilen metni; ya da belirtilmemişse, çağrı yığınını. Çıktı, yalnızca koşul bir bağımsız değişken olarak belirttiyseniz yazılır **Assert** ifadesi **false**.|  
|**Başarısız**|Belirtilen metni; ya da belirtilmemişse, çağrı yığınını.|  
|**Yazma**|Belirtilen metin.|  
|**Writeıf**|Belirtilen metni koşul bir bağımsız değişken olarak belirtilmişse, **Writeıf** deyimi karşılandığında.|  
|**WriteLine**|Belirtilen metni ve bir satır başı karakteri.|  
|**Writelineıf**|Koşul bir bağımsız değişken olarak belirtilmişse Belirtilen metni ve bir satır başlarını, döndürür **Writelineıf** deyimi karşılandığında.|  
  
 İçindeki tüm dinleyicileri <xref:System.Diagnostics.Trace.Listeners%2A> koleksiyonu yukarıdaki tabloda açıklanan iletileri alırsınız, ancak yapılan Eylemler ne tür bir dinleyicisi iletiyi alır bağlı olarak değişebilir. Örneğin, <xref:System.Diagnostics.DefaultTraceListener> tarafından alındığında bir onaylama iletişim kutusu görüntüler bir **başarısız** veya başarısız **Assert** bildirim, ancak bir <xref:System.Diagnostics.TextWriterTraceListener> yalnızca çıktı kendi akışına yazar.  
  
 Kendi dinleyicisi uygulayarak özel sonuçlara yol açabilir. Özel İzleme dinleyicisi, örneğin, iletileri bir ileti kutusu görüntüleme veya iletileri bir tabloya eklemek için bir veritabanına bağlanın. Tüm özel dinleyicileri yukarıda belirtilen altı yöntemlerini desteklemesi gerekir. Geliştirici tarafından tanımlanan dinleyicileri oluşturma hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.TraceListener> .NET Framework başvurusu.  
  
> [!NOTE]
>  İçinde [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], **Debug.Write**, **Debug.WriteIf**, **Debug.WriteLine**, ve **Debug.WriteLineIf** yöntemleri değiştirildi **Debug.Print** Visual Basic önceki sürümlerinde kullanılabilir yöntemi.  
  
 **Yazma** ve **WriteLine** yöntemleri her zaman, belirttiğiniz metin yazma. **Assert**, **Writeıf**, ve **Writelineıf** olsun veya olmasın, belirtilen metnin yazma denetimleri Boolean bir bağımsız değişken gerektirir; bunlar ifade ise yalnızca belirtilen metin yazma **true** (için **Writeıf** ve **Writelineıf**), veya **false** (için **Assert**). **Başarısız** yöntemi, belirtilen metnin her zaman yazar. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) ve .NET Framework başvurusu.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
 Uygulamanız, izleme ve ASP.NET uygulamasını dağıtmadan önce hata ayıklama devre dışı bırakmayın, kötü amaçlı bir program tarafından yararlanılabilir kendi hakkında bilgileri olduğunu gösterebilir. Daha fazla bilgi için bkz: [nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [derlemek ve oluşturmak](/visualstudio/ide/compiling-and-building-in-visual-studio), ve [nasıl yapılır: oluşturma, başlatma ve yapılandırma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md) . Hata ayıklama aynı zamanda Internet Information Services (IIS) aracılığıyla yapılandırılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 [Kod sözleşmeleri](../../../docs/framework/debug-trace-profile/code-contracts.md)  
 [C#, F # ve Visual Basic proje türleri](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)  
 [Nasıl yapılır: uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [Nasıl yapılır: oluşturma ve başlatma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Nasıl yapılır: oluşturma ve başlatma izleme kaynakları](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [Nasıl yapılır: iz dinleyicileri ile TraceSource ve filtreler kullanma](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)  
 [İzleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [İzleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
