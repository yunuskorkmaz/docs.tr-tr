---
title: .NET ile Azure geliştirme için Visual Studio Code yapılandırma
description: Bu makale, VS Code ' de yüklü ve yapılandırılmış doğru eklentilerin alınması dahil olmak üzere Azure geliştirme için Visual Studio Code yapılandırmanıza yardımcı olur
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701214"
---
# <a name="configure-visual-studio-code-for-azure-development"></a><span data-ttu-id="e1879-103">Azure geliştirme için Visual Studio Code yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1879-103">Configure Visual Studio Code for Azure development</span></span>

<span data-ttu-id="e1879-104">.NET geliştirmesi için Visual Studio Code kullanıyorsanız, angular, yanıt verme veya Vue gibi çerçeveleri kullanarak tek sayfalı uygulamalar oluşturmaya veya Python gibi başka bir dilde uygulama yazmaya yönelik olarak Azure geliştirme için Visual Studio Code yapılandırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e1879-104">If you are using Visual Studio Code, whether for .NET development, for building single page applications using frameworks like Angular, React or Vue, or for writing applications in another language like Python, you will want to configure Visual Studio Code for Azure development.</span></span>

### <a name="download-visual-studio-code"></a><span data-ttu-id="e1879-105">Visual Studio Code'u indirin</span><span class="sxs-lookup"><span data-stu-id="e1879-105">Download Visual Studio Code</span></span>

<span data-ttu-id="e1879-106">Zaten Visual Studio Code yüklüyse, bu adımı atlayabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e1879-106">If you already have Visual Studio Code installed, you can skip this step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1879-107">Visual Studio Code'u indirin</span><span class="sxs-lookup"><span data-stu-id="e1879-107">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a><span data-ttu-id="e1879-108">Azure araçları uzantı paketini yükler</span><span class="sxs-lookup"><span data-stu-id="e1879-108">Install the Azure Tools Extension Pack</span></span>

<span data-ttu-id="e1879-109">[Azure araçları uzantı paketi](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) , tek bir kullanışlı pakette Azure App Service, Azure Işlevleri, Azure depolama, Cosmos DB ve Azure sanal makineleri ile çalışmaya yönelik uzantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e1879-109">The [Azure Tools Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines all in one convenient package.</span></span>

<span data-ttu-id="e1879-110">Uzantıyı Visual Studio Code yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="e1879-110">To install the extension from Visual Studio Code:</span></span>

1. <span data-ttu-id="e1879-111">**Uzantılar** penceresini açmak için <kbd>CTRL + SHIFT + X</kbd> tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e1879-111">Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.</span></span>
1. <span data-ttu-id="e1879-112">*Azure Araçları* uzantısını arayın.</span><span class="sxs-lookup"><span data-stu-id="e1879-112">Search for the *Azure Tools* extension.</span></span>
1. <span data-ttu-id="e1879-113">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e1879-113">Select the **Install** button.</span></span>

![Azure araçları uzantı paketi için arama uzantıları paneli 'ni gösteren Visual Studio Code ekran görüntüsü](./media/visual-studio-code-azure-tools.png)

<span data-ttu-id="e1879-115">Visual Studio Code Uzantıları yükleme hakkında daha fazla bilgi edinmek için Visual Studio Code Web sitesindeki [uzantı marketi](https://code.visualstudio.com/docs/editor/extension-gallery) belgesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e1879-115">To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.</span></span>

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a><span data-ttu-id="e1879-116">Azure Araçları 'nı kullanarak Azure hesabınızda oturum açın</span><span class="sxs-lookup"><span data-stu-id="e1879-116">Sign in to your Azure account with Azure Tools</span></span>

<span data-ttu-id="e1879-117">Sol bölmede bir Azure simgesi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e1879-117">On the left hand panel, you'll see an Azure icon.</span></span> <span data-ttu-id="e1879-118">Bu simgeyi seçin ve Azure hizmetleri için bir denetim masası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e1879-118">Select this icon, and a control panel for Azure services will appear.</span></span> <span data-ttu-id="e1879-119">Visual Studio Code ' deki Azure Araçları için kimlik doğrulama işlemini tamamlamaya yönelik herhangi bir hizmette **Azure... oturum aç '** ı seçin.</span><span class="sxs-lookup"><span data-stu-id="e1879-119">Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.</span></span>

![Azure araçlarının Azure 'da nasıl oturum açışını gösteren Visual Studio Code ekran görüntüsü](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a><span data-ttu-id="e1879-121">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e1879-121">Next steps</span></span>

<span data-ttu-id="e1879-122">Daha sonra, Azure CLı 'yi iş istasyonunuza yüklemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e1879-122">Next, you will want to install the Azure CLI on your workstation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1879-123">Azure CLI'yi yükleme</span><span class="sxs-lookup"><span data-stu-id="e1879-123">Install the Azure CLI</span></span>](./install-azure-cli.md)
