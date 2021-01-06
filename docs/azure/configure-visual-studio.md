---
title: .NET ile Azure geliştirme için Visual Studio 'Yu yapılandırma
description: Bu makalede, Visual Studio 'nun yüklü olduğu ve Azure hesabınıza bağlanması dahil olmak üzere Azure için Visual Studio geliştirme 'yi yapılandırmanıza yardımcı olur
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701223"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a><span data-ttu-id="20035-103">.NET ile Azure geliştirme için Visual Studio 'Yu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="20035-103">Configure Visual Studio for Azure development with .NET</span></span>

<span data-ttu-id="20035-104">Visual Studio, Azure 'da uygulamaların geliştirilmesine ve dağıtımına yardımcı olan araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="20035-104">Visual Studio includes tooling to help with the development and deployment of applications on Azure.</span></span>  <span data-ttu-id="20035-105">Bu kılavuz, Azure geliştirmesi için Visual Studio 'Yu doğru şekilde yapılandırdığınızdan emin olmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="20035-105">This guide will help you make sure that you have Visual Studio properly configured for Azure development.</span></span>

### <a name="download-visual-studio-2019"></a><span data-ttu-id="20035-106">Visual Studio 2019’u İndirin</span><span class="sxs-lookup"><span data-stu-id="20035-106">Download Visual Studio 2019</span></span>

<span data-ttu-id="20035-107">Visual Studio 2019 zaten yüklüyse, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20035-107">If you already have Visual Studio 2019 installed, you can skip this step.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20035-108">Visual Studio 2019’u İndirin</span><span class="sxs-lookup"><span data-stu-id="20035-108">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a><span data-ttu-id="20035-109">Azure iş yüklerini yükler</span><span class="sxs-lookup"><span data-stu-id="20035-109">Install Azure workloads</span></span>

<span data-ttu-id="20035-110">**Visual Studio yükleyicisi** başlatın ve **Azure geliştirme** ve **ASP.net ve Web geliştirme** iş yüklerinin yüklü olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="20035-110">Launch the **Visual Studio Installer** and validate that you have the workloads **Azure development** and **ASP.NET and web development** are installed.</span></span>  <span data-ttu-id="20035-111">Bu iş yüklerinden herhangi biri yüklü değilse, yüklemek için bu iş yüklerini seçin.</span><span class="sxs-lookup"><span data-stu-id="20035-111">If either of these workloads is not installed, select these workloads to install them.</span></span>

![Azure geliştirme ve ASP.NET ve Web geliştirme Iş yüklerinin seçili olduğunu gösteren Visual Studio Yükleyicisi ekran görüntüsü](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a><span data-ttu-id="20035-113">Azure ile Visual Studio kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="20035-113">Authenticate Visual Studio with Azure</span></span>

<span data-ttu-id="20035-114">Visual Studio aracılığıyla uygulamalarda hata ayıklarken, Visual Studio Azure hesabınızı kullanarak kimlik doğrulaması yapabilir ve Azure kaynaklarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="20035-114">When debugging apps through Visual Studio, Visual Studio can use your Azure account to authenticate and access Azure Resources with.</span></span>  <span data-ttu-id="20035-115">Bu hesap, uygulamaları doğrudan Visual Studio 'dan Azure 'a yayımladığınızda de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20035-115">This account is also used when you publish apps directly from Visual Studio to Azure.</span></span>

<span data-ttu-id="20035-116">Azure hesabınızın kimliğini Visual Studio 'dan doğrulamak için,   >  **Seçenekler** iletişim kutusunu başlatmak üzere Araçlar **Seçenekler** menüsünü seçin.</span><span class="sxs-lookup"><span data-stu-id="20035-116">To authenticate your Azure account from Visual Studio, select the **Tools** > **Options** menu to launch the **Options** dialog.</span></span> <span data-ttu-id="20035-117">`Azure Service Authentication`Seçeneklere gidin ve Azure hesabınızı kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="20035-117">Navigate to the `Azure Service Authentication` options and sign in using your Azure account.</span></span>

![Azure oturum açma bilgilerini gösteren Visual Studio seçenekleri Iletişim kutusunun ekran görüntüsü](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a><span data-ttu-id="20035-119">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="20035-119">Next steps</span></span>

<span data-ttu-id="20035-120">.NET veya diğer dillerde geliştirme için [Visual Studio Code](https://code.visualstudio.com/) de kullanıyorsanız, [Azure geliştirmesi için Visual Studio Code de yapılandırmanız](./configure-vs-code.md)gerekir.</span><span class="sxs-lookup"><span data-stu-id="20035-120">If you also use [Visual Studio Code](https://code.visualstudio.com/) for development in .NET or any other language, you should also [configure Visual Studio Code for Azure development](./configure-vs-code.md).</span></span> <span data-ttu-id="20035-121">Aksi takdirde, [Azure CLI 'Yı yüklemeye](./install-azure-cli.md)devam edin.</span><span class="sxs-lookup"><span data-stu-id="20035-121">Otherwise, proceed to [Installing the Azure CLI](./install-azure-cli.md).</span></span>
