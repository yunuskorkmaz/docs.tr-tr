---
title: SYSLIB0005 uyarısı
description: Derleme zamanı uyarı SYSLIB0005 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596584"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005: genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor

.NET Core ve .NET 5,0 ve sonraki sürümleri, .NET Framework bulunan genel derleme önbelleği (GAC) kavramını ortadan kaldırır. Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'Lerin kullanılması, `SYSLIB0005` derleme zamanında uyarı oluşturur.

Aşağıdaki GAC ile ilgili API 'Ler artık kullanılmıyor olarak işaretlendi:

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 + ' de döndürdüğünden, çalışma zamanı davranışı hakkında belirleyici hale getirmek için API 'yi kullanmamalıdır.

## <a name="workarounds"></a>Geçici Çözümler

Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun. "GAC 'de olmayan bir derleme"-Flow "( <xref:System.Reflection.Assembly.GlobalAssemblyCache> GAC 'de olmayan bir derleme") arasında seçim yapmak için değeri kullanırsanız, akışın bir .NET 5 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Genel derleme önbelleği](../../../framework/app-domains/gac.md)
