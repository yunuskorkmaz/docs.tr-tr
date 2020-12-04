---
title: Yükleyici ve Ciltçi çalışma zamanı olayları
description: Derleme yükleyicisi ve Ciltçi hakkında bilgi toplamak için yükleyici ve Ciltçi ETW olaylarına özgü tanılama bilgilerini depolayan .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96590037"
---
# <a name="net-runtime-loader-and-binder-events"></a>.NET çalışma zamanı yükleyicisi ve Ciltçi olayları

Bu olaylar derlemeleri ve modülleri yükleme ve kaldırma ile ilgili bilgiler toplar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|151|Bir uygulama etki alanı için bir modül yüklendiğinde tetiklenir.|

## <a name="moduleload_v2-event"></a>ModuleLoad_V2 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|152|Bir işlemin ömrü boyunca bir modül yüklendiğinde tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|Modülün benzersiz KIMLIĞI.|
|`AssemblyID`|`win:UInt64`|Bu modülün bulunduğu derlemenin KIMLIĞI.|
|`ModuleFlags`|`win:UInt32`|0x1: etki alanı bağımsız modülü.<br /><br /> 0x2: modülün yerel bir görüntüsü vardır.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modülü.|
|`Reserved1`|`win:UInt32`|Ayrılmış alan.|
|`ModuleILPath`|`win:UnicodeString`|Modül için ortak ara dil (CıL) görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|
|`ModuleNativePath`|`win:UnicodeString`|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
|`ManagedPdbSignature`|`win:GUID`|Bu modülle eşleşen yönetilen program veritabanının (PDB) GUID imzası.|
|`ManagedPdbAge`|`win:UInt32`|Bu modülle eşleşen yönetilen PDB 'ye yazılan yaş numarası.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Bu modülle eşleşen yönetilen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|
|`NativePdbSignature`|`win:GUID`|Varsa, bu modülle eşleşen yerel görüntü Oluşturucu (NGen) PDB GUID imzası.|
|`NativePdbAge`|`win:UInt32`|Varsa, bu modülle eşleşen NGen PDB 'ye yazılan yaş numarası.|
|`NativePdbBuildPath`|`win:UnicodeString`|Geçerliyse, bu modülle eşleşen NGen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|

## <a name="moduleunload_v2-event"></a>ModuleUnload_V2 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|153|Bir işlem süresince bir modül kaldırıldığında tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|Modülün benzersiz KIMLIĞI.|
|`AssemblyID`|`win:UInt64`|Bu modülün bulunduğu derlemenin KIMLIĞI.|
|`ModuleFlags`|`win:UInt32`|0x1: etki alanı bağımsız modülü.<br /><br /> 0x2: modülün yerel bir görüntüsü vardır.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modülü.|
|`Reserved1`|`win:UInt32`|Ayrılmış alan.|
|`ModuleILPath`|`win:UnicodeString`|Modül için ortak ara dil (CıL) görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|
|`ModuleNativePath`|`win:UnicodeString`|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|
|`ClrInstanceID`|``win:UInt16``|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
|`ManagedPdbSignature`|`win:GUID`|Bu modülle eşleşen yönetilen program veritabanının (PDB) GUID imzası.|
|`ManagedPdbAge`|`win:UInt32`|Bu modülle eşleşen yönetilen PDB 'ye yazılan yaş numarası.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Bu modülle eşleşen yönetilen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|
|`NativePdbSignature`|`win:GUID`|Varsa, bu modülle eşleşen yerel görüntü Oluşturucu (NGen) PDB GUID imzası.|
|`NativePdbAge`|`win:UInt32`|Varsa, bu modülle eşleşen NGen PDB 'ye yazılan yaş numarası.|
|`NativePdbBuildPath`|`win:UnicodeString`|Geçerliyse, bu modülle eşleşen NGen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|

## <a name="moduledcstart_v2-event"></a>ModuleDCStart_V2 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)

|Olay|Olay Kimliği|Açıklama
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|153|Bir başlangıç Özeti sırasında modülleri numaralandırır.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|Modülün benzersiz KIMLIĞI.|
|`AssemblyID`|`win:UInt64`|Bu modülün bulunduğu derlemenin KIMLIĞI.|
|`ModuleFlags`|`win:UInt32`|0x1: etki alanı bağımsız modülü.<br /><br /> 0x2: modülün yerel bir görüntüsü vardır.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modülü.|
|`Reserved1`|`win:UInt32`|Ayrılmış alan.|
|`ModuleILPath`|`win:UnicodeString`|Modül için ortak ara dil (CıL) görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|
|`ModuleNativePath`|`win:UnicodeString`|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
|`ManagedPdbSignature`|`win:GUID`|Bu modülle eşleşen yönetilen program veritabanının (PDB) GUID imzası.|
|`ManagedPdbAge`|`win:UInt32`|Bu modülle eşleşen yönetilen PDB 'ye yazılan yaş numarası.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Bu modülle eşleşen yönetilen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|
|`NativePdbSignature`|`win:GUID`|Varsa, bu modülle eşleşen yerel görüntü Oluşturucu (NGen) PDB GUID imzası.|
|`NativePdbAge`|`win:UInt32`|Varsa, bu modülle eşleşen NGen PDB 'ye yazılan yaş numarası.|
|`NativePdbBuildPath`|`win:UnicodeString`|Geçerliyse, bu modülle eşleşen NGen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|

