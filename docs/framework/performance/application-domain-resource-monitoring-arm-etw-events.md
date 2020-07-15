---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
description: .NET 'te ThreadCreated, Appdomainmemalkonumlandırılan, Appdomainmemsurvi, ve daha fazlası gibi uygulama etki alanı kaynak izleme (ARM) ETW olayları hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309787"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları

Bu olaylar, bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgileri sağlar. Aynı bilgileri elde etmek için bu olayları kullanabilir veya uygulama etki alanı kaynak izleme (ARM) özelliğini kullanabilirsiniz.

## <a name="threadcreated-event"></a>ThreadCreated olayı

Bu olay Ayrıca, Özet sağlayıcının altında `ThreadDC` (anahtar sözcüğünün altında) de oluşturulur `AppDomainResourceManagementRundownKeyword` . Bu, bu kategorideki özet sağlayıcı altında oluşturulan tek olaydır.

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword`0x800|Bilgilendirici (4)|
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ThreadCreated`|85|Uygulama etki alanı için bir iş parçacığı oluşturuldu.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|ThreadID|Win: UInt64|Oluşturulan iş parçacığının KIMLIĞI.|
|AppDomainID|Win: UInt64|İş parçacığı etkinliğinin bildirildiği uygulama etki alanının tanımlayıcısı.|
|Bayraklar|Win: UInt32|İş parçacığı oluşturma bayrakları.|
|Managedthreadındex|Win: UInt32|Oluşturulan iş parçacığının yönetilen dizini.|
|OSThreadId|Win: UInt32|Oluşturulan iş parçacığının işletim sistemi KIMLIĞI.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="appdomainmemallocated-event"></a>Appdomainmemalbulunan olay

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword`0x800|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|83|Uygulama etki alanında her 4 MB bellek (yaklaşık olarak) ayrılır.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|AppDomainID|Win: UInt64|Kaynak kullanımının bildirildiği uygulama etki alanının tanımlayıcısı.|
|Ayrılabilir|Win: UInt64|Uygulama etki alanı oluşturulduğundan bu yana bu uygulama etki alanında ayrılan toplam bayt sayısı (serbest bırakılan bellek miktarı çıkarıldı).|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="appdomainmemsurvived-event"></a>Appdomainmemsurvilenmiş olay

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword`0x800|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|84|Her çöp toplama işlemi sona erdi.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|AppDomainID|Win: UInt64|Kaynak kullanımının bildirildiği etki alanının tanımlayıcısı.|
|Kalan|Win: UInt64|Son koleksiyondan sonra kalan ve bu uygulama etki alanı tarafından tutulması bilinen bayt sayısı. Bu sayı doğru ve tam bir koleksiyon sonrasında tamamlanır, ancak kısa ömürlü bir koleksiyon sonrasında tamamlanmamış olabilir.|
|Processsurviks|Win: UInt64|Son koleksiyondan kalan toplam bayt sayısı. Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki etkin tutulan bayt sayısını temsil eder. Kısa ömürlü bir koleksiyondan sonra bu sayı, kısa ömürlü neslerde bulunan baytların sayısını temsil eder.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword`0x800|Bilgilendirici (4)|
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|87|Bir iş parçacığı bir uygulama etki alanı girer.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|ThreadID|Win: UInt64|İş parçacığı tanımlayıcısı.|
|AppDomainID|Win: UInt64|Uygulama etki alanı tanımlayıcısı.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="threadterminated-event"></a>Threadsonlandırılmış olay

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword`0x800|Bilgilendirici (4)|
|`ThreadingKeyword`(0x10000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ThreadTerminated`|86|Bir iş parçacığı sonlanır.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|ThreadID|Win: UInt64|İş parçacığı tanımlayıcısı.|
|AppDomainID|Win: UInt64|Uygulama etki alanı tanımlayıcısı.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
