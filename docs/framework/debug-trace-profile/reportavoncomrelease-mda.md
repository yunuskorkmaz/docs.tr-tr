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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b03b4f3f8c5b6e3e86903a240259ddf2fbf5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
`reportAvOnComRelease` Yönetilen hata ayıklama Yardımcısı (MDA) kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle özel durum oluştuğunda etkinleştirilirse <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi birleştirilmiş ham COM aramaları.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri ve Bellek Bozulması.  
  
## <a name="cause"></a>Sebep  
 Bazen, kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle bir özel durum <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi birleştirilmiş ham COM aramaları. Bunu yapmazsanız bir erişim ihlali CLR neden olacağından normalde, bu özel durum atılır getiren. Bu yardımcı etkinleştirildiğinde, bu tür özel durumlar algıladı ve yalnızca atılmadan yerine bildirdi.  
  
## <a name="resolution"></a>Çözüm  
 Başvuru sayım kodu ve hatalarını arayın yanı sıra nesnenizin başvuru sayım hataları için yerel istemcilerde inceleniyor inceleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 İki mod kullanılabilir. Varsa `allowAv` özniteliği `true`, erişim ihlali atılıyor çalışma zamanı Yardımcısı engeller. Varsa `allowAv` olan `false`, varsayılan, erişim ihlali çalışma zamanı atar, ancak bir uyarı iletisi bir özel durum oluşturulur ve atılan gerektiğini belirtmek için kullanıcıya bildirilir.  
  
## <a name="output"></a>Çıkış  
 Mümkünse, çıktı COM arabirimi işaretçinin özgün vtable içerir. Aksi halde, bir bilgilendirme iletisi görüntülenir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
