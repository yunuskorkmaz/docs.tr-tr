---
title: Sistem çalışma zamanı olaylarını yazın
description: TypeLoadStart ve TypeLoadStop gibi .NET tür sistemine özgü tanılama bilgilerini toplanan .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589989"
---
# <a name="net-runtime-type-events"></a>.NET çalışma zamanı türü olayları

Bu olaylar, yükleme türleriyle ilgili bilgiler toplar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="typeloadstart-event"></a>TypeLoadStart olayı

|Olayı yükseltmek için anahtar sözcük|Olay|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Bilgilendirici (4)|  

|Olay|Olay Kimliği|Description|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|73|Bir tür yüklemesi başlatıldı.|

|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|Tür yükleme işleminin KIMLIĞI.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  

## <a name="typeloadstop-event"></a>TypeLoadStop olayı

|Olayı yükseltmek için anahtar sözcük|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` (0x8000000000)|Bilgilendirici (4)|  

|Olay|Olay Kimliği|Description|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|74|Bir tür yüklemesi tamamlandı.|

|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|Tür yükleme işleminin KIMLIĞI (karşılık gelen TypeLoadStart olayının Typeloadstartıd ile eşleşir).|
|`LoadLevel`|`win:UInt16`|Yük düzeyini yazın.|
|`TypeID`|`win:UInt64`|Tür tanıtıcısına yönelik işaretçi.|
|`TypeName`|`win:UnicodeString`|Türün adı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
