---
title: .NET Yerel ile Başlangıç İyileştirmesini Hesaplama
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
ms.openlocfilehash: 41a693f18ffea0e5ce0ca742bc251d147e8e3784
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180992"
---
# <a name="measuring-startup-improvement-with-net-native"></a>.NET Yerel ile Başlangıç İyileştirmesini Hesaplama
.NET Native uygulamaların lansman süresini önemli ölçüde artırır. Bu gelişme özellikle taşınabilir, düşük güçlü cihazlarda ve karmaşık uygulamalarda fark edilir. Bu konu, bu başlangıç geliştirmeölçmek için gerekli temel enstrümantasyon ile başlamak yardımcı olur.  
  
 Performans araştırmalarını kolaylaştırmak için .NET Framework ve Windows, uygulamanızın olaylar olduğunda araç kullanımını bildirmesine olanak tanıyan Windows için Olay İzleme (ETW) adlı bir olay çerçevesi kullanır. Daha sonra ETW olaylarını kolayca görüntülemek ve analiz etmek için PerfView adlı bir araç kullanabilirsiniz. Bu konu nasıl açıklanıyor:  
  
- Olayları <xref:System.Diagnostics.Tracing.EventSource> yayıltmak için sınıfı kullanın.  
  
- Bu olayları toplamak için PerfView'i kullanın.  
  
- Bu olayları görüntülemek için PerfView'i kullanın.  
  
## <a name="using-eventsource-to-emit-events"></a>Olayları yayıltmak için EventSource'u kullanma  
 <xref:System.Diagnostics.Tracing.EventSource>özel bir olay sağlayıcısı oluşturmak için hangi bir taban sınıf sağlar. Genellikle, kendi olay yöntemleri <xref:System.Diagnostics.Tracing.EventSource> ile `Write*` bir alt sınıf oluşturmak ve yöntemleri sarın. Bir singleton deseni genellikle <xref:System.Diagnostics.Tracing.EventSource>her biri için kullanılır.  
  
 Örneğin, aşağıdaki örnekteki sınıf iki performans özelliğini ölçmek için kullanılabilir:  
  
- Sınıf oluşturucusu `App` çağrılana kadar olan zaman.  
  
- `MainPage` Yapıcı nın çağrıldaki zamanı.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Burada dikkat ived etmek için birkaç şey vardır. İlk olarak, bir singleton `AppEventSource.Log`oluşturulur. Bu örnek tüm günlüğe kaydetme için kullanılır. İkinci olarak, her <xref:System.Diagnostics.Tracing.EventAttribute>olay yönteminin bir . Bu, takımlamanın <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> yöntemin dizinini çağrılan `AppEventSource`yöntemle ilişkilendirmesine yardımcı olur.  
  
 Bu olayların tamamen açıklayıcı olduğunu unutmayın. Çoğu uygulama kodu bu olaylardan sonra çalışır. Koddaki hangi olayların kullanıcı etkileşimlerine karşılık geldiğini anlamalı, bunları ölçmeli ve bu ölçütleri geliştirmelisiniz. Ayrıca, olayların kendileri zaman içinde yalnızca tek bir örnek günlük. Genellikle her işlem için eşleşen başlangıç ve durdurma olayları olması yararlıdır. Uygulama başlatma yı incelerken, başlangıç olayı genellikle işletim sisteminin yadığı "İşlem/Başlat" olayıdır.  
  
 Örneğin, bir RSS okuyucu oluşturduğunuzu varsayalım. Bir olayı günlüğe kaydetmek için birkaç ilginç konum şunlardır:  
  
- Ana sayfa ilk işlendiğinde.  
  
- Eski RSS hikayeleri yerel depolamadan deserialized olduğunda.  
  
- Uygulamanız yeni haberleri eşitlemeye başladığında.  
  
- Uygulamanız yeni haberleri eşitlemeyi bitirdiğinde.  
  
 Bir uygulamayı enstrümanting basittir: Sadece türemiş sınıf üzerinde uygun yöntemi arayın. Önceki `AppEventSource` örnekten kullanarak, bir uygulamayı aşağıdaki gibi enstrümanta layabilirsiniz:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Uygulama işletildiğinde, etkinlikleri toplamaya hazırsınız.  
  
