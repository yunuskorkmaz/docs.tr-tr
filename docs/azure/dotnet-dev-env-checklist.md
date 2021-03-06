---
title: Azure yapılandırma denetim listesinde .NET geliştirme
description: Azure ile .NET geliştirme yapmak için yüklemiş olmanız gereken tüm araçların hızlı bir özetini sağlar
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 2f22f69ec99baf192d1cbdd28f884b7f47867389
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257986"
---
# <a name="net-on-azure-development-environment-checklist"></a>Azure geliştirme ortamında .NET denetim listesi

Bu denetim listesi, geliştirme ortamınızın Azure ile .NET geliştirmesi için doğru şekilde yapılandırıldığından emin olmanıza yardımcı olmak için sağlanır

## <a name="create-an-azure-account"></a>Azure hesabı oluşturma

Azure hizmetlerine erişmek veya Azure 'da uygulama çalıştırmak için bir Azure hesabınızın olması gerekir.

* Visual Studio abonesiyseniz, aylık [ücretsiz Azure kredilerinin](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) her ay sizin için kullanılabilir olduğunu
* [Ücretsiz bir Azure hesabı oluşturun](https://azure.microsoft.com/free/dotnet/) ve kredilerin $200 ' i alıp 12 ay boyunca ücretsiz hizmetler ' i seçin
* Şirketinizin Azure Yöneticisi tarafından size atanan bir hesabı kullanın

## <a name="configure-your-ide"></a>IDE 'nizi yapılandırma

Visual Studio ve Visual Studio Code gibi popüler araçlar, IDE 'nizden Azure ile çalışmanıza olanak sağlamak için kullanılabilir uzantılara sahiptir.

* Azure kullanarak .NET geliştirme için [Visual Studio 'Yu yapılandırma](./configure-visual-studio.md)
* Azure kullanarak .NET geliştirmesi için [Visual Studio Code yapılandırma](./configure-vs-code.md)

## <a name="install-the-azure-cli"></a>Azure CLI'yi yükleme

Azure portal kullanmanın yanı sıra Azure kaynaklarını oluşturmak ve yönetmek için Azure CLı 'yi de yüklemek isteyeceksiniz.

* [Windows için Azure CLI'yı yükleme](/cli/azure/install-azure-cli-windows?tabs=azure-cli)
* [macOS için Azure CLI'yı yükleme](/cli/azure/install-azure-cli-macos)
* [Linux için Azure CLı 'yı yükler](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a>Ek araçlar ve yardımcı programlar yükler

Bu ek araçlar, Azure ile çalışırken daha üretken olmanızı sağlayacak şekilde tasarlanmıştır.

* Azure kaynaklarını oluşturmak ve yönetmek için PowerShell betikleri kullanmayı planlıyorsanız [Azure PowerShell 'Yi yükler](/powershell/azure/install-az-ps)
* Blob, kuyruk, tablo ve CosmosDB gibi Azure depolama kaynaklarında verileri karşıya yüklemek, indirmek ve yönetmek için [Azure Depolama Gezgini yükleyin](https://azure.microsoft.com/features/storage-explorer/) .
* Azure SQL ile çalışıyorsanız [Azure Data Studio 'Yi yükler](/sql/azure-data-studio/download-azure-data-studio)

## <a name="bookmark-the-following-sites"></a>Aşağıdaki sitelere yer işareti ekleyin

Bu siteleri Azure geliştirme yaparken sık sık kullanacaksınız.  Hızlı başvuru için bunlara yer işareti ekleyin.

* Azure portalı- [https://portal.azure.com/](https://portal.azure.com/)
* Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)
