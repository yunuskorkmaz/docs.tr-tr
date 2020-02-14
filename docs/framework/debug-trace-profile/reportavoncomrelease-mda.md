---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217217"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
`reportAvOnComRelease` yönetilen hata ayıklama Yardımcısı (MDA), COM birlikte çalışma gerçekleştirirken ve ham COM çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri ve bellek bozulması.  
  
## <a name="cause"></a>Nedeni  
 Bazen, COM birlikte çalışma gerçekleştirirken ve ham COM çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> ya da <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle bir özel durum oluşturulur. Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor. Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.  
  
## <a name="resolution"></a>Çözüm  
 Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 İki mod kullanılabilir. `allowAv` özniteliği `true`, yardımcı çalışma zamanının erişim ihlalini almasını engeller. Varsayılan değer olan `allowAv` `false`, çalışma zamanı erişim ihlalini atar, ancak bir özel durumun oluşturulduğunu ve atıldığını göstermek için kullanıcıya bir uyarı iletisi bildirilir.  
  
## <a name="output"></a>Çıktı  
 Mümkünse, çıkış COM arabirimi işaretçisinin orijinal vtable 'sini içerir. Aksi takdirde, bir bilgi iletisi görüntülenir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
