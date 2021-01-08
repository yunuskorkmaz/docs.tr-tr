---
title: Azure yapılandırma denetim listesinde .NET geliştirme
description: Azure ile .NET geliştirme yapmak için yüklemiş olmanız gereken tüm araçların hızlı bir özetini sağlar
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: a2ff9bbf1e6a8790ddc161a1a1c8d14e8fab6e41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98027276"
---
# <a name="net-on-azure-development-environment-checklist"></a><span data-ttu-id="463a1-103">Azure geliştirme ortamında .NET denetim listesi</span><span class="sxs-lookup"><span data-stu-id="463a1-103">.NET on Azure development environment checklist</span></span>

<span data-ttu-id="463a1-104">Bu denetim listesi, geliştirme ortamınızın Azure ile .NET geliştirmesi için doğru şekilde yapılandırıldığından emin olmanıza yardımcı olmak için sağlanır</span><span class="sxs-lookup"><span data-stu-id="463a1-104">This checklist is provided to help you make sure you have your development environment correctly configured for .NET development with Azure</span></span>

## <a name="create-an-azure-account"></a><span data-ttu-id="463a1-105">Azure hesabı oluşturma</span><span class="sxs-lookup"><span data-stu-id="463a1-105">Create an Azure account</span></span>

<span data-ttu-id="463a1-106">Azure hizmetlerine erişmek veya Azure 'da uygulama çalıştırmak için bir Azure hesabınızın olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="463a1-106">To access Azure services or run applications in Azure, you need an Azure account.</span></span>

* <span data-ttu-id="463a1-107">Visual Studio abonesiyseniz, aylık [ücretsiz Azure kredilerinin](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) her ay sizin için kullanılabilir olduğunu</span><span class="sxs-lookup"><span data-stu-id="463a1-107">If you are a Visual Studio subscriber, you have monthly [free Azure credits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) available to you every month</span></span>
* <span data-ttu-id="463a1-108">[Ücretsiz bir Azure hesabı oluşturun](https://azure.microsoft.com/free/dotnet/) ve kredilerin $200 ' i alıp 12 ay boyunca ücretsiz hizmetler ' i seçin</span><span class="sxs-lookup"><span data-stu-id="463a1-108">[Create a free Azure account](https://azure.microsoft.com/free/dotnet/) and receive $200 in credits and select services free for 12 months</span></span>
* <span data-ttu-id="463a1-109">Şirketinizin Azure Yöneticisi tarafından size atanan bir hesabı kullanın</span><span class="sxs-lookup"><span data-stu-id="463a1-109">Use an account assigned to you by your company's Azure administrator</span></span>

## <a name="configure-your-ide"></a><span data-ttu-id="463a1-110">IDE 'nizi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="463a1-110">Configure your IDE</span></span>

<span data-ttu-id="463a1-111">Visual Studio ve Visual Studio Code gibi popüler araçlar, IDE 'nizden Azure ile çalışmanıza olanak sağlamak için kullanılabilir uzantılara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="463a1-111">Popular tools like Visual Studio and Visual Studio Code have extensions available to let you work with Azure right from your IDE.</span></span>

* <span data-ttu-id="463a1-112">Azure kullanarak .NET geliştirme için [Visual Studio 'Yu yapılandırma](./configure-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="463a1-112">[Configure Visual Studio](./configure-visual-studio.md) for .NET development using Azure</span></span>
* <span data-ttu-id="463a1-113">Azure kullanarak .NET geliştirmesi için [Visual Studio Code yapılandırma](./configure-vs-code.md)</span><span class="sxs-lookup"><span data-stu-id="463a1-113">[Configure Visual Studio Code](./configure-vs-code.md) for .NET Development using Azure</span></span>

## <a name="install-the-azure-cli"></a><span data-ttu-id="463a1-114">Azure CLI'yi yükleme</span><span class="sxs-lookup"><span data-stu-id="463a1-114">Install the Azure CLI</span></span>

<span data-ttu-id="463a1-115">Azure portal kullanmanın yanı sıra Azure kaynaklarını oluşturmak ve yönetmek için Azure CLı 'yi de yüklemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="463a1-115">In addition to using the Azure portal, you will want to install the Azure CLI to create and manage Azure resources.</span></span>

* <span data-ttu-id="463a1-116">[Windows Için Azure CLI 'Yı yükler](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span><span class="sxs-lookup"><span data-stu-id="463a1-116">[Install the Azure CLI for Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span></span>
* [<span data-ttu-id="463a1-117">macOS için Azure CLI'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="463a1-117">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)
* [<span data-ttu-id="463a1-118">Linux için Azure CLı 'yı yükler</span><span class="sxs-lookup"><span data-stu-id="463a1-118">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a><span data-ttu-id="463a1-119">Ek araçlar ve yardımcı programlar yükler</span><span class="sxs-lookup"><span data-stu-id="463a1-119">Install additional tools and utilities</span></span>

<span data-ttu-id="463a1-120">Bu ek araçlar, Azure ile çalışırken daha üretken olmanızı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="463a1-120">These additional tools are designed to make you more productive when working with Azure.</span></span>

* <span data-ttu-id="463a1-121">Azure kaynaklarını oluşturmak ve yönetmek için PowerShell betikleri kullanmayı planlıyorsanız [Azure PowerShell 'Yi yükler](/powershell/azure/install-az-ps)</span><span class="sxs-lookup"><span data-stu-id="463a1-121">[Install Azure PowerShell](/powershell/azure/install-az-ps) if you plan on using PowerShell scripts to create and manage Azure resources</span></span>
* <span data-ttu-id="463a1-122">Blob, kuyruk, tablo ve CosmosDB gibi Azure depolama kaynaklarında verileri karşıya yüklemek, indirmek ve yönetmek için [Azure Depolama Gezgini yükleyin](https://azure.microsoft.com/features/storage-explorer/) .</span><span class="sxs-lookup"><span data-stu-id="463a1-122">[Install Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) to upload, download, and manage data in Azure storage resources including blobs, queues, tables, and CosmosDB.</span></span>
* <span data-ttu-id="463a1-123">Azure SQL ile çalışıyorsanız [Azure Data Studio 'Yi yükler](/sql/azure-data-studio/download-azure-data-studio)</span><span class="sxs-lookup"><span data-stu-id="463a1-123">[Install Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) if you are working with Azure SQL</span></span>

## <a name="bookmark-the-following-sites"></a><span data-ttu-id="463a1-124">Aşağıdaki sitelere yer işareti ekleyin</span><span class="sxs-lookup"><span data-stu-id="463a1-124">Bookmark the following sites</span></span>

<span data-ttu-id="463a1-125">Bu siteleri Azure geliştirme yaparken sık sık kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="463a1-125">You will use these sites frequently when doing Azure development.</span></span>  <span data-ttu-id="463a1-126">Hızlı başvuru için bunlara yer işareti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="463a1-126">Bookmark them for quick reference.</span></span>

* <span data-ttu-id="463a1-127">Azure portalı- [https://portal.azure.com/](https://portal.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="463a1-127">Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)</span></span>
* <span data-ttu-id="463a1-128">Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="463a1-128">Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)</span></span>
