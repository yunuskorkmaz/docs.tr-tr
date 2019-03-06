---
title: Yöntem ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7969c0a3f5f828f1a1c0d4f33b82881130c6e15
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370169"
---
# <a name="method-etw-events"></a>Yöntem ETW Olayları

<a name="top"></a> Bu olaylar yöntemlere özel bilgiler toplayın. Bu olayların yükünü sembol çözümlemesi için gereklidir. Ayrıca, bu olayların sayısı gibi yararlı bilgileri bir yöntemi çağrıldı sağlar.

Tüm yöntemi olayları "Bilgilendirici (4)" düzeyine sahip. Tüm yöntemi ayrıntılı olayları "Ayrıntılı (5)" düzeyine sahip.

Tarafından tetiklenen tüm yöntemi olayları `JITKeyword` (0x10) anahtar sözcüğü veya `NGenKeyword` çalışma zamanı sağlayıcısı altında (0x20) anahtar sözcüğü veya `JitRundownKeyword` (0x10) veya `NGENRundownKeyword` (0x20) Özet sağlayıcı altında.

CLR yöntemini olayları daha aşağıdaki alt bölümlere:

- [CLR yöntem olayları](#clr_method_events)

- [CLR yöntemini işaret olayları](#clr_method_marker_events)

- [CLR yöntemini ayrıntılı olayları](#clr_method_verbose_events)

- [MethodJittingStarted olay](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a>CLR yöntem olayları

Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)

|Olayı için anahtar sözcüğü|Düzey|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`NGenKeyword` (0x20) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`JitRundownKeyword` Özet sağlayıcısı (0x10)|Bilgilendirici (4)|
|`NGENRundownKeyword` Özet sağlayıcısı (0x20)|Bilgilendirici (4)|

Aşağıdaki tabloda, olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Bir yöntem olduğunda ortaya yeni yüklenen zamanında (JIT yüklenen) ya da NGEN resmi yüklendikten. Dinamik ve genel yöntemler bu sürümü yöntemi yükler için kullanmayın. JIT Yardımcıları hiçbir zaman bu sürümü kullanın.|
|`MethodUnLoad_V1`|137|Bir modül kaldırılır ya da bir uygulama etki alanı edildiğinde oluşturulur. Dinamik yöntemler, bu sürümü için yöntemi bellekten hiçbir zaman kullanın.|
|`MethodDCStart_V1`|137|Başlangıç özeti sırasında yöntemlerini numaralandırır.|
|`MethodDCEnd_V1`|138|Bir Özet sonu sırasında yöntemlerini numaralandırır.|

Aşağıdaki tabloda, olay verilerini gösterir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|MethodID|Kazanma: UInt64|Bir yöntem benzersiz tanımlayıcısı. JIT yardımcı yöntemler için bu yöntem için başlangıç adresi ayarlanır.|
|Modül kimliği|Kazanma: UInt64|Bu yöntem (0 için JIT Yardımcıları) ait olduğu modül tanıtıcısı.|
|MethodStartAddress|Kazanma: UInt64|Başlangıç adresi yöntemi.|
|MethodSize|Kazanma: UInt32|Yönteminin boyutu.|
|MethodToken|Kazanma: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|
|MethodFlags|Kazanma: UInt32|0x1: Dinamik yöntem.<br /><br /> 0x2: Genel yöntem.<br /><br /> 0x4: JIT olarak derlenmiş kod yöntemi (Aksi NGEN yerel görüntü kodu).<br /><br /> 0x8: Yardımcı yöntemi.|
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|

[Başa dön](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a>CLR yöntemini işaret olayları

Bu olaylar yalnızca Özet sağlayıcı altında üretilir. Bunlar yöntemi numaralandırma bir başlangıç sırasında sonunu belirtmek veya özeti bitmelidir. (Diğer bir deyişle, bunlar yükseltilir, `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, veya `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü etkindir.)

Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.

|Olayı için anahtar sözcüğü|Düzey|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword` Özet sağlayıcısı (0x800)|Bilgilendirici (4)|
|`JitRundownKeyword` Özet sağlayıcısı (0x10)|Bilgilendirici (4)|
|`NGENRundownKeyword` Özet sağlayıcısı (0x20)|Bilgilendirici (4)|

Aşağıdaki tabloda, olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Numaralandırma sırasında bir başlangıç özeti başlamadan önce gönderilir.|
|`DCStartComplete_V1`|145|Numaralandırma sırasında bir başlangıç özeti sonunda gönderilir.|
|`DCEndInit_V1`|148|Özet sonu sırasında numaralandırma başlamadan önce gönderilir.|
|`DCEndComplete_V1`|146|Numaralandırma sırasında bir Özet sonu sonunda gönderilir.|

Aşağıdaki tabloda, olay verilerini gösterir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|

[Başa dön](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a>CLR yöntemini ayrıntılı olayları

Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.

|Olayı için anahtar sözcüğü|Düzey|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) çalışma zamanı sağlayıcısı|Ayrıntılı (5)|
|`NGenKeyword` (0x20) çalışma zamanı sağlayıcısı|Ayrıntılı (5)|
|`JitRundownKeyword` Özet sağlayıcısı (0x10)|Ayrıntılı (5)|
|`NGENRundownKeyword` Özet sağlayıcısı (0x20)|Ayrıntılı (5)|

Aşağıdaki tabloda, olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Bir yöntem JIT yüklü olduğunda veya bir NGEN resmi yüklendikten oluşturulur. Dinamik ve genel yöntemler bu sürümü yöntemi yükler için her zaman kullanın. JIT Yardımcıları her zaman bu sürümü kullanın.|
|`MethodUnLoadVerbose_V1`|144|Dinamik bir yöntem yok, modül kaldırılır veya uygulama etki alanı edildiğinde oluşturulur. Dinamik yöntemler, her zaman bu sürümü için yöntemi bellekten kullanın.|
|`MethodDCStartVerbose_V1`|141|Başlangıç özeti sırasında yöntemlerini numaralandırır.|
|`MethodDCEndVerbose_V1`|142|Bir Özet sonu sırasında yöntemlerini numaralandırır.|

Aşağıdaki tabloda, olay verilerini gösterir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|MethodID|Kazanma: UInt64|Yöntem benzersiz tanımlayıcısı. JIT yardımcı yöntemler için yöntem için başlangıç adresi ayarlayın.|
|Modül kimliği|Kazanma: UInt64|Bu yöntem (0 için JIT Yardımcıları) ait olduğu modül tanıtıcısı.|
|MethodStartAddress|Kazanma: UInt64|Başlangıç adresi.|
|MethodSize|Kazanma: UInt32|Yöntem uzunluğu.|
|MethodToken|Kazanma: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|
|MethodFlags|Kazanma: UInt32|0x1: Dinamik yöntem.<br /><br /> 0x2: Genel yöntem.<br /><br /> 0x4: (Aksi takdirde, NGen.exe ile oluşturulan) JIT olarak derlenmiş yöntemi<br /><br /> 0x8: Yardımcı yöntemi.|
|MethodNameSpace|Kazanma: UnicodeString|Yöntemiyle ilişkili tam ad alanı adı.|
|methodName|Kazanma: UnicodeString|Yöntemiyle ilişkili tam sınıf adı.|
|MethodSignature|Kazanma: UnicodeString|(Virgülle ayrılmış listesi tür adları) metodun imzası.|
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|

[Başa dön](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a>MethodJittingStarted olay

Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.

|Olayı için anahtar sözcüğü|Düzey|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) çalışma zamanı sağlayıcısı|Ayrıntılı (5)|
|`NGenKeyword` (0x20) çalışma zamanı sağlayıcısı|Ayrıntılı (5)|
|`JitRundownKeyword` Özet sağlayıcısı (0x10)|Ayrıntılı (5)|
|`NGENRundownKeyword` Özet sağlayıcısı (0x20)|Ayrıntılı (5)|

Aşağıdaki tabloda, olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|JIT olarak derlenmiş bir yöntem olduğunda oluşturulur.|

Aşağıdaki tabloda, olay verilerini gösterir.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|MethodID|Kazanma: UInt64|Yöntem benzersiz tanımlayıcısı.|
|Modül kimliği|Kazanma: UInt64|Bu yöntemin ait olduğu için modül tanıtıcısı.|
|MethodToken|Kazanma: UInt32|dinamik yöntemleri ve JIT Yardımcıları için 0.|
|MethodILSize|Kazanma: UInt32|JIT-derlenmiş yöntem için Microsoft Ara dilini (MSIL) boyutu.|
|MethodNameSpace|Kazanma: UnicodeString|Yöntemiyle ilişkili tam sınıf adı.|
|methodName|Kazanma: UnicodeString|Yöntemin adı.|
|MethodSignature|Kazanma: UnicodeString|(Virgülle ayrılmış listesi tür adları) metodun imzası.|
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
