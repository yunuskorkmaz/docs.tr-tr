---
title: İzleme Anahtarları
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b8ee0d04644cf504354767c296f504a937055d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="trace-switches"></a>İzleme Anahtarları
İzleme anahtarları etkinleştir, devre dışı bırakın ve İzleme çıktısı filtrelemek etkinleştirin. Bunlar, kodunuzda var ve dışarıdan .config dosyası aracılığıyla yapılandırılabilir nesneleridir. .NET Framework sağlanan izleme anahtarları üç tür vardır: <xref:System.Diagnostics.BooleanSwitch> sınıfı, <xref:System.Diagnostics.TraceSwitch> sınıfı ve <xref:System.Diagnostics.SourceSwitch> sınıfı. <xref:System.Diagnostics.BooleanSwitch> Bir iki durumlu izleme deyimleri çeşitli devre dışı bırakma veya etkinleştirme anahtarı, sınıf görevi görür. <xref:System.Diagnostics.TraceSwitch> Ve <xref:System.Diagnostics.SourceSwitch> sınıfların belirli izleme düzeyi için bir izleme anahtarı etkinleştirin izin verecek şekilde <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.TraceSource> bu düzeyin altındaki tüm düzeyleri için belirtilen iletileri görüntülenir. Anahtar devre dışı bırakırsanız, izleme iletileri görüntülenmez. Özet bu sınıfların türetilmesi (**MustInherit**) sınıf **anahtar**gibi bir kullanıcı tarafından geliştirilen anahtar gerekir.  
  
 İzleme anahtarları bilgi filtreleme için yararlı olabilir. Örneğin, her bir veri erişim modülünden izleme iletisinde, ancak uygulamanın geri kalanına yalnızca hata iletilerini görmek isteyebilirsiniz. Bu durumda, uygulama geri kalanı için bir izleme için veri erişim modülünden ve bir anahtarı kullanırsınız. Anahtarlar için uygun ayarları yapılandırmak için .config dosyası kullanarak, aldığınız izleme iletisi ne tür denetleyebilir. Daha fazla bilgi için bkz: [nasıl yapılır: oluşturma, başlatma ve yapılandırma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Genellikle, kullanıcıların bir ekranda görünen veya uygulama çalışırken bir günlük dosyasını doldurma ilgisiz izleme iletilerini çok Gözlemleme böylece dağıtılan bir uygulama devre dışı, kendi anahtarlarıyla yürütülür. Uygulama yürütme sırasında bir sorun ortaya çıkarsa, uygulamayı durdurun, anahtarları etkinleştirmek ve uygulamayı yeniden başlatın. Ardından izleme iletileri görüntülenir.  
  
 Bir anahtar kullanmak için önce bir anahtar nesneden oluşturmalısınız bir **BooleanSwitch** sınıfı, bir **TraceSwitch** sınıfı ya da bir geliştirici tarafından tanımlanan anahtar sınıfı. Geliştirici tarafından tanımlanan anahtarları oluşturma hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.Switch> sınıf .NET Framework başvurusu. Sonra ne zaman kullanılacak anahtarı nesne olduğunu belirten bir yapılandırma değeri ayarlayın. Ardından anahtar nesnesinin ayarı çeşitli içinde test **izleme** (veya **hata ayıklama**) izleme yöntemleri.  
  
## <a name="trace-levels"></a>İzleme düzeyi  
 Kullandığınızda **TraceSwitch**, ek noktalar vardır. A **TraceSwitch** nesnesi döndüren dört özellikleri sahip **Boolean** anahtar belirli en az bir düzeye ayarlanıp ayarlanmadığını gösteren değerler:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Düzeyleri, bir sorunu çözmek için gereken bu bilgileri yalnızca aldığınız izleme bilgilerinin miktarını sınırlamak izin verir. Ayarlama ve izleme anahtarları uygun izleme düzeyi için yapılandırarak, izleme çıktısı istediğiniz ayrıntı düzeyini belirtin. Hiç hata iletileri, uyarı iletileri, bilgilendirici iletileri, ayrıntılı izleme iletileri veya hiçbir ileti alabilir.  
  
 Her düzey ile ilişkilendirmek için ileti türlerini karar vermenizi kadar tamamen olur. Genellikle, her düzeyi ile ilişkilendirmek izleme iletileri içeriğini bağlıdır, ancak düzeyleri arasındaki farklar belirleyin. Bir sorun 3 düzeyinde ayrıntılı açıklamaları sağlamak isteyebilir (**bilgisi**), örneğin, ancak yalnızca bir hata başvuru numarası 1 düzeyinde sağlar (**hata**). Tamamen hangi düzeni uygulamanızda iyi karar vermenize olanak kadar olur.  
  
 Bu özelliklerin değerleri 1-4 arası karşılık gelen **TraceLevel** numaralandırması. Aşağıdaki tabloda düzeylerini listeler **TraceLevel** numaralandırma ve değerleri.  
  
|Enum değeri|Tamsayı değeri|Görüntülenen ileti türünü (veya belirtilen çıkış hedefe yazılmış)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Kapalı|0|Yok.|  
|Hata|1.|Yalnızca hata iletileri|  
|Uyarı|2|Uyarı iletileri ve hata iletileri|  
|Bilgi|3|Bilgilendirici iletileri, uyarı iletileri ve hata iletileri|  
|Ayrıntılı|4|Ayrıntılı iletiler, bilgilendirici iletileri, uyarı iletileri ve hata iletileri|  
  
 **TraceSwitch** özellikleri anahtar için en fazla izleme düzeyini gösterir. Diğer bir deyişle, izleme bilgilerini de olduğu gibi tüm düzeylerinde belirtilen düzeyi için yazılmış olmalıdır. Örneğin, varsa **TraceInfo** olan **true**, ardından **TraceError** ve **TraceWarning** de **doğru** ancak **TraceVerbose** iyi olabilir **false**.  
  
 Bu, salt okunur özelliklerdir. **TraceSwitch** nesne otomatik olarak ayarlar bunları zaman **TraceLevel** özelliği ayarlanmış. Örneğin:  
  
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
  
## <a name="developer-defined-switches"></a>Geliştirici tarafından tanımlanan anahtarları  
 Sağlama yanı sıra **BooleanSwitch** ve **TraceSwitch**, devralarak kendi anahtarları tanımlayabilirsiniz **anahtar** sınıf ve taban sınıf yöntemlerini geçersiz kılma özelleştirilmiş yöntemleriyle. Geliştirici tarafından tanımlanan anahtarları oluşturma hakkında daha fazla bilgi için bkz: <xref:System.Diagnostics.Switch> sınıf .NET Framework başvurusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
