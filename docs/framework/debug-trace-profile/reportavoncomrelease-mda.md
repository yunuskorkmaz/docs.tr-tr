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
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052322"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
Yönetilen `reportAvOnComRelease` hata ayıklama Yardımcısı (MDA), com birlikte çalışma gerçekleştirirken ve ham com çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri ve bellek bozulması.  
  
## <a name="cause"></a>Sebep  
 Bazen, com birlikte çalışma gerçekleştirirken ve ham com çağrılarıyla birleştirilmiş <xref:System.Runtime.InteropServices.Marshal.Release%2A> veya <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> yöntemi kullanılarak Kullanıcı başvuruları saymasına neden olan bir özel durum oluşturulur. Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor. Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.  
  
## <a name="resolution"></a>Çözüm  
 Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 İki mod kullanılabilir. `allowAv` Özniteliği ise`true`, yardımcı çalışma zamanının erişim ihlaline engel olmasını önler. `allowAv` Varsayılanolanise,çalışmazamanıerişimihlaliniatar,ancakbirözeldurumunoluşturulduğunuveatıldığınıgöstermekiçinkullanıcıya`false`bir uyarı iletisi bildirilir.  
  
## <a name="output"></a>Çıkış  
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
