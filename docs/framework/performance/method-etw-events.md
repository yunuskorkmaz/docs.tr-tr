---
title: Yöntem ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58249a0e080e045223bdaf170f2eaedb67fc0dea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046382"
---
# <a name="method-etw-events"></a>Yöntem ETW Olayları

<a name="top"></a>Bu olaylar yöntemlere özgü bilgiler toplar. Bu olayların yükü sembol çözümlemesi için gereklidir. Ayrıca, bu olaylar yöntemin kaç kez çağrıldığı gibi yararlı bilgiler sağlar.

Tüm Yöntem olayları "bilgilendirme (4)" düzeyine sahiptir. Tüm Yöntem ayrıntılı olayları "verbose (5)" düzeyine sahiptir.

Tüm `JITKeyword` Yöntem olayları, (0x10) anahtar sözcüğü `NGenKeyword` veya çalışma zamanı sağlayıcısı `JitRundownKeyword` altındaki (0x20) anahtar sözcüğü veya (0x10) ya `NGENRundownKeyword` da (0x20) özet sağlayıcısının altında oluşturulur.

CLR yöntemi olayları aşağıda verilmiştir:

- [CLR yöntemi olayları](#clr_method_events)

- [CLR Yöntem Işaretleyici olayları](#clr_method_marker_events)

- [CLR metodu ayrıntılı olayları](#clr_method_verbose_events)

- [Methodjtingstarted olayı](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a>CLR yöntemi olayları

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir. (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`JitRundownKeyword`(0x10) Özeti sağlayıcı|Bilgilendirici (4)|
|`NGENRundownKeyword`(0x20) Özeti sağlayıcı|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Bir yöntem yüklendiğinde (JıT-yüklü) veya bir NGEN görüntüsünün yüklendiği zaman tetiklenir. Dinamik ve genel yöntemler bu sürümü Yöntem yüklemeleri için kullanmaz. JıT yardımcıları bu sürümü hiçbir şekilde kullanmaz.|
|`MethodUnLoad_V1`|137|Bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler bu sürümü Yöntem kaldırmalar için hiçbir şekilde kullanmaz.|
|`MethodDCStart_V1`|137|Başlangıç özeti sırasında yöntemleri numaralandırır.|
|`MethodDCEnd_V1`|138|Son Özeti sırasında yöntemleri numaralandırır.|

Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Methoddıd|Win: UInt64|Metodun benzersiz tanımlayıcısı. JıT yardımcı yöntemleri için bu, yönteminin başlangıç adresine ayarlanır.|
|Modül kimliği|Win: UInt64|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|MethodStartAddress|Win: UInt64|Metodun başlangıç adresi.|
|MethodSize|Win: UInt32|Metodun boyutu.|
|MethodToken|Win: UInt32|dinamik yöntemler ve JıT yardımcıları için 0.|
|MethodFlags|Win: UInt32|0x1 Dinamik yöntem.<br /><br /> 0x2 Genel yöntem.<br /><br /> 4, JıT derlenmiş kod yöntemi (Aksi takdirde NGEN yerel görüntü kodu).<br /><br /> 0x8 Yardımcı yöntemi.|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

[Başa dön](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a>CLR Yöntem Işaretleyici olayları

Bu olaylar yalnızca Özet sağlayıcının altında oluşturulur. Bir başlangıç veya bitiş Özeti sırasında Yöntem numaralandırması sonunu işaret eder. (Yani `NGENRundownKeyword`,,, veya `JitRundownKeyword` `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü etkinleştirildiğinde tetiklenir `LoaderRundownKeyword`.)

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword`(0x800) runaşağı sağlayıcı|Bilgilendirici (4)|
|`JitRundownKeyword`(0x10) Özeti sağlayıcı|Bilgilendirici (4)|
|`NGENRundownKeyword`(0x20) Özeti sağlayıcı|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Başlangıç özeti sırasında numaralandırmanın başlangıcından önce gönderilir.|
|`DCStartComplete_V1`|145|Bir başlangıç Özeti sırasında numaralandırmanın sonuna gönderilir.|
|`DCEndInit_V1`|148|Son Özeti sırasında numaralandırmanın başlangıcından önce gönderilir.|
|`DCEndComplete_V1`|146|Son Özeti sırasında numaralandırmanın sonuna gönderilir.|

Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

[Başa dön](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a>CLR metodu ayrıntılı olayları

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Verbose (5)|
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Verbose (5)|
|`JitRundownKeyword`(0x10) Özeti sağlayıcı|Verbose (5)|
|`NGENRundownKeyword`(0x20) Özeti sağlayıcı|Verbose (5)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Bir yöntem JıT olarak yüklendiğinde veya bir NGEN görüntüsü yüklendiğinde tetiklenir. Dinamik ve genel yöntemler her zaman Yöntem yüklemeleri için bu sürümü kullanır. JıT yardımcıları her zaman bu sürümü kullanır.|
|`MethodUnLoadVerbose_V1`|144|Dinamik bir yöntem yok edildiğinde, bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler her zaman bu sürümü Yöntem kaldırmalar için kullanır.|
|`MethodDCStartVerbose_V1`|141|Başlangıç özeti sırasında yöntemleri numaralandırır.|
|`MethodDCEndVerbose_V1`|142|Son Özeti sırasında yöntemleri numaralandırır.|

Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Methoddıd|Win: UInt64|Metodun benzersiz tanıtıcısı. JıT yardımcı yöntemleri için, yönteminin başlangıç adresine ayarlanır.|
|Modül kimliği|Win: UInt64|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|MethodStartAddress|Win: UInt64|Başlangıç adresi.|
|MethodSize|Win: UInt32|Yöntem uzunluğu.|
|MethodToken|Win: UInt32|dinamik yöntemler ve JıT yardımcıları için 0.|
|MethodFlags|Win: UInt32|0x1 Dinamik yöntem.<br /><br /> 0x2 Genel yöntem.<br /><br /> 4, JıT derlenmiş yöntemi (Aksi takdirde, NGen. exe tarafından oluşturulur)<br /><br /> 0x8 Yardımcı yöntemi.|
|MethodNameSpace|Win: UnicodeString|Yöntemiyle ilişkili tam ad alanı adı.|
|MethodName|Win: UnicodeString|Yöntemiyle ilişkili tam sınıf adı.|
|MethodSignature|Win: UnicodeString|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

[Başa dön](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a>Methodjtingstarted olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`JITKeyword`(0x10) çalışma zamanı sağlayıcısı|Verbose (5)|
|`NGenKeyword`(0x20) çalışma zamanı sağlayıcısı|Verbose (5)|
|`JitRundownKeyword`(0x10) Özeti sağlayıcı|Verbose (5)|
|`NGENRundownKeyword`(0x20) Özeti sağlayıcı|Verbose (5)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Bir yöntem JıT olarak derlendiğinde tetiklenir.|

Aşağıdaki tabloda olay verileri gösterilmektedir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Methoddıd|Win: UInt64|Metodun benzersiz tanıtıcısı.|
|Modül kimliği|Win: UInt64|Bu yöntemin ait olduğu modülün tanımlayıcısı.|
|MethodToken|Win: UInt32|dinamik yöntemler ve JıT yardımcıları için 0.|
|Methoddilsize|Win: UInt32|JıT olarak derlenen metodun Microsoft ara dili (MSIL) boyutu.|
|MethodNameSpace|Win: UnicodeString|Yöntemiyle ilişkili tam sınıf adı.|
|MethodName|Win: UnicodeString|Metodun adı.|
|MethodSignature|Win: UnicodeString|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
