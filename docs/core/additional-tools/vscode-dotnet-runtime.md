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
# <a name="net-install-tool-for-extension-authors"></a><span data-ttu-id="eacac-103">Uzantı yazarları için .NET yüklemesi aracı</span><span class="sxs-lookup"><span data-stu-id="eacac-103">.NET install tool for extension authors</span></span>

<span data-ttu-id="eacac-104">[Uzantı yazarları için .net Install aracı](https://github.com/dotnet/vscode-dotnet-runtime) , .NET çalışma zamanının özellikle vs Code uzantısı yazarları için alım almasına izin veren bir Visual Studio Code uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="eacac-104">The [.NET install tool for extension authors](https://github.com/dotnet/vscode-dotnet-runtime) is a Visual Studio Code extension that allows acquisition of the .NET runtime specifically for VS Code extension authors.</span></span> <span data-ttu-id="eacac-105">Bu aracın .NET dilinde yazılmış ve uzantının (örneğin, bir dil sunucusu) önyüklemesinde .NET gerektiren uzantılar için yararlanılabilir olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eacac-105">This tool is intended to be leveraged in extensions that are written in .NET and require .NET to boot pieces of the extension (for example, a language server).</span></span> <span data-ttu-id="eacac-106">Uzantı, kullanıcıların geliştirme için .NET yüklemesi tarafından doğrudan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="eacac-106">The extension is not intended to be used directly by users to install .NET for development.</span></span>

## <a name="getting-started-extension-authors"></a><span data-ttu-id="eacac-107">Başlarken: uzantı yazarları</span><span class="sxs-lookup"><span data-stu-id="eacac-107">Getting started: extension authors</span></span>

<span data-ttu-id="eacac-108">Uzantı yazarları için .NET Install aracının senaryonuza doğru uygun olduğundan emin olmak için GitHub sayfamızda [Bu uzantının hedeflerini](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) inceleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="eacac-108">To ensure that the .NET install tool for extension authors is the right fit for your scenario, start by reviewing the [goals of this extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) on our GitHub page.</span></span>

> [!NOTE]
> <span data-ttu-id="eacac-109">Bu araç yalnızca .NET çalışma zamanını yüklemek için kullanılabilir. Şu anda .NET SDK 'Yı yüklemek için yetenek yoktur.</span><span class="sxs-lookup"><span data-stu-id="eacac-109">This tool can be used to install the .NET runtime only, it currently does not have the capability to install the .NET SDK.</span></span>

<span data-ttu-id="eacac-110">Uzantı yazarları için .NET yüklemesi aracının ihtiyaçlarınıza uygun olduğunu doğruladıktan sonra [uzantı bildiriminizde](https://code.visualstudio.com/api/references/extension-manifest) buna bir bağımlılık alabilir ve [vs Code API 'si](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command)ile kullanıma sunduğumuz komutları kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eacac-110">Once you have verified that the .NET install tool for extension authors fits your needs, you can take a dependency on it in your [extension manifest](https://code.visualstudio.com/api/references/extension-manifest) and begin using the commands we expose with the [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span></span> <span data-ttu-id="eacac-111">Bu uzantının [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md)'da sunduğu komutların listesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eacac-111">You can find the list of commands this extension exposes on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/commands.md).</span></span>

<span data-ttu-id="eacac-112">Bu adımları eylemde görmek için bu [örnek uzantıya](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) göz atın.</span><span class="sxs-lookup"><span data-stu-id="eacac-112">Check out this [sample extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/master/sample) to see these steps in action.</span></span>

<span data-ttu-id="eacac-113">Daha fazla örnek için şu anda bu aracı kullanan bu açık kaynak uzantılarına göz atın:</span><span class="sxs-lookup"><span data-stu-id="eacac-113">For more examples, check out these open source extensions that currently leverage this tool:</span></span>

- [<span data-ttu-id="eacac-114">Visual Studio Code için Azure Resource Manager (ARM) araçları</span><span class="sxs-lookup"><span data-stu-id="eacac-114">Azure Resource Manager (ARM) Tools for Visual Studio Code</span></span>](https://github.com/microsoft/vscode-azurearmtools)

- [<span data-ttu-id="eacac-115">.NET etkileşimli not defterleri</span><span class="sxs-lookup"><span data-stu-id="eacac-115">.NET Interactive Notebooks</span></span>](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a><span data-ttu-id="eacac-116">Başlarken: son kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="eacac-116">Getting started: end users</span></span>

<span data-ttu-id="eacac-117">Genel olarak, son kullanıcının uzantı yazarları için .NET install aracıyla etkileşimde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eacac-117">In general, the end user should not need to interact with the .NET install tool for extension authors at all.</span></span> <span data-ttu-id="eacac-118">Uzantıyla ilgili sorun yaşıyorsanız [sorun giderme sayfamıza](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) göz atın veya [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues)' da bir sorun gidermeye hazır olun.</span><span class="sxs-lookup"><span data-stu-id="eacac-118">If you are having problems with the extension, check out our [troubleshooting page](https://github.com/dotnet/vscode-dotnet-runtime/blob/master/Documentation/troubleshooting.md) or file an issue on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span></span>
