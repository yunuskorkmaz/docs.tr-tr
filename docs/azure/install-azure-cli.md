---
title: Azure CLI yükleme
description: Azure geliştiricileri 'nin Azure CLı 'nin yüklü olması gerekir, bu nedenle bu makalede CLı ve nereden indirileceği ve yükleneceğine ilişkin durumlar açıklanmaktadır.
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: aa2739cc6c11145887e64921398c72affeaec729
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025035"
---
# <a name="install-the-azure-cli"></a><span data-ttu-id="9d876-103">Azure CLI'yi yükleme</span><span class="sxs-lookup"><span data-stu-id="9d876-103">Install the Azure CLI</span></span>

<span data-ttu-id="9d876-104">Azure portalına ek olarak, Azure Azure kaynaklarını oluşturmak ve yönetmek için Azure [CLI](/cli/azure/) 'yi bir komut satırı aracı olarak da sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d876-104">In addition to the Azure Portal, Azure also offers the [Azure CLI](/cli/azure/) as a command-line tool to create and manage Azure resources.</span></span> <span data-ttu-id="9d876-105">Azure CLı, verimlilik, yinelenebilirlik ve yinelenen görevleri betikleştirime avantajları sunar.</span><span class="sxs-lookup"><span data-stu-id="9d876-105">The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks.</span></span>  

<span data-ttu-id="9d876-106">Uygulamada çoğu geliştirici hem Azure portalını hem de Azure CLı 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d876-106">In practice, most developers use both the Azure Portal and the Azure CLI.</span></span> <span data-ttu-id="9d876-107">Azure Portal 'ın yeni hizmetleri araştırırken ve Azure hesabınızdaki tüm kaynaklara genel bir bakış edinmesinde yararlı olduğu durumlarda, çoğu geliştirici Azure CLı 'yi daha hızlı ve daha verimli olacak şekilde bulur.</span><span class="sxs-lookup"><span data-stu-id="9d876-107">Where as the Azure Portal is useful when exploring new services and getting an overview of all of the resources in your Azure account, most developers find the Azure CLI to be faster and more efficient.</span></span>  <span data-ttu-id="9d876-108">Azure CLı, genellikle Azure portalında birden çok adımı alan tek bir komutta gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-108">The Azure CLI can often accomplish in a single command what takes multiple steps in the Azure Portal.</span></span>  <span data-ttu-id="9d876-109">Ayrıca, Azure CLı komutları bir dosyaya kaydedilemediğinden, geliştiriciler yinelenen görevlerin her seferinde aynı şekilde çalışmasını güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-109">In addition, since Azure CLI commands can be saved to a file, developers can assure that recurrent tasks are run the same way each time.</span></span>

<span data-ttu-id="9d876-110">Azure CLı, Windows, macOS ve Linux 'ta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d876-110">The Azure CLI is available for Windows, macOS, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d876-111">Windows için Azure CLI'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="9d876-111">Install the Azure CLI for Windows</span></span>](/cli/azure/install-azure-cli-windows?tabs=azure-cli)

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d876-112">macOS için Azure CLI'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="9d876-112">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d876-113">Linux için Azure CLı 'yı yükler</span><span class="sxs-lookup"><span data-stu-id="9d876-113">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

### <a name="azure-cloud-shell"></a><span data-ttu-id="9d876-114">Azure Cloud Shell</span><span class="sxs-lookup"><span data-stu-id="9d876-114">Azure Cloud Shell</span></span>

<span data-ttu-id="9d876-115">Azure CLı 'yi de Azure Cloud Shell de kullanabilirsiniz [https://shell.azure.com](https://shell.azure.com) .</span><span class="sxs-lookup"><span data-stu-id="9d876-115">You can also use the Azure CLI in the Azure Cloud Shell at [https://shell.azure.com](https://shell.azure.com).</span></span>  <span data-ttu-id="9d876-116">Azure Cloud Shell, Azure kaynaklarını yönetmeye yönelik tam işlevli, tarayıcı tabanlı bir kabuktur.</span><span class="sxs-lookup"><span data-stu-id="9d876-116">The Azure Cloud Shell is a fully functional, browser-based shell for managing Azure resources.</span></span>  <span data-ttu-id="9d876-117">Azure Cloud Shell, bir komut satırı ortamına ihtiyacınız olduğunda, ancak Azure CLı 'yi yükleyemedik bir cihazda çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d876-117">The Azure Cloud Shell is useful when you need a command line environment but are working on a device where you are unable to install the Azure CLI.</span></span>

![Tarayıcıda çalışan Azure Cloud Shell ekran görüntüsü](media/azure-cloud-shell.png)

### <a name="next-steps"></a><span data-ttu-id="9d876-119">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9d876-119">Next steps</span></span>

<span data-ttu-id="9d876-120">Daha sonra, Azure ile daha üretken olmanızı sağlamak için Azure Depolama Gezgini ve Azure Data Studio gibi [ek Azure Araçları yüklemek](./azure-tools.md) isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9d876-120">Next, you will want to [install additional Azure tools](./azure-tools.md) like Azure Storage Explorer and Azure Data Studio to make you more productive with Azure.</span></span>
