---
title: SYSLIB0011 uyarısı
description: Derleme zamanı uyarı SYSLIB0011 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1b4f4c24c64148319f659b78573a4d80fd5b98a7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440021"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="f00be-103">SYSLIB0011: BinaryFormatter serileştirme artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="f00be-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="f00be-104">' Deki [güvenlik açıklarına](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki apı 'ler .NET 5,0 ' den itibaren eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f00be-104">Due to [security vulnerabilities](../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="f00be-105">Kod içinde kullanmak, `SYSLIB0011` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f00be-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="f00be-106">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="f00be-106">Workarounds</span></span>

<span data-ttu-id="f00be-107"><xref:System.Text.Json.JsonSerializer>Yerine veya kullanmayı düşünün <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .</span><span class="sxs-lookup"><span data-stu-id="f00be-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="f00be-108">Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="f00be-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="f00be-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f00be-109">See also</span></span>

- [<span data-ttu-id="f00be-110">BinaryFormatter kullanımdan çıkarılması ve disablement hataları çözümleniyor</span><span class="sxs-lookup"><span data-stu-id="f00be-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](https://aka.ms/binaryformatter)
- [<span data-ttu-id="f00be-111">BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış</span><span class="sxs-lookup"><span data-stu-id="f00be-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](corefx.md#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
