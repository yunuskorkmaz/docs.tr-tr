---
title: Çekişme ETW olayları-.NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716131"
---
# <a name="contention-etw-events"></a>Çekişme ETW olayları

Çekişme olayları, çalışma zamanı tarafından kullanılan <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitleri veya yerel kilitler için çekişme olduğunda tetiklenir. Başka bir iş parçacığı kilitlemeye sahip olsa da bir iş parçacığı kilit beklerken bir çekişme meydana gelir.

Aşağıdaki tabloda, çekişme olaylarının oluşturulduğu anahtar sözcüğü ve olayların düzeyi gösterilmektedir. Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).

|Olayı yükseltmek için anahtar sözcük|Düzey|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Bilgilendirici (4)|

Aşağıdaki tabloda olay bilgileri gösterilmektedir:

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Çekişme başlar. Bu olay, bir iş parçacığının bir kilit elde etmeden önce geçen dönme süresini içermez; yalnızca iş parçacığı bir kilit almayı bekliyorsa tetiklenir.|
|`ContentionStop`|91|Çekişme bitiyor.|

Aşağıdaki tabloda olay verileri gösterilmektedir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Bayraklar|Win: UInt8|yönetilen için 0; Yerel için 1.|
|ClrInstanceID|Win: UInt16|CLR örneği için benzersiz KIMLIK.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
