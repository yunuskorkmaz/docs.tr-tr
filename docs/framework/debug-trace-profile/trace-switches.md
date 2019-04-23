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
ms.openlocfilehash: 85a1a017197826717280f53995ed98f26f1d80bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132671"
---
# <a name="trace-switches"></a>İzleme Anahtarları
İzleme anahtarları etkinleştirmek, devre dışı bırakın ve İzleme çıkışı filtrelemek olanak sağlar. Bunlar, mevcut kodunuzu ve .config dosyası aracılığıyla harici olarak yapılandırılabilir nesnelerdir. .NET Framework içinde sağlanan izleme anahtarlarını üç tür vardır: <xref:System.Diagnostics.BooleanSwitch> sınıfı <xref:System.Diagnostics.TraceSwitch> sınıfı ve <xref:System.Diagnostics.SourceSwitch> sınıfı. <xref:System.Diagnostics.BooleanSwitch> Bir iki durumlu izleme deyimleri çeşitli devre dışı bırakma veya etkinleştirme anahtarı, sınıf görevi görür. <xref:System.Diagnostics.TraceSwitch> Ve <xref:System.Diagnostics.SourceSwitch> sınıfları belirli izleme düzeyi için bir izleme anahtarı etkinleştirmenize izin böylece <xref:System.Diagnostics.Trace> veya <xref:System.Diagnostics.TraceSource> düzeyi ve altındaki tüm düzeyleri için belirtilen iletileri görüntülenir. Geçiş devre dışı bırakırsanız, izleme iletileri görüntülenmez. Bu sınıflar türetilen Özet (**MustInherit**) sınıfı **anahtar**gibi bir kullanıcı tarafından geliştirilen anahtar gerekir.  
  
 İzleme anahtarları bilgi filtreleme için yararlı olabilir. Örneğin, bir veri erişim modülünden her izleme iletisi, ancak uygulamanın geri kalanında yalnızca hata iletileri görmek isteyebilirsiniz. Bu durumda, uygulama geri kalanı için bir izleme anahtarı için veri erişim modülünden ve bir anahtarı kullanırsınız. Anahtarlar için uygun ayarları yapılandırmak için .config dosyasını kullanarak, ne tür bir izleme iletisi aldığınız denetleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Genellikle, kullanıcıların ekranda görünmesini veya uygulama çalışırken bir günlük dosyasının doldurma ilgisiz izleme iletilerini birçok Gözlemleme böylece dağıtılan bir uygulama devre dışı, kendi anahtarlarıyla yürütülür. Uygulama yürütme sırasında bir sorun ortaya çıkarsa, uygulamayı durdurun, anahtarlar etkinleştirin ve uygulamayı yeniden başlatın. Ardından izleme iletileri görüntülenir.  
  
 Bir anahtar kullanmak için önce bir anahtar nesneden oluşturmanız gerekir bir **BooleanSwitch** sınıfı, bir **TraceSwitch** sınıfı ya da bir geliştirici tarafından tanımlanan anahtar sınıfı. Geliştirici tanımlı anahtarlar oluşturma hakkında daha fazla bilgi için bkz. <xref:System.Diagnostics.Switch> sınıfı .NET Framework başvurusu. Sonra kullanılacak anahtar nesnesi olduğunda belirten bir yapılandırma değeri ayarlayın. Ardından anahtar nesnesinin çeşitli test ayarı **izleme** (veya **hata ayıklama**) izleme yöntemleri.  
  
## <a name="trace-levels"></a>İzleme düzeyi  
 Kullanırken **TraceSwitch**, ek hususlar vardır. A **TraceSwitch** döndüren dört özellikler nesnesinde **Boole** anahtar belirli en az bir düzeye ayarlanıp ayarlanmadığını belirten değerleri:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Düzeyleri, bir sorunu çözmek için gereken bu bilgileri yalnızca aldığınız izleme bilgilerinin miktarını sınırlamak sağlar. Ayarlayarak ve uygun izleme düzeyi için izleme anahtarları yapılandırma, izleme çıktısı istediğiniz ayrıntı düzeyini belirtin. Hiç hata iletileri, uyarı iletilerini, bilgilendirme iletileri, ayrıntılı izleme iletileri veya ileti alabilir.  
  
 Bu, hangi tür iletilerin her düzeyi ile ilişkilendirilecek karar vermenize kadar tamamen olur. Genellikle, her düzeyi ile ilişkilendirmek izleme iletileri içeriğini bağlıdır, ancak düzeyleri arasındaki farklar belirleyin. Bir sorun 3 düzeyinde ayrıntılı açıklamaları sağlamak isteyebilirsiniz (**bilgisi**), örneğin, ancak yalnızca bir hata başvuru numarası 1 düzeyinde sağlar (**hata**). Bu, uygulamanızda hangi düzeni iyi karar vermenize kadar tamamen olur.  
  
 Bu özelliklerin değerleri 1 ile 4 karşılık gelen **TraceLevel** sabit listesi. Aşağıdaki tabloda düzeyleri **TraceLevel** sabit listesi ve bunların değerleri.  
  
|Enum değeri|Tamsayı değeri|Görüntülenen ileti türü (veya belirtilen çıkış hedefine yazılmış)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Kapalı|0|Yok.|  
|Hata|1.|Yalnızca hata iletileri|  
|Uyarı|2|Uyarı iletileri ve hata iletileri|  
|Bilgi|3|Bilgilendirme iletileri, uyarı iletileri ve hata iletileri|  
|Ayrıntılı|4|Ayrıntılı iletiler, bilgilendirme iletileri, uyarı iletileri ve hata iletileri|  
  
 **TraceSwitch** özellikleri anahtar için en fazla izleme düzeyini belirtir. Diğer bir deyişle, izleme bilgileri de olduğu gibi tüm alt düzeyleri belirtilen düzeyi için yazılır. Örneğin, varsa **TraceInfo** olduğu **true**, ardından **TraceError** ve **Tacewarning** de **true** ancak **TraceVerbose** de ilginizi çekebilir **false**.  
  
 Bu özellikleri salt okunurdur. **TraceSwitch** nesne otomatik olarak ayarlar bunları zaman **TraceLevel** özelliği ayarlanmış. Örneğin:  
  
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
 Sağlamaya ek olarak **BooleanSwitch** ve **TraceSwitch**, kendi anahtarları devralarak tanımlayabileceğiniz **anahtar** sınıfı ve taban sınıf yöntemlerini geçersiz kılma özelleştirilmiş yöntemleri ile. Geliştirici tanımlı anahtarlar oluşturma hakkında daha fazla bilgi için bkz. <xref:System.Diagnostics.Switch> sınıfı .NET Framework başvurusu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
