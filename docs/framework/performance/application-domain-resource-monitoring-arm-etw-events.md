---
title: "Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
<a name="top"></a>Bu olaylar uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi sağlayın. Bu olaylar kullanın ya da aynı bilgileri elde etmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [ThreadCreated olayı](#threadcreated_event)  
  
-   [AppDomainMemAllocated olayı](#appdomainmemallocated_event)  
  
-   [AppDomainMemSurvived olayı](#appdomainmemsurvived_event)  
  
-   [ThreadAppDomainEnter olayı](#threadappdomainenter_event)  
  
-   [ThreadTerminated olayı](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated olayı  
 Bu olay ayrıca özeti sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü). Bu kategorideki özeti sağlayıcısı altında tetiklenir yalnızca olay budur.  
  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Uygulama etki alanı için bir iş parçacığı oluşturuldu.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Win: UInt64|Oluşturulan iş parçacığı kimliği.|  
|AppDomainID|Win: UInt64|Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.|  
|Bayraklar|Win: UInt32|İş parçacığı oluşturma bayrakları.|  
|ManagedThreadIndex|Win: UInt32|Dizini oluşturulan iş parçacığının yönetilen.|  
|OSThreadId|Win: UInt32|Oluşturulan iş parçacığı kimliği işletim sistemi.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Her 4 MB bellek (yaklaşık) uygulama etki alanında tahsis edilir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Kaynak kullanım bildirilen uygulama etki alanı tanımlayıcısı.|  
|Ayrılmış|Win: UInt64|Toplam uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış bayt sayısı (boşaltılmış bellek miktarını değil çıkarılır).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Her çöp toplama sona erdi.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Kaynak kullanım bildirilen etki alanı tanımlayıcısı.|  
|Derdi bitti|Win: UInt64|Sonra son koleksiyon derdi bitti ve bu uygulama etki alanı tarafından tutulması için bilinen bayt sayısı. Bu sayı doğru ve eksiksiz sonra tam bir koleksiyon, ancak sonra kısa ömürlü bir koleksiyonu eksik olabilir.|  
|ProcessSurvived|Win: UInt64|Son koleksiyondan derdi bitti toplam bayt sayısı. Sonra tam bir koleksiyon, bu numara temsil bayt sayısı Yönetilen yığın Canlı tutuldu. Kısa ömürlü bir koleksiyon sonra bu sayı temsil bayt sayısı kısa ömürlü kuşakta Canlı tutulan.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Bir iş parçacığı uygulama etki alanı girer.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Win: UInt64|İş parçacığı tanımlayıcısı.|  
|AppDomainID|Win: UInt64|Uygulama etki alanı tanımlayıcısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated olayı  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Bir iş parçacığını sonlandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir:  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Win: UInt64|İş parçacığı tanımlayıcısı.|  
|AppDomainID|Win: UInt64|Uygulama etki alanı tanımlayıcısı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
