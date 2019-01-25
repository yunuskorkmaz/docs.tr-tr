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
ms.openlocfilehash: c70c70f251fca9312019d4c63304e8354bf87fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729164"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
`reportAvOnComRelease` Yönetilen hata ayıklama Yardımcısı (MDA) kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle özel durumlar oluşturulduğunda etkinleştirilir <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi ham COM çağrıları ile birlikte.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri ve Bellek Bozulması.  
  
## <a name="cause"></a>Sebep  
 Bazen, kullanıcı başvuru sayım hataları COM birlikte çalışma ve kullanarak gerçekleştirilirken nedeniyle bir özel durum <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi ham COM çağrıları ile birlikte. Normalde, bunu bir erişim ihlali CLR'de neden olacağından bu özel durum atılır yükseltilebildiği. Bu yardımcı etkinleştirildiğinde, bu tür özel durumların algıladı ve yalnızca atılmadan yerine bildirdi.  
  
## <a name="resolution"></a>Çözüm  
 Başvuru sayım kod ve hataları Ara hem de nesne başvuru sayım hataları için yerel istemcileri İnceleme inceleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 İki modu kullanılabilir. Varsa `allowAv` özniteliği `true`, erişim ihlali atılıyor gelen çalışma zamanı Yardımcısı engeller. Varsa `allowAv` olduğu `false`, varsayılan değer olan, çalışma zamanı erişim ihlali atar, ancak bir özel durum ve atılan gerektiğini belirtmek için kullanıcıya bir uyarı iletisi bildirilir.  
  
## <a name="output"></a>Çıkış  
 Mümkünse, COM arabirimi işaretçisini kişinin orijinal vtable çıkış içerir. Aksi halde bir bilgi iletisi görüntülenir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
