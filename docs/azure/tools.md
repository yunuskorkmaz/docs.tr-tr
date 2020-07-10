---
title: Azure .NET geliştiricileri için Araçlar
description: Azure .NET kitaplıklarını bir Windows, Linux ve Mac ortamından kullanmaya başlamak için Araçları alın.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174955"
---
# <a name="azure-tools-for-developing-with-net"></a>.NET ile geliştirmeye yönelik Azure Araçları

## <a name="sdk-downloads"></a>SDK İndirmeleri

.NET için Azure kitaplıkları, [NuGet paketleri](https://www.nuget.org/packages?q=windowsazureofficial)olarak uygulanır. Azure hizmeti tarafından düzenlenen başvuru belgeleri için [API başvurusuna](/dotnet/api/overview/azure/?view=azure-dotnet) bakın.

## <a name="development-tools"></a>Geliştirme araçları

Visual Studio, yerleşik birçok Azure hizmeti için araç içerir. Bazı Azure hizmetlerinde [Azure Depolama Gezgini](https://azure.microsoft.com/features/storage-explorer/)gibi ek araçlar veya Öykünücüler mevcuttur. Gerekirse, ek araçlar için Azure hizmetinize yönelik belgelere bakın.

Aşağıda tercih ettiğiniz geliştirme ortamınızı seçin.

## <a name="visual-studio-on-windows"></a>[Windows üzerinde Visual Studio](#tab/vs)

Visual Studio sürüm 2017 ve üzeri, Azure geliştirme için yerleşik desteğe sahiptir. Aşağıdaki adımlarda, Visual Studio 'da Azure geliştirme desteğinin etkinleştirilmesi açıklanır.

Visual Studio 2015 ve önceki sürümleri için <a href="vs2015-install.md">Bu yönergeleri izleyin</a>.

### <a name="step-1-download-visual-studio-2019"></a>1. Adım: Visual Studio 2019 ' i Indirin

Visual Studio 2019 zaten yüklüyse, bu adımı atlayabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio 2019’u İndirin](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>2. Adım: iki Azure iş yükünü yüklerken

Visual Studio yükleyicisi ' nde, Visual Studio 'Yu (veya var olan bir yüklemeyi değiştirme) yükleme. *Azure geliştirme* ve *ASP.net ve Web geliştirme* iş yüklerinin seçildiğinden emin olun.

### <a name="step-3-develop-with-net-on-azure"></a>3. Adım: Azure 'da .NET ile geliştirme

[İlk ASP.NET Core Web uygulamanızı Azure App Service dağıtmaya](/azure/app-service-web/app-service-web-get-started-dotnet)başlayın.

## <a name="visual-studio-code-cross-platform"></a>[Visual Studio Code (platformlar arası)](#tab/vscode)

Visual Studio Code platformlar arası Azure geliştirme için ihtiyacınız olan her şeye sahiptir.

### <a name="step-1-download-the-net-core-sdk"></a>1. Adım: .NET Core SDK Indirin

.NET Core uygulamaları için SDK ve komut satırı araçları.

> [!div class="nextstepaction"]
> [.NET Core SDK indir](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>2. Adım: Visual Studio Code

Herhangi bir işletim sisteminde .NET Core uygulamalarını düzenleyin ve hatalarını ayıklayın: Windows, Mac ve Linux.

> [!div class="nextstepaction"]
> [Visual Studio Code indir](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a>3. Adım: Azure Araçları uzantısı

Azure Araçları uzantısını Visual Studio Code ' ye yükler.

> [!div class="nextstepaction"]
> [Azure Araçları uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a>4. Adım: Azure 'da .NET ile geliştirme

[Linux üzerinde Azure App Service üzerinde ilk ASP.NET Core Web uygulamanızı dağıtmaya](/azure/app-service/containers/quickstart-dotnetcore)başlayın.

---
