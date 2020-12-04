---
title: VS Code uzantısı yazarları için .NET yüklemesi aracı
description: .NET çalışma zamanı yüklemeye yönelik Visual Studio Code uzantısı olan uzantı yazarları için .NET yükleme aracına genel bakış.
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: 37be1b9dcdb9fba99554800fea23f28443efb5fa
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599916"
---
# <a name="net-install-tool-for-extension-authors"></a>Uzantı yazarları için .NET yüklemesi aracı

[Uzantı yazarları için .net Install aracı](https://github.com/dotnet/vscode-dotnet-runtime) , .NET çalışma zamanının özellikle vs Code uzantısı yazarları için alım almasına izin veren bir Visual Studio Code uzantısıdır. Bu aracın .NET dilinde yazılmış ve uzantının (örneğin, bir dil sunucusu) önyüklemesinde .NET gerektiren uzantılar için yararlanılabilir olması amaçlanmıştır. Uzantı, kullanıcıların geliştirme için .NET yüklemesi tarafından doğrudan kullanılmaya yönelik değildir.

## <a name="getting-started-extension-authors"></a>Başlarken: uzantı yazarları

Uzantı yazarları için .NET Install aracının senaryonuza doğru uygun olduğundan emin olmak için GitHub sayfamızda [Bu uzantının hedeflerini](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) inceleyerek başlayın.

> [!NOTE]
> Bu araç yalnızca .NET çalışma zamanını yüklemek için kullanılabilir. Şu anda .NET SDK 'Yı yüklemek için yetenek yoktur.

Uzantı yazarları için .NET yüklemesi aracının ihtiyaçlarınıza uygun olduğunu doğruladıktan sonra [uzantı bildiriminizde](https://code.visualstudio.com/api/references/extension-manifest) buna bir bağımlılık alabilir ve [vs Code API 'si](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command)ile kullanıma sunduğumuz komutları kullanmaya başlayabilirsiniz. Bu uzantının [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md)'da sunduğu komutların listesini bulabilirsiniz.

Bu adımları eylemde görmek için bu [örnek uzantıya](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) göz atın.

Daha fazla örnek için şu anda bu aracı kullanan bu açık kaynak uzantılarına göz atın:

- [Visual Studio Code için Azure Resource Manager (ARM) araçları](https://github.com/microsoft/vscode-azurearmtools)

- [.NET etkileşimli not defterleri](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a>Başlarken: son kullanıcılar

Genel olarak, son kullanıcının uzantı yazarları için .NET install aracıyla etkileşimde olması gerekmez. Uzantıyla ilgili sorun yaşıyorsanız [sorun giderme sayfamıza](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) göz atın veya [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues)' da bir sorun gidermeye hazır olun.
