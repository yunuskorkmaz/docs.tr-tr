---
title: Birlikte çalışma çalışma zamanı olayları
description: Birlikte çalışabilirlik 'e özgü tanılama bilgilerini toplamak için .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Interop events (CoreCLR)
- ETW, EventPipe, LTTng interop events (CoreCLR)
ms.openlocfilehash: 5635fb55b3a6ffa3f5611da80cdb2909e226e2ea
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589994"
---
# <a name="net-runtime-interop-events"></a>.NET çalışma zamanı birlikte çalışma olayları

Bu çalışma zamanı olayları ortak ara dil (CıL) saplama oluşturma hakkındaki bilgileri yakalar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="ilstubgenerated-event"></a>ILStubGenerated olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`InteropKeyword` (0x2000)|Bilgilendirici (4)|
  
|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ILStubGenerated`|88|Il saplaması oluşturulur.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt16`|Modül tanımlayıcısı.|
|`StubMethodID`|`win:UInt64`|Saplama yöntemi tanımlayıcısı.|
|`StubFlags`|`win:UInt32`|Saplama bayrakları:<br /><br /> `0x1` -Ters çalışabilirliği.<br /><br /> `0x2` -COM birlikte çalışma.<br /><br /> `0x4` -NGen.exe tarafından oluşturulan saplama.<br /><br /> `0x8` Ğini.<br /><br /> `0x10` -Variable bağımsız değişkeni.<br /><br /> `0x20` -Yönetilmeyen aranan.<br /><br /> `0x40` -Struct sıralaması|
|`ManagedInteropMethodToken`|`win:UInt32`|Managed Interop yöntemi için belirteç.|
|`ManagedInteropMethodNameSpace`|`win:UnicodeString`|Yönetilen birlikte çalışma yönteminin ad alanı ve kapsayan türü.|
|`ManagedInteropMethodName`|`win:UnicodeString`|Yönetilen birlikte çalışma yönteminin adı.|
|`ManagedInteropMethodSignature`|`win:UnicodeString`|Managed Interop yönteminin imzası.|
|`NativeMethodSignature`|`win:UnicodeString`|Yerel Yöntem imzası.|
|`StubMethodSignature`|`win:UnicodeString`|Saplama yöntemi imzası.|
|`StubMethodILCode`|`win:UnicodeString`|Saplama yöntemi için ortak ara dil (CıL) kodu.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|
