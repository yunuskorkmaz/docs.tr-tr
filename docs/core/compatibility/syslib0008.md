---
title: SYSLIB0008 uyarısı
description: Derleme zamanı uyarı SYSLIB0008 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440601"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008: CreatePdbGenerator desteklenmiyor

<xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API, .net 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'nin kullanılması, `SYSLIB0008` derleme zamanında uyarı oluşturur.

## <a name="suppress-the-warning"></a>Uyarıyı gösterme

Kodunuzu değiştirememek için, bir `#pragma` yönerge veya proje ayarı aracılığıyla uyarıyı gizleyebilirsiniz `<NoWarn>` . Örnekler için bkz. [uyarıları gösterme](syslib-obsoletions.md#suppress-warnings).
