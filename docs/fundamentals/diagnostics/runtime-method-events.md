---
title: Yöntem çalışma zamanı olayları
description: CLR yöntemi olayları, CLR Yöntem işaretleyicisi veya CLR yöntemi ayrıntılı olayları ve Methodjtingstarted gibi yöntemlere özgü tanılama bilgilerini toplamak için .NET çalışma zamanı olayları ' na bakın.
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589990"
---
# <a name="net-runtime-method-events"></a>.NET çalışma zamanı yöntemi olayları

Bu olaylar yöntemlere özgü bilgiler toplar. Bu olayların yükü sembol çözümlemesi için gereklidir. Ayrıca, bu olaylar, yüklenmiş ve kaldırılmış Yöntemler gibi yararlı bilgiler sağlar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

Tüm Yöntem olayları "bilgilendirme (4)" düzeyine sahiptir. Tüm Yöntem ayrıntılı olayları "verbose (5)" düzeyine sahiptir.

Tüm Yöntem olayları, `JITKeyword` (0x10) anahtar sözcüğü veya `NGenKeyword` çalışma zamanı sağlayıcısı altındaki (0x20) anahtar sözcüğü veya ( `JitRundownKeyword` 0x10) ya da ( `NGENRundownKeyword` 0x20) özet sağlayıcısının altında oluşturulur.

Bu olayların v2 sürümleri, reJitId 'yi içerir, v1 sürümleri desteklemez.

