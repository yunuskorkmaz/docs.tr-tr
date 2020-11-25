---
title: 'Son değişiklik: SignalR: MessagePack hub Protokolü MessagePack 2. x paketine taşındı'
description: "ASP.NET Core 5,0 ' deki, SignalR: MessagePack hub protokolünü MessagePack 2. x paketine taşınan Son değişiklik hakkında bilgi edinin"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e666c40d7046233c9fb06af819b901fd1251b06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761686"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack 2. x paketine taşınan MessagePack hub Protokolü

ASP.NET Core SignalR [MessagePack hub Protokolü](/aspnet/core/signalr/messagepackhubprotocol) MessagePack serileştirme Için [MessagePack NuGet paketini](https://www.nuget.org/packages/MessagePack) kullanır. ASP.NET Core 5,0 paketi 1. x sürümünden en son 2. x paketi sürümüne yükseltir.

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 1

## <a name="old-behavior"></a>Eski davranış

ASP.NET Core SignalR, MessagePack iletilerini seri hale getirmek ve seri durumdan çıkarmak için MessagePack 1. x paketini kullandı.

## <a name="new-behavior"></a>Yeni davranış

ASP.NET Core SignalR, MessagePack iletilerinin serileştirilmek ve serisini kaldırmak için MessagePack 2. x paketini kullanır.

## <a name="reason-for-change"></a>Değişiklik nedeni

MessagePack 2. x paketindeki en son geliştirmeler yararlı işlevsellik ekler.

## <a name="recommended-action"></a>Önerilen eylem

Bu son değişiklik şu durumlarda geçerlidir:

* Değerleri ayarlama veya yapılandırma <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .
* MessagePack API 'Lerini doğrudan kullanarak ve aynı projede ASP.NET Core SignalR MessagePack hub protokolünü kullanarak. Önceki sürüm yerine daha yeni bir sürüm yüklenecektir.

Paket yazarlarından geçiş kılavuzu için bkz. [MessagePack v1. x 'Ten MessagePack v2. x 'e](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)geçiş. İleti serileştirme ve seri durumdan çıkarma özelliklerinin bazı yönleri etkilenir. Özellikle, [DateTime değerlerinin serileştirilme şekli için davranış değişiklikleri](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)vardır.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
