---
title: İzleme Anahtarları
description: İzleme çıkışlarını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlayan izleme anahtarlarını keşfet. .NET, BooleanSwitch, TraceSwitch ve SourceSwitch sınıflarını sağlar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
ms.openlocfilehash: 29de46afa2a96dd7011cec40f4f76e7bfb8ee454
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803542"
---
# <a name="trace-switches"></a>İzleme Anahtarları
İzleme anahtarları, izleme çıkışını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar. Bunlar, kodunuzda var olan ve. config dosyası aracılığıyla dışarıdan yapılandırılabilecekleri nesnelerdir. .NET Framework üç tür izleme anahtarı vardır: <xref:System.Diagnostics.BooleanSwitch> sınıfı, <xref:System.Diagnostics.TraceSwitch> sınıfı ve <xref:System.Diagnostics.SourceSwitch> sınıfı. <xref:System.Diagnostics.BooleanSwitch>Sınıfı, çeşitli izleme deyimlerini etkinleştirmek veya devre dışı bırakmak için iki durumlu anahtar işlevi görür. <xref:System.Diagnostics.TraceSwitch>Ve <xref:System.Diagnostics.SourceSwitch> sınıfları belirli bir izleme düzeyi için bir izleme anahtarı etkinleştirmenizi sağlar, böylece <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.TraceSource> Bu düzeyi ve altındaki tüm düzeyler için belirtilen iletiler görüntülenir. Anahtarı devre dışı bırakırsanız izleme iletileri görünmez. Tüm bu sınıflar, Kullanıcı tarafından geliştirilen tüm anahtarlar gibi soyut (**MustInherit**) sınıf **anahtarından**türetilir.  
  
 İzleme anahtarları, bilgileri filtrelemek için yararlı olabilir. Örneğin, bir veri erişim modülündeki her izleme iletisini görmek isteyebilirsiniz, ancak yalnızca uygulamanın geri kalanında hata iletileri görebilirsiniz. Bu durumda, veri erişim modülü için bir izleme anahtarı ve uygulamanın geri kalanı için bir anahtar kullanırsınız. Anahtarları uygun ayarlara göre yapılandırmak için. config dosyasını kullanarak hangi türde iz iletileri aldığınızı denetleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: oluşturma, başlatma ve yapılandırma Izleme anahtarları](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Genellikle dağıtılan bir uygulama, anahtarları devre dışı bırakılmış olarak yürütülür. böylece kullanıcılar ekranda görüntülenen çok sayıda ilgisiz izleme iletisini gözlemlemeye veya uygulama çalışırken bir günlük dosyasının doldurulmasına gerek kalmaz. Uygulama yürütme sırasında bir sorun oluşursa, uygulamayı durdurabilir, anahtarları etkinleştirebilir ve uygulamayı yeniden başlatabilirsiniz. İzleme iletileri görüntülenir.  
  
 Bir anahtar kullanmak için önce bir **BooleanSwitch** sınıfından, **TraceSwitch** sınıfından veya bir geliştirici tanımlı anahtar sınıfından bir Switch nesnesi oluşturmanız gerekir. Geliştirici tanımlı anahtarlar oluşturma hakkında daha fazla bilgi için <xref:System.Diagnostics.Switch> .NET Framework başvurusu içindeki sınıfına bakın. Ardından, anahtar nesnesinin ne zaman kullanılacağını belirten bir yapılandırma değeri ayarlarsınız. Daha sonra, farklı **izleme** (veya **hata ayıklama**) izleme yöntemlerinde Switch nesnesinin ayarını test edersiniz.  
  
## <a name="trace-levels"></a>İzleme düzeyleri  
 **TraceSwitch**kullandığınızda ek hususlar vardır. Bir **TraceSwitch** nesnesi, anahtarın en az belirli bir düzeye ayarlanmış olup olmadığını belirten **Boolean** değerler döndüren dört özelliğe sahiptir:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Düzeyler, aldığınız izleme bilgilerini yalnızca bir sorunu çözmek için gereken bilgilere göre sınırlamanızı sağlar. İzleme anahtarlarını uygun izleme düzeyine ayarlayarak ve yapılandırarak, izleme çıktılarınızda istediğiniz ayrıntı düzeyini belirtirsiniz. Hata iletileri, uyarı iletileri, bilgilendirici iletiler, ayrıntılı izleme iletileri veya hiç ileti yok alabilirsiniz.  
  
 Her bir düzeyle ne tür bir ileti ilişkilendirileceğini belirlemek tamamen sizin için önemlidir. Genellikle, izleme iletilerinin içeriği her bir düzeyle ilişkilendirdiklerinize bağlıdır, ancak Düzeyler arasındaki farkları belirlersiniz. Örneğin, düzey 3 ' te (**bilgi**) bir sorunun ayrıntılı açıklamalarını sağlamak isteyebilirsiniz, ancak düzey 1 ' de yalnızca bir hata başvuru numarası sağlayın (**hata**). Uygulamanızda en iyi şekilde hangi düzenin en iyi şekilde çalıştığını belirlemek tamamen sizin için önemlidir.  
  
 Bu özellikler, **TraceLevel** numaralandırması için 1 ile 4 arasında bir değere karşılık gelir. Aşağıdaki tabloda, **TraceLevel** numaralandırması ve bunların değerleri listelenmiştir.  
  
|Numaralandırılmış değer|Tamsayı değeri|Görüntülenecek ileti türü (veya belirtilen bir çıktı hedefine yazıldı)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Kapalı|0|Hiçbiri|  
|Hata|1|Yalnızca hata iletileri|  
|Uyarı|2|Uyarı iletileri ve hata iletileri|  
|Bilgi|3|Bilgilendirici iletiler, uyarı iletileri ve hata iletileri|  
|Ayrıntılı|4|Ayrıntılı iletiler, bilgilendirici iletiler, uyarı iletileri ve hata iletileri|  
  
 **TraceSwitch** özellikleri, anahtar için en yüksek izleme düzeyini gösterir. Diğer bir deyişle, izleme bilgileri, belirtilen düzeyin yanı sıra tüm alt düzeyler için yazılır. Örneğin, **TraceInfo** **true**Ise **TraceError** ve **TraceWarning** da **true** , ancak **TraceVerbose** de **false**olabilir.  
  
 Bu özellikler salt okunurdur. **TraceSwitch** nesnesi, **TraceLevel** özelliği ayarlandığında onları otomatik olarak ayarlar. Örneğin:  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>Geliştirici tanımlı anahtarlar  
 **BooleanSwitch** ve **TraceSwitch**sağlamaya ek olarak, **anahtar** sınıfından devralarak ve temel sınıf yöntemlerini özelleştirilmiş yöntemlerle geçersiz kılarak kendi anahtarlarınızı tanımlayabilirsiniz. Geliştirici tanımlı anahtarlar oluşturma hakkında daha fazla bilgi için <xref:System.Diagnostics.Switch> .NET Framework başvurusu içindeki sınıfına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İz Dinleyicileri](trace-listeners.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