## <a name="methodload_v1-event"></a>MethodLoad_V1 olayı

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|141|Bir yöntem yüklendiğinde (JıT-yüklü) veya bir NGEN görüntüsünün yüklendiği zaman tetiklenir. Dinamik ve genel yöntemler bu sürümü Yöntem yüklemeleri için kullanmaz. JıT yardımcıları bu sürümü hiçbir şekilde kullanmaz.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`NGenKeyword` (0x20) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanımlayıcısı. JıT yardımcı yöntemleri için bu, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Metodun başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Metodun boyutu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş kod yöntemi (Aksi takdirde NGEN yerel görüntü kodu).<br /><br /> 0x8: yardımcı yöntemi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodload_v2-event"></a>MethodLoad_V2 olayı

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|141|Bir yöntem yüklendiğinde (JıT-yüklü) veya bir NGEN görüntüsünün yüklendiği zaman tetiklenir. Dinamik ve genel yöntemler bu sürümü Yöntem yüklemeleri için kullanmaz. JıT yardımcıları bu sürümü hiçbir şekilde kullanmaz.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|
|`NGenKeyword` (0x20) çalışma zamanı sağlayıcısı|Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanımlayıcısı. JıT yardımcı yöntemleri için bu, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Metodun başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Metodun boyutu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş kod yöntemi (Aksi takdirde NGEN yerel görüntü kodu).<br /><br /> 0x8: yardımcı yöntemi.|
|`ReJITID`|`win:UInt64`|Metodun ReJIT KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodunload_v1-event"></a>MethodUnLoad_V1 olayı

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|142|Bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler bu sürümü Yöntem kaldırmalar için hiçbir şekilde kullanmaz.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10|Bilgilendirici (4)|
|`NGenKeyword` 0x20|Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanımlayıcısı. JıT yardımcı yöntemleri için bu, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Metodun başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Metodun boyutu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş kod yöntemi (Aksi takdirde NGEN yerel görüntü kodu).<br /><br /> 0x8: yardımcı yöntemi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodunload_v2-event"></a>MethodUnLoad_V2 olayı

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|142|Bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler bu sürümü Yöntem kaldırmalar için hiçbir şekilde kullanmaz.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10|Bilgilendirici (4)|
|`NGenKeyword` 0x20|Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanımlayıcısı. JıT yardımcı yöntemleri için bu, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Metodun başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Metodun boyutu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş kod yöntemi (Aksi takdirde NGEN yerel görüntü kodu).<br /><br /> 0x8: yardımcı yöntemi.|
|`ReJITID`|`win:UInt64`|Metodun ReJIT KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="r2rgetentrypoint-event"></a>R2RGetEntryPoint olayı

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|159|Bir R2R giriş noktası araması sona erdiğinde tetiklenir.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Bir R2R yönteminin benzersiz tanıtıcısı.|
|`MethodNamespace`|`win:UnicodeString`|Aranmakta olan metodun ad alanı.|
|`MethodName`|`win:UnicodeString`|Aranmakta olan yöntemin adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`EntryPoint`|`win:UInt64`|R2R yönteminin giriş noktası işaretçisi|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="r2rgetentrypointstart-event"></a>R2RGetEntryPointStart olayı

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|160|Bir R2R giriş noktası araması başladığında tetiklenir.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Bir R2R yönteminin benzersiz tanıtıcısı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodloadverbose_v1-event"></a>MethodLoadVerbose_V1 olayı

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Bir yöntem JıT olarak yüklendiğinde veya bir NGEN görüntüsü yüklendiğinde tetiklenir. Dinamik ve genel yöntemler her zaman Yöntem yüklemeleri için bu sürümü kullanır. JıT yardımcıları her zaman bu sürümü kullanır.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanıtıcısı. JıT yardımcı yöntemleri için, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Yöntem uzunluğu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş Yöntem (Aksi takdirde, NGen.exe tarafından oluşturulur)<br /><br /> 0x8: yardımcı yöntemi.|
|`MethodNameSpace`|`win:UnicodeString`|Yöntemiyle ilişkili tam ad alanı adı.|
|`MethodName`|`win:UnicodeString`|Yöntemiyle ilişkili tam sınıf adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodloadverbose_v2-event"></a>MethodLoadVerbose_V2 olayı

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Bir yöntem JıT olarak yüklendiğinde veya bir NGEN görüntüsü yüklendiğinde tetiklenir. Dinamik ve genel yöntemler her zaman Yöntem yüklemeleri için bu sürümü kullanır. JıT yardımcıları her zaman bu sürümü kullanır.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanıtıcısı. JıT yardımcı yöntemleri için, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Yöntem uzunluğu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş Yöntem (Aksi takdirde, NGen.exe tarafından oluşturulur)<br /><br /> 0x8: yardımcı yöntemi.|
|`MethodNameSpace`|`win:UnicodeString`|Yöntemiyle ilişkili tam ad alanı adı.|
|`MethodName`|`win:UnicodeString`|Yöntemiyle ilişkili tam sınıf adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`ReJITID`|`win:UInt64`|Metodun ReJIT KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodunloadverbose_v1-event"></a>MethodUnLoadVerbose_V1 olayı

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|144|Dinamik bir yöntem yok edildiğinde, bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler her zaman bu sürümü Yöntem kaldırmalar için kullanır.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanıtıcısı. JıT yardımcı yöntemleri için, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Yöntem uzunluğu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş Yöntem (Aksi takdirde, NGen.exe tarafından oluşturulur)<br /><br /> 0x8: yardımcı yöntemi.|
|`MethodNameSpace`|`win:UnicodeString`|Yöntemiyle ilişkili tam ad alanı adı.|
|`MethodName`|`win:UnicodeString`|Yöntemiyle ilişkili tam sınıf adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodunloadverbose_v2-event"></a>MethodUnLoadVerbose_V2 olayı

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|144|Dinamik bir yöntem yok edildiğinde, bir modül kaldırıldığında veya bir uygulama etki alanı yok edildiğinde tetiklenir. Dinamik yöntemler her zaman bu sürümü Yöntem kaldırmalar için kullanır.|

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Bilgilendirici (4)|
|`NGenKeyword` 0x20 |Bilgilendirici (4)|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanıtıcısı. JıT yardımcı yöntemleri için, yönteminin başlangıç adresine ayarlanır.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı (JıT yardımcıları için 0).|
|`MethodStartAddress`|`win:UInt64`|Başlangıç adresi.|
|`MethodSize`|`win:UInt32`|Yöntem uzunluğu.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodFlags`|`win:UInt32`|0x1: dinamik yöntem.<br /><br /> 0x2: genel yöntem.<br /><br /> 0x4: JıT derlenmiş Yöntem (Aksi takdirde, NGen.exe tarafından oluşturulur)<br /><br /> 0x8: yardımcı yöntemi.|
|`MethodNameSpace`|`win:UnicodeString`|Yöntemiyle ilişkili tam ad alanı adı.|
|`MethodName`|`win:UnicodeString`|Yöntemiyle ilişkili tam sınıf adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`ReJITID`|`win:UInt64`|Metodun ReJIT KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodjittingstarted_v1-event"></a>MethodJittingStarted_V1 olayı

Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITKeyword` 0x10 |Verbose (5)|
|`NGenKeyword` 0x20 |Verbose (5)|

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|145|Bir yöntem JıT olarak derlendiğinde tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanıtıcısı.|
|`ModuleID`|`win:UInt64`|Bu yöntemin ait olduğu modülün tanımlayıcısı.|
|`MethodToken`|`win:UInt32`|dinamik yöntemler ve JıT yardımcıları için 0.|
|`MethodILSize`|`win:UInt32`|JıT olarak derlenen metodun ortak ara dil (CıL) boyutu.|
|`MethodNameSpace`|`win:UnicodeString`|Yöntemiyle ilişkili tam sınıf adı.|
|`MethodName`|`win:UnicodeString`|Metodun adı.|
|`MethodSignature`|`win:UnicodeString`|Metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodjitinliningsucceeded-event"></a>Methodjınliningsucceeded olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000) |Verbose (5)|

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|185|Bir yöntem JıT derleyicisi tarafından başarıyla satır içine eklendiğinde tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Derlenmekte olan metodun ad alanı.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Derlenmekte olan yöntemin adı.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Derlenen yöntemin imzası (tür adlarının virgülle ayrılmış listesi).|
|`InlinerNamespace`|`win:UnicodeString`|Inoluşturucu ("Parent") yönteminin ad alanı.|
|`InlinerName`|`win:UnicodeString`|İnoluşturucu ("Parent") metodunun adı.|
|`InlinerNameSignature`|`win:UnicodeString`|İnoluşturucu ("Parent") yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`InlineeNamespace`|`win:UnicodeString`|Inlinee ("Child") yönteminin ad alanı.|
|`InlineeName`|`win:UnicodeString`|Inlinee ("Child") yönteminin adı.|
|`InlineeNameSignature`|`win:UnicodeString`|Inlinee ("Child") yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodjitinliningfailed-event"></a>Methodjınliningfailed olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000) |Verbose (5)|

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|192|Bir yöntemin JıT derleyicisi tarafından satır içine alınmayacak olması başarısız olduğunda tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Derlenmekte olan metodun ad alanı.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Derlenmekte olan yöntemin adı.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Derlenen yöntemin imzası (tür adlarının virgülle ayrılmış listesi).|
|`InlinerNamespace`|`win:UnicodeString`|Inoluşturucu ("Parent") yönteminin ad alanı.|
|`InlinerName`|`win:UnicodeString`|İnoluşturucu ("Parent") metodunun adı.|
|`InlinerNameSignature`|`win:UnicodeString`|İnoluşturucu ("Parent") yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`InlineeNamespace`|`win:UnicodeString`|Inlinee ("Child") yönteminin ad alanı.|
|`InlineeName`|`win:UnicodeString`|Inlinee ("Child") yönteminin adı.|
|`InlineeNameSignature`|`win:UnicodeString`|Inlinee ("Child") yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`FailAlways`|`win:Boolean`|Yöntemin kullanılamaz olarak işaretlenip işaretlenmediğini belirtir.|
|`FailReason`|`win:UnicodeString`|Neden ayrılamadı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodjittailcallsucceeded-event"></a>Methodj, Callsucceeded olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000) |Verbose (5)|

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|192|Bir yöntem başarıyla tail çağrıldığında JıT derleyicisi tarafından tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Derlenmekte olan metodun ad alanı.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Derlenmekte olan yöntemin adı.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Derlenen yöntemin imzası (tür adlarının virgülle ayrılmış listesi).|
|`CallerNamespace`|`win:UnicodeString`|Çağıran yönteminin ad alanı.|
|`CallerName`|`win:UnicodeString`|Arayan yönteminin adı.|
|`CallerNameSignature`|`win:UnicodeString`|Çağıran yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`CalleeNamespace`|`win:UnicodeString`|Çağrılan metodun ad alanı.|
|`CalleeName`|`win:UnicodeString`|Çağrılan yöntemin adı.|
|`CalleeNameSignature`|`win:UnicodeString`|Çağrılan metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`TailPrefix`|`win:Boolean`|Bir kuyruk ön eki yönergesi olup olmadığı.|
|`TailCallType`|`win:UInt32`|Kuyruk çağrısının türü.<br/><br/>0: iyileştirilmiş kuyruk çağrısı (bitiş + JMP)<br/><br/>1: özyinelemeli tail çağrısı (Yöntem kuyruğu kendisini çağırır)<br/><br/>2: yardımcı yardımlı kuyruk çağrısı|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodjittailcallfailed-event"></a>Methodjbir Callcallfailed olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` (0x1000) |Verbose (5)|

