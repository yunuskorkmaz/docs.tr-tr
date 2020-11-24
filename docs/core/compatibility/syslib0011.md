---
title: SYSLIB0011 uyarısı
description: Derleme zamanı uyarı SYSLIB0011 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 99cdd9f5335f71eb9325039891db17972fb48532
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685012"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a>SYSLIB0011: BinaryFormatter serileştirme artık kullanılmıyor

' Deki [güvenlik açıklarına](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki apı 'ler .NET 5,0 ' den itibaren eski olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0011` derleme zamanında uyarı oluşturur.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

<xref:System.Text.Json.JsonSerializer>Yerine veya kullanmayı düşünün <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .

Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](https://aka.ms/binaryformatter).

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [BinaryFormatter kullanımdan çıkarılması ve disablement hataları çözümleniyor](https://aka.ms/binaryformatter)
- [BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış](core-libraries/5.0/binaryformatter-serialization-obsolete.md)
