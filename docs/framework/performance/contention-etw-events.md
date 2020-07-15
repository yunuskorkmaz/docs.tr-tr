---
title: Çekişme ETW olayları-.NET
description: System. Threading. Monitor kilitleri veya çalışma zamanı tarafından kullanılan yerel kilitler için çekişme olduğunda oluşan çekişme ETW olayları hakkında ayrıntılı bilgi alın.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309607"
---
# <a name="contention-etw-events"></a>Çekişme ETW olayları

Çekişme, <xref:System.Threading.Monitor?displayProperty=nameWithType> çalışma zamanı tarafından kullanılan kilitler veya yerel kilitler için çekişme olduğunda oluşturulur. Başka bir iş parçacığı kilitlemeye sahip olsa da bir iş parçacığı kilit beklerken bir çekişme meydana gelir.

Aşağıdaki tabloda, çekişme olaylarının oluşturulduğu anahtar sözcüğü ve olayların düzeyi gösterilmektedir. Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`ContentionKeyword`0x4000|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Çekişme başlar. Bu olay, bir iş parçacığının bir kilit elde etmeden önce geçen dönme süresini içermez; yalnızca iş parçacığı bir kilit almayı bekliyorsa tetiklenir.|
|`ContentionStop`|91|Çekişme bitiyor.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Description|
|----------------|---------------|-----------------|
|Bayraklar|Win: UInt8|yönetilen için 0; Yerel için 1.|
|ClrInstanceID|Win: UInt16|CLR örneği için benzersiz KIMLIK.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
