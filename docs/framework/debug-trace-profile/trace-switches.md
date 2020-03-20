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
ms.openlocfilehash: a8ce4ee5de4d330b88e98e85cce4b6547e969613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181725"
---
# <a name="trace-switches"></a>İzleme Anahtarları
İzleme anahtarları, izleme çıktısını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar. Bunlar, kodunuzda bulunan ve .config dosyası aracılığıyla dışarıdan yapılandırılabilen nesnelerdir. .NET Framework'de sağlanan üç tür izleme anahtarı <xref:System.Diagnostics.BooleanSwitch> vardır: <xref:System.Diagnostics.TraceSwitch> sınıf, <xref:System.Diagnostics.SourceSwitch> sınıf ve sınıf. Sınıf, <xref:System.Diagnostics.BooleanSwitch> çeşitli izleme deyimlerini etkinleştiren veya devre dışı bırakan bir geçiş anahtarı görevi görür. Ve <xref:System.Diagnostics.TraceSwitch> <xref:System.Diagnostics.SourceSwitch> sınıflar, belirli bir izleme düzeyi için izleme anahtarını <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.TraceSource> etkinleştirmenize izin verir, böylece o düzey için belirtilen iletiler ve altındaki tüm düzeyler görünür. Anahtarı devre dışı bederseniz, izleme iletileri görünmez. Tüm bu sınıflar soyut türetilmiştir (**MustInherit**) sınıf **Switch**, herhangi bir kullanıcı tarafından geliştirilen anahtarları gerektiği gibi.  
  
 İzleme anahtarları bilgileri filtreleme için yararlı olabilir. Örneğin, bir veri erişim modülündeki her izleme iletisini görmek isteyebilirsiniz, ancak uygulamanın geri kalanında yalnızca hata iletileri. Bu durumda, veri erişim modülü için bir izleme anahtarı ve uygulamanın geri kalanı için bir anahtar kullanırsınız. Anahtarları uygun ayarlara yapılandırmak için .config dosyasını kullanarak, aldığınız izleme iletisi türlerini denetleyebilirsiniz. Daha fazla bilgi için [bkz: İzleme Anahtarlarını Oluşturma, Başlatma ve Yapılandırma.](how-to-create-initialize-and-configure-trace-switches.md)  
  
 Genellikle, dağıtılan bir uygulama anahtarları devre dışı bırakılmış olarak yürütülür, böylece kullanıcıların bir ekranda görünen alakasız izleme iletileri çok gözlemlemek gerekmez veya uygulama çalışırken bir günlük dosyası doldurma. Uygulama yürütme sırasında bir sorun ortaya çıkarsa, uygulamayı durdurabilir, anahtarları etkinleştirebilir ve uygulamayı yeniden başlatabilirsiniz. Ardından izleme iletileri görüntülenir.  
  
 Bir anahtarı kullanmak için önce **BooleanSwitch** sınıfından, **TraceSwitch** sınıfından veya geliştirici tanımlı bir anahtar sınıfından bir anahtar nesnesi oluşturmanız gerekir. Geliştirici tanımlı anahtarlar oluşturma hakkında daha <xref:System.Diagnostics.Switch> fazla bilgi için .NET Framework başvurusundasınıfa bakın. Ardından, anahtar nesnesinin ne zaman kullanılacağını belirten bir yapılandırma değeri ayarlarsınız. Daha sonra, çeşitli **İzleme** (veya Hata **Ayıklama)** izleme yöntemlerinde anahtar nesnesinin ayarını sınarsınız.  
  
## <a name="trace-levels"></a>İzleme Düzeyleri  
 **TraceSwitch'i**kullandığınızda, başka hususlar da vardır. **TraceSwitch nesnesi,** anahtarın en az belirli bir düzeye ayarlanıp ayarlanmadığını belirten **Boolean** değerlerini döndüren dört özellime sahiptir:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Düzeyler, aldığınız izleme bilgisini yalnızca bir sorunu çözmek için gereken bilgilerle sınırlamanıza olanak sağlar. İzleme anahtarlarını uygun izleme düzeyine ayarlayarak ve yapılandırarak izleme çıktınızda istediğiniz ayrıntı düzeyini belirtirsiniz. Hata iletileri, uyarı iletileri, bilgilendirme iletileri, ayrıntılı izleme iletileri veya hiç ileti alabilirsiniz.  
  
 Her düzeyde ne tür bir mesaj ilişkilendirmek için karar vermek tamamen size kalmış. Genellikle, iletileri izlemenin içeriği her düzeyle ilişkilendirdiğiniz içeriğe bağlıdır, ancak düzeyler arasındaki farkları siz belirlersiniz. Örneğin, düzey 3 **'de**bir sorunun ayrıntılı açıklamalarını sağlamak isteyebilirsiniz, ancak düzey 1'de yalnızca bir hata referans numarası **(Hata)** sağlayabilirsiniz. Uygulamanızda hangi şemanın en iyi şekilde çalıştığına karar vermek tamamen size kalmış.  
  
 Bu **özellikler, TraceLevel** numaralandırmasının 1 ile 4 arasındaki değerlerine karşılık gelir. Aşağıdaki tabloda **TraceLevel** numaralandırma düzeyleri ve değerleri listeleneb.rı.  
  
|Numaralandırılmış değer|Tamsayı değeri|Görüntülenen ileti türü (veya belirli bir çıktı hedefine yazılır)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Kapalı|0|None|  
|Hata|1|Yalnızca hata iletileri|  
|Uyarı|2|Uyarı iletileri ve hata iletileri|  
|Bilgi|3|Bilgilendirme iletileri, uyarı iletileri ve hata iletileri|  
|Ayrıntılı|4|Ayrıntılı mesajlar, bilgilendirme iletileri, uyarı iletileri ve hata iletileri|  
  
 **TraceSwitch** özellikleri, anahtar için maksimum izleme düzeyini gösterir. Diğer bir süre, izleme bilgileri belirtilen düzey in yanı sıra tüm alt düzeyler için yazılır. Örneğin, **TraceInfo** **doğruysa,** **TraceError** ve **TraceWarning** da **doğrudur** ancak **TraceVerbose** yanlış **olabilir.**  
  
 Bu özellikler salt okunur. **TraceLevel** özelliği ayarlandığında **TraceSwitch** nesnesi bunları otomatik olarak ayarlar. Örnek:  
  
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
  
## <a name="developer-defined-switches"></a>Geliştirici Tanımlı Anahtarlar  
 **BooleanSwitch** ve **TraceSwitch**sağlamanın yanı sıra, **Switch** sınıfından devralarak ve özelleştirilmiş yöntemlerle taban sınıf yöntemlerini geçersiz kılarak kendi anahtarlarınızı tanımlayabilirsiniz. Geliştirici tanımlı anahtarlar oluşturma hakkında daha <xref:System.Diagnostics.Switch> fazla bilgi için .NET Framework başvurusundasınıfa bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İz Dinleyicileri](trace-listeners.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