## <a name="moduledcend_v2-event"></a>ModuleDCEnd_V2 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|154|Bir son özeti sırasında modülleri numaralandırır.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|Modülün benzersiz KIMLIĞI.|
|`AssemblyID`|`win:UInt64`|Bu modülün bulunduğu derlemenin KIMLIĞI.|
|`ModuleFlags`|`win:UInt32`|0x1: etki alanı bağımsız modülü.<br /><br /> 0x2: modülün yerel bir görüntüsü vardır.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modülü.|
|`Reserved1`|`win:UInt32`|Ayrılmış alan.|
|`ModuleILPath`|`win:UnicodeString`|Modül için ortak ara dil (CıL) görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|
|`ModuleNativePath`|`win:UnicodeString`|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
|`ManagedPdbSignature`|`win:GUID`|Bu modülle eşleşen yönetilen program veritabanının (PDB) GUID imzası.|
|`ManagedPdbAge`|`win:UInt32`|Bu modülle eşleşen yönetilen PDB 'ye yazılan yaş numarası.|
|`ManagedPdbBuildPath`|`win:UnicodeString`|Bu modülle eşleşen yönetilen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|
|`NativePdbSignature`|`win:GUID`|Varsa, bu modülle eşleşen yerel görüntü Oluşturucu (NGen) PDB GUID imzası.|
|`NativePdbAge`|`win:UInt32`|Varsa, bu modülle eşleşen NGen PDB 'ye yazılan yaş numarası.|
|`NativePdbBuildPath`|`win:UnicodeString`|Geçerliyse, bu modülle eşleşen NGen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir.|

## <a name="assemblyload_v1-event"></a>AssemblyLoad_V1 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|154|Bir derleme yüklendiğinde tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|Derlemenin benzersiz KIMLIĞI.|
|`AppDomainID`|`win:UInt64`|Bu derlemenin etki alanının KIMLIĞI.|
|`BindingID`|`win:UInt64`|Derleme bağlamasını benzersiz bir şekilde tanımlayan KIMLIK.|
|`AssemblyFlags`|`win:UInt32`|0x1: etki alanı bağımsız derlemesi.<br /><br /> 0x2: dinamik derleme.<br /><br /> 0x4: bütünleştirilmiş kod yerel bir görüntüye sahip.<br /><br /> 0x8: toplanabilir derleme.|
|`AssemblyName`|`win:UnicodeString`|Tam derleme adı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.

