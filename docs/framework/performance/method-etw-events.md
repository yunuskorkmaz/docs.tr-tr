---
title: "Yöntem ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea7214e284754b1a2f5c8a7a68f19b1b94e02a13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="method-etw-events"></a>Yöntem ETW Olayları
<a name="top"></a>Bu olaylar yöntemlerine özgüdür bilgi toplayın. Bu olaylar yükü simge çözünürlüğü için gereklidir. Ek olarak, bu olayları bir yöntem çağrıldı sayısı gibi yararlı bilgileri sağlar.  
  
 Tüm yöntem olayları "Bilgilendirici (4)" düzeyine sahip. Tüm yöntemi ayrıntılı olayları "Verbose (5)" düzeyine sahip.  
  
 Tarafından gerçekleştirilen tüm yöntem olayları `JITKeyword` (0x10) anahtar sözcüğü veya `NGenKeyword` çalışma zamanı sağlayıcısı altında (0x20) anahtar sözcüğü veya `JitRundownKeyword` (0x10) veya `NGENRundownKeyword` (0x20) özeti sağlayıcısı altında.  
  
 CLR yöntem olayları daha fazla aşağıdaki alt bölümlere:  
  
-   [CLR yöntem olayları](#clr_method_events)  
  
-   [CLR yöntem işaret olayları](#clr_method_marker_events)  
  
-   [CLR yöntem ayrıntılı olayları](#clr_method_verbose_events)  
  
-   [MethodJittingStarted olayı](#methodjittingstarted_event)  
  
<a name="clr_method_events"></a>   
## <a name="clr-method-events"></a>CLR yöntem olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|  
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|  
|`JitRundownKeyword`(0x10) özeti sağlayıcısı|Bilgilendirici (4)|  
|`NGENRundownKeyword`(0x20) özeti sağlayıcısı|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`MethodLoad_V1`|136|Yeni yüklenen zamanında (JIT yüklenir) olan bir yöntem tetiklenir veya NGEN görüntü yüklenemedi. Dinamik ve genel yöntemler bu sürümü yöntemi yükler için kullanmayın. JIT Yardımcıları hiçbir zaman bu sürümü kullanın.|  
|`MethodUnLoad_V1`|137|Bir modül kaldırılır veya uygulama etki alanı yok tetiklenir. Dinamik yöntemleri, yöntemi bellekten için hiçbir zaman bu sürümü kullanın.|  
|`MethodDCStart_V1`|137|Bir başlangıç özeti sırasında yöntemlerini numaralandırır.|  
|`MethodDCEnd_V1`|138|Son özeti sırasında yöntemlerini numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Bir yöntem benzersiz tanımlayıcısı. JIT yardımcı yöntemler için bu yöntemi başlangıç adresi olarak ayarlanır.|  
|Modül kimliği|Win: UInt64|Bu yöntem (0 JIT Yardımcıları için) ait olduğu modül tanıtıcısı.|  
|MethodStartAddress|Win: UInt64|Başlangıç adresi yöntemi.|  
|MethodSize|Win: UInt32|Yöntem boyutu.|  
|MethodToken|Win: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|  
|MethodFlags|Win: UInt32|0x1: dinamik yöntemi.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JIT derlenmiş kod yöntemi (Aksi NGEN yerel görüntü kodu).<br /><br /> 0x8: yardımcı yöntemi.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="clr_method_marker_events"></a>   
## <a name="clr-method-marker-events"></a>CLR yöntem işaret olayları  
 Bu olaylar yalnızca özeti sağlayıcısı altında oluşturulur. Bunlar yöntemi numaralandırma bir başlangıç sırasında sonu belirtmek veya özeti bitemez. (Diğer bir deyişle, yükseltilmiş zaman `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, veya `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü etkindir.)  
  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementRundownKeyword`(0x800) özeti sağlayıcısı|Bilgilendirici (4)|  
|`JitRundownKeyword`(0x10) özeti sağlayıcısı|Bilgilendirici (4)|  
|`NGENRundownKeyword`(0x20) özeti sağlayıcısı|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklaması|  
|-----------|--------------|----------------|  
|`DCStartInit_V1`|147|Numaralandırma başlangıç özeti sırasında başlamadan önce gönderilir.|  
|`DCStartComplete_V1`|145|Numaralandırma başlangıç özeti sırasında sonunda gönderdi.|  
|`DCEndInit_V1`|148|Numaralandırma sırasında son özeti başlamadan önce gönderilir.|  
|`DCEndComplete_V1`|146|Numaralandırma sırasında son özeti sonunda gönderdi.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="clr_method_verbose_events"></a>   
## <a name="clr-method-verbose-events"></a>CLR yöntem ayrıntılı olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Verbose (5)|  
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Verbose (5)|  
|`JitRundownKeyword`(0x10) özeti sağlayıcısı|Verbose (5)|  
|`NGENRundownKeyword`(0x20) özeti sağlayıcısı|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`MethodLoadVerbose_V1`|143|JIT yüklenen bir yöntemdir veya NGEN görüntü yüklenemedi tetiklenir. Dinamik ve genel yöntemler bu sürümü yöntemi yükler için her zaman kullanın. JIT Yardımcıları her zaman bu sürümü kullanın.|  
|`MethodUnLoadVerbose_V1`|144|Dinamik yöntemi yok, modül kaldırılır ve uygulama etki alanı yok tetiklenir. Dinamik yöntemleri, yöntemi bellekten için her zaman bu sürümü kullanın.|  
|`MethodDCStartVerbose_V1`|141|Bir başlangıç özeti sırasında yöntemlerini numaralandırır.|  
|`MethodDCEndVerbose_V1`|142|Son özeti sırasında yöntemlerini numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Yöntem benzersiz tanımlayıcısı. JIT yardımcı yöntemler için yöntemi başlangıç adresi olarak ayarlayın.|  
|Modül kimliği|Win: UInt64|Bu yöntem (0 JIT Yardımcıları için) ait olduğu modül tanıtıcısı.|  
|MethodStartAddress|Win: UInt64|Başlangıç adresi.|  
|MethodSize|Win: UInt32|Yöntem uzunluğu.|  
|MethodToken|Win: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|  
|MethodFlags|Win: UInt32|0x1: dinamik yöntemi.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JIT derlenmiş yöntemi (Aksi takdirde NGen.exe tarafından oluşturulan)<br /><br /> 0x8: yardımcı yöntemi.|  
|MethodNameSpace|Win: UnicodeString|Yöntemiyle ilişkili tam ad alanı adı.|  
|MethodName|Win: UnicodeString|Yöntemiyle ilişkili tam sınıfı adı.|  
|MethodSignature|Win: UnicodeString|İmza yöntemi (virgülle ayrılmış listesi adlarını yazın).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="methodjittingstarted_event"></a>   
## <a name="methodjittingstarted-event"></a>MethodJittingStarted olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Verbose (5)|  
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Verbose (5)|  
|`JitRundownKeyword`(0x10) özeti sağlayıcısı|Verbose (5)|  
|`NGENRundownKeyword`(0x20) özeti sağlayıcısı|Verbose (5)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`MethodJittingStarted`|145|JIT derlenmiş bir yöntem tetiklenir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|MethodID|Win: UInt64|Yöntem benzersiz tanımlayıcısı.|  
|Modül kimliği|Win: UInt64|Bu yöntemin ait olduğu modül tanıtıcısı.|  
|MethodToken|Win: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|  
|MethodILSize|Win: UInt32|JIT derlenmiş yöntemi için Microsoft Ara dili (MSIL) boyutu.|  
|MethodNameSpace|Win: UnicodeString|Yöntemiyle ilişkili tam sınıfı adı.|  
|MethodName|Win: UnicodeString|Yöntemin adı.|  
|MethodSignature|Win: UnicodeString|İmza yöntemi (virgülle ayrılmış listesi adlarını yazın).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