|Olay|Olay Kimliği|Description|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|191|Bir yöntemin kuyruğu çağrıldığında JıT derleyicisi tarafından tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|Derlenmekte olan metodun ad alanı.|
|`MethodBeingCompiledName`|`win:UnicodeString`|Derlenmekte olan yöntemin adı.|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|Derlenen yöntemin imzası (tür adlarının virgülle ayrılmış listesi).|
|`CallerNamespace`|`win:UnicodeString`|Çağıran yönteminin ad alanı.|
|`CallerNam`a|`win:UnicodeString`|Arayan yönteminin adı.|
|`CallerNameSignature`|`win:UnicodeString`|Çağıran yönteminin imzası (tür adlarının virgülle ayrılmış listesi).|
|`CalleeNamespace`|`win:UnicodeString`|Çağrılan metodun ad alanı.|
|`CalleeName`|`win:UnicodeString`|Çağrılan yöntemin adı.|
|`CalleeNameSignature`|`win:UnicodeString`|Çağrılan metodun imzası (tür adlarının virgülle ayrılmış listesi).|
|`TailPrefix`|`win:Boolean`|Bir kuyruk ön eki yönergesi olup olmadığı.|
|`FailReason`|`win:UnicodeString`|Kuyruk çağrısı başarısız oldu.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="methodiltonativemap-event"></a>Methoddiltonativemap olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`JittedMethodILToNativeMapKeyword` (0x20000) |Verbose (5)|

|Olay|Olay Kimliği|Description|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|190|JıT ile derlenen metotlar için IL-yerel eşleme olayını eşler.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|Metodun benzersiz tanımlayıcısı.|
|`ReJITID`|`win:UInt64`|Metodun ReJIT KIMLIĞI.|
|`MethodExtent`|`win:UInt8`|Jnderlenen yöntemin uzantısı.|
|`CountOfMapEntries`|`win:UInt8`|Eşleme girişi sayısı|
|`ILOffsets`|`win:UInt32`|Il kayması.|
|`NativeOffsets`|`win:UInt32`|Yerel kod boşluğu.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