## <a name="assemblyunload_v1-event"></a>AssemblyUnload_V1 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|155|Bir derleme yüklendiğinde tetiklenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|Derlemenin benzersiz KIMLIĞI.|
|`AppDomainID`|`win:UInt64`|Bu derlemenin etki alanının KIMLIĞI.|
|`BindingID`|`win:UInt64`|Derleme bağlamasını benzersiz bir şekilde tanımlayan KIMLIK.|
|`AssemblyFlags`|`win:UInt32`|0x1: etki alanı bağımsız derlemesi.<br /><br /> 0x2: dinamik derleme.<br /><br /> 0x4: bütünleştirilmiş kod yerel bir görüntüye sahip.<br /><br /> 0x8: toplanabilir derleme.|
|`AssemblyName`|`win:UnicodeString`|Tam derleme adı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="assemblydcstart_v1-event"></a>AssemblyDCStart_V1 olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`LoaderKeyword` 0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|155|Bir başlangıç Özeti sırasında derlemeleri numaralandırır.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|Derlemenin benzersiz KIMLIĞI.|
|`AppDomainID`|`win:UInt64`|Bu derlemenin etki alanının KIMLIĞI.|
|`BindingID`|`win:UInt64`|Derleme bağlamasını benzersiz bir şekilde tanımlayan KIMLIK.|
|`AssemblyFlags`|`win:UInt32`|0x1: etki alanı bağımsız derlemesi.<br /><br /> 0x2: dinamik derleme.<br /><br /> 0x4: bütünleştirilmiş kod yerel bir görüntüye sahip.<br /><br /> 0x8: toplanabilir derleme.|
|`AssemblyName`|`win:UnicodeString`|Tam derleme adı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="assemblyloadstart-event"></a>AssemblyLoadStart olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|`AssemblyLoadStart`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|290|Derleme yükü istendi.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`AssemblyPath`|`win:UnicodeString`|Derleme adının yolu.|
|`RequestingAssembly`|`win:UnicodeString`|İstek yapan ("üst") derlemenin adı.|
|`AssemblyLoadContext`|`win:UnicodeString`|Derlemenin yükleme bağlamı.|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|İstek ("Parent") derlemesinin yükleme bağlamı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="assemblyloadstop-event"></a>AssemblyLoadStop olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|`AssemblyLoadStart`|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|291|Derleme yükü istendi.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`AssemblyPath`|`win:UnicodeString`|Derleme adının yolu.|
|`RequestingAssembly`|`win:UnicodeString`|İstek yapan ("üst") derlemenin adı.|
|`AssemblyLoadContext`|`win:UnicodeString`|Derlemenin yükleme bağlamı.|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|İstek ("Parent") derlemesinin yükleme bağlamı.|
|`Success`|`win:Boolean`|Derleme yükünün başarılı olup olmadığı.|
|`ResultAssemblyName`|`win:UnicodeString`|Yüklenen derlemenin adı.|
|`ResultAssemblyPath`|`win:UnicodeString`|Öğesinden yüklenen derlemenin yolu.|
|`Cached`|`win:UnicodeString`|Yükün önbelleğe alınıp alınmayacağını belirtir.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="resolutionattempted-event"></a>Resolutiondenenen olay

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|292|Derleme yükü istendi.

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`Stage`|`win:UInt16`|Çözüm aşaması.<br/><br/>0: yüklemede bul.<br/><br/>1: derleme yükleme bağlamı</br><br/>2: uygulama derlemeleri.<br/><br/>3: varsayılan derleme yükleme bağlamı geri dönüş. <br/><br/>4: uydu derlemesini çözümleyin. <br/><br/>5: derleme yükleme bağlamı çözümleniyor.<br/><br/>6: AppDomain derleme çözümleniyor.
|`AssemblyLoadContext`|`win:UnicodeString`|Derlemenin yükleme bağlamı.|
|`Result`|`win:UInt16`|Çözümleme denemesinin sonucu.<br/><br/>0: başarılı<br/><br/>1: derleme NotFound<br/><br/>2: uyumsuz sürüm<br/><br/>3: eşleşmeyen derleme adı<br/><br/>4: hata<br/><br/>5: özel durum|
|`ResultAssemblyName`|`win:UnicodeString`|Çözümlenen derlemenin adı.|
|`ResultAssemblyPath`|`win:UnicodeString`|Çözümlenmiş derlemenin yolu.|
|`ErrorMessage`|`win:UnicodeString`|Özel durum varsa hata iletisi.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a>Assemblyloadcontextresolvinghandlerçağrılan olay

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|293|[Assemblyloadcontext. çözümleniyor](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) işleyicisi çağrıldı.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`HandlerName`|`win:UnicodeString`|Çağrılan işleyicinin adı.|
|`AssemblyLoadContext`|`win:UnicodeString`|Derlemenin yükleme bağlamı.|
|`ResultAssemblyName`|`win:UnicodeString`|Çözümlenen derlemenin adı.|
|`ResultAssemblyPath`|`win:UnicodeString`|Çözümlenmiş derlemenin yolu.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a>Appdomainassemblyresolvehandlerçağrılan olay

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|294|Bir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> işleyici çağrıldı.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`HandlerName`|`win:UnicodeString`|Çağrılan işleyicinin adı.|
|`ResultAssemblyName`|`win:UnicodeString`|Çözümlenen derlemenin adı.|
|`ResultAssemblyPath`|`win:UnicodeString`|Çözümlenmiş derlemenin yolu.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a>Assemblyloadfromresolvehandlerçağrılan olay

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|295|Bir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> işleyici çağrıldı.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|Derleme adının adı.|
|`IsTrackedLoad`|`win:Boolean`|Derleme yükünün izleniyor olup olmadığı.|
|`RequestingAssemblyPath`|`win:UnicodeString`|İstekte bulunan derlemenin yolu.|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|İstenen derlemenin yolu.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="knownpathprobed-event"></a>KnownPathProbed olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|-----------|
|`Binder` 4,|Bilgilendirici (4)|

|Olay|Olay Kimliği|Açıklama|
|-----------|--------------|-----------------|
|`KnownPathProbed`|296|Bilinen bir yol derleme için araştırılırdı.|

|Alan Adı|Veri Türü|Açıklama|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|Yol araştırılan.|
|`Source`|`win:UInt16`|Araştırılan yolun kaynağı.<br/><br/>0x0: uygulama derlemeleri.<br/><br/>0x1: uygulama yerel görüntü yolu.<br/><br/>0x2: uygulama yolu.</br><br/>0x3: platform kaynak kökleri.<br/><br/>0x4: uydu alt dizini.</br>|
|`Result`|`win:UInt32`|Araştırma için HRESULT.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
