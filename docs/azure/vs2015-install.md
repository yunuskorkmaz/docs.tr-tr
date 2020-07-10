---
title: Visual Studio için Azure Araçları 2015
description: Visual Studio 2015 ' den Azure .NET kitaplıklarını kullanmaya başlamak için Araçları alın.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 72229ce0c0276912ddc5658e34f4572a7948a4e6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174952"
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="d2248-103">Visual Studio için Azure Araçları 2015</span><span class="sxs-lookup"><span data-stu-id="d2248-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="d2248-104">**Visual studio 2015 Için Azure SDK 'sını** ve **Visual studio 2015 için Service Fabric SDK ve araçları** yüklemenin en hızlı ve en kolay yolu [Web Platformu Yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx)'ni kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d2248-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="d2248-105">Microsoft Web Platformu Yükleyicisi, Visual Studio 2015 için Azure araçları dahil olmak üzere Microsoft Web Platformu bileşenlerini indirmeyi, yüklemeyi ve güncellemeyi kolaylaştıran ücretsiz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="d2248-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span> <span data-ttu-id="d2248-106">Bu SDK 'lar Ayrıca [Azure İndirmeleri sayfasından](https://azure.microsoft.com/downloads/)ayrı bileşenler olarak indirilip yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d2248-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span>

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="d2248-107">Web Platformu Yükleyicisi 'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="d2248-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="d2248-108">Bu [Web platformu yükleyici Bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)'nı indirip çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2248-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>

2. <span data-ttu-id="d2248-109">Önyükleyici, Web Platformu Yükleyicisi 'ni yükler (gerekirse) ve **Visual studio 2015 Için Azure SDK** 'nın en son sürümlerini ve visual Studio 2015 IÇIN **Service Fabric SDK ve araçlar** 'ı otomatik olarak yerleştirir. *Items to be installed*</span><span class="sxs-lookup"><span data-stu-id="d2248-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span> <span data-ttu-id="d2248-110">**Yükle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2248-110">Click **Install**.</span></span>

    ![Web Platformu Yükleyicisi](media/vs2015-install/webpi.png)

3. <span data-ttu-id="d2248-112">Sonraki ekranda **kabul ediyorum**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2248-112">On the next screen, click **I Accept**.</span></span> <span data-ttu-id="d2248-113">Web PI seçtiğiniz bileşenleri indirmeye ve yüklemeye başlayacak.</span><span class="sxs-lookup"><span data-stu-id="d2248-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="d2248-114">Yükleme tamamlandıktan sonra, bir onay ekranı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2248-114">After the installation is finished, it will display a confirmation screen.</span></span> <span data-ttu-id="d2248-115">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2248-115">Click **Finish**.</span></span> <span data-ttu-id="d2248-116">Artık Web Platformu Yükleyicisi 'ni kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2248-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="d2248-117">Yüklemenin doğrulanması</span><span class="sxs-lookup"><span data-stu-id="d2248-117">Verifying the installation</span></span>

1. <span data-ttu-id="d2248-118">Visual Studio 2015 ' de **Araçlar** menüsüne ve ardından **Uzantılar ve Güncelleştirmeler ' e tıklayın...**</span><span class="sxs-lookup"><span data-stu-id="d2248-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="d2248-119">Görüntülenmiş listede **Microsoft Azure App Service araçları**, **Microsoft Azure depolama bağlı hizmet**ve **Service Fabric araçları**gibi çeşitli Azure araçları yer alacak.</span><span class="sxs-lookup"><span data-stu-id="d2248-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Uzantılar ve güncelleştirmeler](media/vs2015-install/ext-tools.png)