## <a name="gathering-events-with-perfview"></a>PerfView ile etkinlik toplama  
 PerfView, uygulamanızda her türlü performans araştırmasını yapmanıza yardımcı olmak için ETW etkinliklerini kullanır. Ayrıca, farklı türde olaylar için günlüğe kaydetmeyi açmanızı veya kapatmanızı sağlayan bir yapılandırma GUI içerir. PerfView ücretsiz bir araçtır ve [Microsoft Download Center'dan](https://www.microsoft.com/download/details.aspx?id=28567)indirilebilir. Daha fazla bilgi için [PerfView öğretici videolarını](https://channel9.msdn.com/Series/PerfView-Tutorial)izleyin.  
  
> [!NOTE]
> PerfView ARM sistemlerinde olayları toplamak için kullanılamaz. ARM sistemlerinde olayları toplamak için Windows Performance Recorder (WPR) kullanın. Daha fazla bilgi için [Vance Morrison'ın blog yazısına](https://docs.microsoft.com/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device)bakın.  
  
 Komut satırından PerfView'i de çağırabilirsiniz. Yalnızca sağlayıcınızdaki olayları günlüğe kaydetmek için Komut İstem penceresini açın ve komutu girin:  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile
```  
  
 burada:  
  
 `-KernelEvents:Process`  
 İşlemin ne zaman başlayıp durduğunu bilmek istediğinizi gösterir. Uygulamanızın diğer etkinlik saatlerinden çıkarılabilmeleri için Uygulamanız için İşlem/Başlangıç etkinliğine ihtiyacınız var.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 PerfView'in varsayılan olarak açtığı diğer sağlayıcıları kapatır ve MyCompany-MyApp sağlayıcısını açar.  (Yıldız işareti bunun bir <xref:System.Diagnostics.Tracing.EventSource>.) olduğunu gösterir.  
  
 `collect outputFile`  
 Toplamayı başlatmak ve verileri outputFile.etl.zip'e kaydetmek istediğinizi gösterir.  
  
 PerfView'i çalıştırdıktan sonra uygulamanızı çalıştırın. Uygulamanızı çalıştırırken hatırlanması gereken birkaç şey vardır:  
  
- Hata ayıklama oluşturma değil, sürüm oluşturma oluşturma kullanın. Hata ayıklama oluşturur genellikle uygulamanızın beklenenden daha yavaş çalışmasına neden olabilecek ekstra hata denetimi ve hata işleme kodu içerir.  
  
- Uygulamanızı ekli bir hata ayıklama yla çalıştırmak uygulamanızın performansını etkiler.  
  
- Windows, uygulama başlatma sürelerini hızlandırmak için birden çok önbelleğe alma stratejileri kullanır. Uygulamanız şu anda bellekte önbelleğe alınmışsa ve diskten yüklenmesi gerekmiyorsa, daha hızlı başlar. Tutarlılık sağlamak için, uygulamanızı ölçmeden önce birkaç kez başlatın ve kapatın.  
  
 PerfView'in yayılan olayları toplayabilmesi için uygulamanızı çalıştırdığınızda, **Koleksiyonu Durdur** düğmesini seçin. Genellikle, uygulamanızı kapatmadan önce koleksiyonu durdurmalısınız, böylece gereksiz etkinliklere girmemelisiniz. Ancak, kapatma veya askıya alma performansını ölçüyorsanız, toplamaya devam etmek istersiniz.  
  
## <a name="displaying-the-events"></a>Olayları görüntüleme  
 Zaten toplanmış olayları görüntülemek için, oluşturduğunuz .etl veya .etl.zip dosyasını açmak için PerfView'i kullanın ve **Etkinlikler'i**seçin. ETW, diğer süreçlerden gelen olaylar da dahil olmak üzere çok sayıda olay hakkında bilgi toplamış olacaktır. Araştırmanızı odaklamak için, etkinlik görünümünde aşağıdaki metin kutularını doldurun:  
  
- İşlem **Filtresi** kutusunda, uygulama adınızı (".exe" olmadan) belirtin.  
  
- Olay **Türleri Filtresi** kutusunda. `Process/Start | MyCompany-MyApp` Bu, MyCompany-MyApp ve Windows Çekirdeği/İşlem/Başlat etkinliğindeki olaylar için bir filtre ayarlar.  
  
 Sol bölmede (Ctrl-A) listelenen tüm olayları seçin ve **Enter** tuşunu seçin. Şimdi, her olay zaman damgaları görmek gerekir. Bu zaman damgaları izlemenin başlangıcına göredir, bu nedenle başlangıçtan bu yana geçen süreyi belirlemek için her olayın saatini işlemin başlangıç saatinden çıkarmanız gerekir. İki zaman damgası seçmek için Ctrl+Click kullanıyorsanız, sayfanın altındaki durum çubuğunda görüntülenen satır aralarındaki farkı görürsünüz. Bu, ekrandaki iki olay arasında geçen süreyi (işlem başlangıcı dahil) görmenizi kolaylaştırır. Görünüm için kısayol menüsünü açabilir ve verileri kaydetmek veya işlemek için CSV dosyalarına dışa aktarma veya Microsoft Excel'i açma gibi bir dizi yararlı seçenek arasından seçim yapabilirsiniz.  
  
 Hem orijinal uygulamanız hem de .NET Native araç zincirini kullanarak oluşturduğunuz sürüm için yordamı yineleyerek performans farkını karşılaştırabilirsiniz.   .NET Yerel uygulamalar genellikle non-.NET Yerel uygulamalardan daha hızlı başlar. Daha derine inmeyle ilgileniyorsanız, PerfView kodunuzun en çok zaman alan bölümlerini de belirleyebilir. Daha fazla bilgi için [PerfView eğitimlerini](https://channel9.msdn.com/Series/PerfView-Tutorial) izleyin veya [Vance Morrison'ın blog girişini](https://docs.microsoft.com/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool)okuyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Tracing.EventSource>
