---
title: SYSLIB0011 uyarısı
description: Derleme zamanı uyarı SYSLIB0011 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189863"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a>SYSLIB0011: BinaryFormatter serileştirme artık kullanılmıyor

' Deki [güvenlik açıklarına](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki apı 'ler .NET 5,0 ' den itibaren eski olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0011` derleme zamanında uyarı oluşturur.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

<xref:System.Text.Json.JsonSerializer>Yerine veya kullanmayı düşünün <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .

Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](../../../standard/serialization/binaryformatter-security-guide.md).

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [BinaryFormatter kullanımdan çıkarılması ve disablement hataları çözümleniyor](../../../standard/serialization/binaryformatter-security-guide.md)
- [BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
