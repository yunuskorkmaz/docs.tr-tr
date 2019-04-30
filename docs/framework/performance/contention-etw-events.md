---
title: Çekişme ETW olayları - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723946"
---
# <a name="contention-etw-events"></a>Çekişme ETW olayları

Çekişme olayları oluştuğunda için Çekişme olduğunda <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitler veya çalışma zamanı tarafından kullanılan yerel kilitler. Başka bir iş parçacığı kilit sahip olduğu sırada bir kilit için bekleyen bir iş parçacığı Çekişme gerçekleşir.

Çekişme olayları altında oluşturulan anahtar sözcüğü ve olayları düzeyi aşağıdaki tabloda gösterilmektedir. Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](clr-etw-keywords-and-levels.md).

|Olayı için anahtar sözcüğü|Düzey|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Bilgilendirici (4)|

Aşağıdaki tabloda, olay bilgiler gösterir:

|Olay|Olay Kimliği|Ne zaman gerçekleşti|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Çekişme başlatır. Bu olay, dönen bir iş parçacığı kilit için bekleyen önceki süre miktarını içermez; yalnızca iş parçacığının bir kilidi bekler olduğunda tetiklenir.|
|`ContentionStop`|91|Çekişme sona erer.|

Aşağıdaki tabloda, olay verilerini gösterir:

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|Bayraklar|Kazanma: UInt8|0 için yönetilen; Yerel için 1.|
|ClrInstanceID|Kazanma: UInt16|CLR örneği için benzersiz kimliği.|

## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
