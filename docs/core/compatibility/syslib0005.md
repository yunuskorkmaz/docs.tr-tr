---
title: SYSLIB0005 uyarısı
description: Derleme zamanı uyarı SYSLIB0005 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8a9893d81c781335014c8b970c460b5a4241ed18
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333346"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005: genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor

.NET Core ve .NET 5,0 ve sonraki sürümleri, .NET Framework bulunan genel derleme önbelleği (GAC) kavramını ortadan kaldırır. Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'Lerin kullanılması, `SYSLIB0005` derleme zamanında uyarı oluşturur.

Aşağıdaki GAC ile ilgili API 'Ler artık kullanılmıyor olarak işaretlendi:

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 + ' de döndürdüğünden, çalışma zamanı davranışı hakkında belirleyici hale getirmek için API 'yi kullanmamalıdır.

## <a name="workaround"></a>Geçici çözüm

Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun. "GAC 'de olmayan bir derleme"-Flow "( <xref:System.Reflection.Assembly.GlobalAssemblyCache> GAC 'de olmayan bir derleme") arasında seçim yapmak için değeri kullanırsanız, akışın bir .NET 5 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel derleme önbelleği](../../framework/app-domains/gac.md)
