---
title: SYSLIB0008 uyarısı
description: Derleme zamanı uyarı SYSLIB0008 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2b573f4b28cdf79107395f5cb38a4226d0ccc11e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596554"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008: CreatePdbGenerator desteklenmiyor

<xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API, .net 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'nin kullanılması, `SYSLIB0008` derleme zamanında uyarı oluşturur.

## <a name="suppress-the-warning"></a>Uyarıyı gösterme

Kodunuzu değiştirememek için, bir `#pragma` yönerge veya proje ayarı aracılığıyla uyarıyı gizleyebilirsiniz `<NoWarn>` . Örnekler için bkz. [uyarıları gösterme](../syslib-obsoletions.md#suppress-warnings).
