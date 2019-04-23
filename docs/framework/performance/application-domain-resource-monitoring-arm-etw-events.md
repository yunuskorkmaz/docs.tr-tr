---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133828"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
<a name="top"></a> Bu olayları, uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgileri sağlar. Bu olayları kullanan ya da aynı bilgileri edinmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.  
  
 Bu kategori aşağıdaki olaylar oluşur:  
  
-   [ThreadCreated olay](#threadcreated_event)  
  
-   [AppDomainMemAllocated olay](#appdomainmemallocated_event)  
  
-   [AppDomainMemSurvived olay](#appdomainmemsurvived_event)  
  
-   [ThreadAppDomainEnter olay](#threadappdomainenter_event)  
  
-   [ThreadTerminated olay](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated olay  
 Bu olay Özet sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü). Bu kategorideki Özet sağlayıcı altında oluşturulur yalnızca olay budur.  
  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Uygulama etki alanı için bir iş parçacığı oluşturulur.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Kazanma: UInt64|Oluşturulan iş parçacığının kimliği.|  
|AppDomainID|Kazanma: UInt64|Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.|  
|Bayraklar|Kazanma: UInt32|İş parçacığı oluşturma bayrakları.|  
|ManagedThreadIndex|Kazanma: UInt32|Dizini oluşturulan iş parçacığının yönetilen.|  
|OSThreadId|Kazanma: UInt32|Oluşturulan iş parçacığının kimliği işletim sistemi.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Her 4 MB bellek, uygulama etki alanında (yaklaşık) ayrılır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Kazanma: UInt64|Kaynak kullanımı bildirilen uygulama etki alanı tanımlayıcısı.|  
|ayrılmış|Kazanma: UInt64|Uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış baytların toplam sayısı (boşaltılmış bellek miktarı değil çıkarılır).|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Her çöp toplama sona erdi.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Kazanma: UInt64|Kullanım raporlama için hangi kaynak etki alanı tanımlayıcısı.|  
|Kurtulan|Kazanma: UInt64|Sonra son toplamadan kurtulan ve bu uygulama etki alanına göre tutulması için bilinen bayt sayısı. Bu sayı, sonra tam bir koleksiyon doğru ve eksiksiz olması, ancak kısa ömürlü bir toplamanın ardından tamamlanmamış olabilir.|  
|ProcessSurvived|Kazanma: UInt64|Son derlemeden kurtulan toplam bayt sayısı. Tam bir koleksiyon sonra bu numara temsil bayt sayısı, yönetilen yığınlar Canlı tutulmakta. Kısa ömürlü bir toplamanın ardından bu numara temsil bayt sayısı kısa ömürlü nesillerde Canlı tutulan.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Bir iş parçacığı, bir uygulama etki alanı girer.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Kazanma: UInt64|İş parçacığı tanımlayıcısı.|  
|AppDomainID|Kazanma: UInt64|Uygulama etki alanı tanımlayıcısı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated olay  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Düzey|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Ne zaman gerçekleşti|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Bir iş parçacığı sonlanır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir:  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ThreadID|Kazanma: UInt64|İş parçacığı tanımlayıcısı.|  
|AppDomainID|Kazanma: UInt64|Uygulama etki alanı tanımlayıcısı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
