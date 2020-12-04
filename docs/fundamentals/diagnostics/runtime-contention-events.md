---
title: Kilit çakışması çalışma zamanı olaylarını izleme
description: İzleyici kilit çekişmelerini özel bilgi toplamak için bkz. ETW olayları.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96589998"
---
# <a name="net-runtime-contention-events"></a>.NET çalışma zamanı çekişme olayları

Bu çalışma zamanı olayları `Monitor.Enter` , veya C# lock anahtar sözcüğü gibi izleyici kilit çekişmeleri hakkındaki bilgileri yakalar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="contentionstart_v1-event"></a>ContentionStart_V1 olayı

Bu olay, bir izleyici kilit çakışması başlangıcında yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` 0x4000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|İzleyici Kilidi çakışması başlar.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` yönetilen için; `1` yerel için.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="contentionstop_v1-event"></a>ContentionStop_V1 olayı

Bu olay, bir izleyici kilit çakışması sonunda yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` 0x4000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|91|İzleyici Kilidi çakışması sona erer.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` yönetilen için; `1` yerel için.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|
|`DurationNs`|`win:Double`|Nanosaniye cinsinden çekişme süresi.|
