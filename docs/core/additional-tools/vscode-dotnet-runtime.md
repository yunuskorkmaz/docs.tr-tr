---
title: VS Code uzantısı yazarları için .NET yüklemesi aracı
description: .NET çalışma zamanı yüklemeye yönelik Visual Studio Code uzantısı olan uzantı yazarları için .NET yükleme aracına genel bakış.
author: sfoslund
ms.date: 11/18/2020
ms.openlocfilehash: a372d0cc728956920d013dac9bc0da1bcd3edc0b
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872996"
---
# <a name="net-install-tool-for-extension-authors"></a><span data-ttu-id="37049-103">Uzantı yazarları için .NET yükleme aracı</span><span class="sxs-lookup"><span data-stu-id="37049-103">.NET install tool for extension authors</span></span>

<span data-ttu-id="37049-104">[Uzantı yazarları için .net Install aracı](https://github.com/dotnet/vscode-dotnet-runtime) , .NET çalışma zamanının özellikle vs Code uzantısı yazarları için alım almasına izin veren bir Visual Studio Code uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="37049-104">The [.NET install tool for extension authors](https://github.com/dotnet/vscode-dotnet-runtime) is a Visual Studio Code extension that allows acquisition of the .NET runtime specifically for VS Code extension authors.</span></span> <span data-ttu-id="37049-105">Bu aracın .NET dilinde yazılmış ve uzantının (örneğin, bir dil sunucusu) önyüklemesinde .NET gerektiren uzantılar için yararlanılabilir olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="37049-105">This tool is intended to be leveraged in extensions that are written in .NET and require .NET to boot pieces of the extension (for example, a language server).</span></span> <span data-ttu-id="37049-106">Uzantı, kullanıcıların geliştirme için .NET yüklemesi tarafından doğrudan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="37049-106">The extension is not intended to be used directly by users to install .NET for development.</span></span>

## <a name="getting-started-extension-authors"></a><span data-ttu-id="37049-107">Başlarken: uzantı yazarları</span><span class="sxs-lookup"><span data-stu-id="37049-107">Getting started: extension authors</span></span>

<span data-ttu-id="37049-108">Uzantı yazarları için .NET Install aracının senaryonuza doğru uygun olduğundan emin olmak için GitHub sayfamızda [Bu uzantının hedeflerini](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) inceleyerek başlayın.</span><span class="sxs-lookup"><span data-stu-id="37049-108">To ensure that the .NET install tool for extension authors is the right fit for your scenario, start by reviewing the [goals of this extension](https://github.com/dotnet/vscode-dotnet-runtime#goals-acquiring-net-core-for-extensions) on our GitHub page.</span></span>

> [!NOTE]
> <span data-ttu-id="37049-109">Bu araç yalnızca .NET çalışma zamanını yüklemek için kullanılabilir. Şu anda .NET SDK 'Yı yüklemek için yetenek yoktur.</span><span class="sxs-lookup"><span data-stu-id="37049-109">This tool can be used to install the .NET runtime only, it currently does not have the capability to install the .NET SDK.</span></span>

<span data-ttu-id="37049-110">Uzantı yazarları için .NET yüklemesi aracının ihtiyaçlarınıza uygun olduğunu doğruladıktan sonra [uzantı bildiriminizde](https://code.visualstudio.com/api/references/extension-manifest) buna bir bağımlılık alabilir ve [vs Code API 'si](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command)ile kullanıma sunduğumuz komutları kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37049-110">Once you have verified that the .NET install tool for extension authors fits your needs, you can take a dependency on it in your [extension manifest](https://code.visualstudio.com/api/references/extension-manifest) and begin using the commands we expose with the [VS Code API](https://code.visualstudio.com/api/extension-guides/command#programmatically-executing-a-command).</span></span> <span data-ttu-id="37049-111">Bu uzantının [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/commands.md)'da sunduğu komutların listesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37049-111">You can find the list of commands this extension exposes on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/commands.md).</span></span>

<span data-ttu-id="37049-112">Bu adımları eylemde görmek için bu [örnek uzantıya](https://github.com/dotnet/vscode-dotnet-runtime/tree/main/sample) göz atın.</span><span class="sxs-lookup"><span data-stu-id="37049-112">Check out this [sample extension](https://github.com/dotnet/vscode-dotnet-runtime/tree/main/sample) to see these steps in action.</span></span>

<span data-ttu-id="37049-113">Daha fazla örnek için şu anda bu aracı kullanan bu açık kaynak uzantılarına göz atın:</span><span class="sxs-lookup"><span data-stu-id="37049-113">For more examples, check out these open source extensions that currently leverage this tool:</span></span>

- [<span data-ttu-id="37049-114">Visual Studio Code için Azure Resource Manager (ARM) araçları</span><span class="sxs-lookup"><span data-stu-id="37049-114">Azure Resource Manager (ARM) Tools for Visual Studio Code</span></span>](https://github.com/microsoft/vscode-azurearmtools)

- [<span data-ttu-id="37049-115">.NET etkileşimli not defterleri</span><span class="sxs-lookup"><span data-stu-id="37049-115">.NET Interactive Notebooks</span></span>](https://github.com/dotnet/interactive/tree/main/src/dotnet-interactive-vscode)

## <a name="getting-started-end-users"></a><span data-ttu-id="37049-116">Başlarken: son kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="37049-116">Getting started: end users</span></span>

<span data-ttu-id="37049-117">Genel olarak, son kullanıcının uzantı yazarları için .NET install aracıyla etkileşimde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="37049-117">In general, the end user should not need to interact with the .NET install tool for extension authors at all.</span></span> <span data-ttu-id="37049-118">Uzantıyla ilgili sorun yaşıyorsanız [sorun giderme sayfamıza](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/troubleshooting-runtime.md) göz atın veya [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues)' da bir sorun gidermeye hazır olun.</span><span class="sxs-lookup"><span data-stu-id="37049-118">If you are having problems with the extension, check out our [troubleshooting page](https://github.com/dotnet/vscode-dotnet-runtime/blob/main/Documentation/troubleshooting-runtime.md) or file an issue on our [GitHub](https://github.com/dotnet/vscode-dotnet-runtime/issues).</span></span>
