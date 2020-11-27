---
title: reportAvOnComRelease MDA
description: .NET 'teki erişim ihlalleri ve bellek bozulması nedeniyle etkinleştirilebilecek reportAvOnComRelease Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: c5047aa4005cdaa9ae6aabe8dcd7ee838ee13f58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267123"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA

`reportAvOnComRelease`Yönetilen hata ayıklama Yardımcısı (MDA), com birlikte çalışma gerçekleştirirken ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ham com çağrılarıyla birleştirilmiş veya yöntemi kullanılarak kullanıcı başvurusu sayma hataları nedeniyle özel durumlar oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  

 Erişim ihlalleri ve bellek bozulması.  
  
## <a name="cause"></a>Nedeni  

 Bazen, COM birlikte çalışma gerçekleştirirken ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ham com çağrılarıyla birleştirilmiş veya yöntemi kullanılarak Kullanıcı başvuruları saymasına neden olan bir özel durum oluşturulur. Normalde bu özel durum atılır çünkü bu durum, CLR 'de bir erişim ihlaline neden olur ve bunu aşağı doğru hale getiriyor. Bu yardımcı etkin olduğunda, bu tür özel durumlar algılanmak yerine tespit edilebilir ve bildirilebilir.  
  
## <a name="resolution"></a>Çözüm  

 Başvuru sayma kodunuzu inceleyin ve hata sayma hataları için nesnenizin yerel istemcilerini inceleyerek hata sayısını araştırın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 İki mod kullanılabilir. `allowAv`Özniteliği ise `true` , yardımcı çalışma zamanının erişim ihlaline engel olmasını önler. Varsayılan olan ise, `allowAv` `false` çalışma zamanı erişim ihlalini atar, ancak bir özel durumun oluşturulduğunu ve atıldığını göstermek için kullanıcıya bir uyarı iletisi bildirilir.  
  
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
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
