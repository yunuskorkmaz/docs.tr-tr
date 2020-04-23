---
title: Visual Studio 2015 için Azure araçları
description: Visual Studio 2015'teki Azure .NET kitaplıklarını kullanmaya başlamak için araçları alın.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071929"
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="c2f4c-103">Visual Studio 2015 için Azure araçları</span><span class="sxs-lookup"><span data-stu-id="c2f4c-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="c2f4c-104">**Visual Studio 2015 için Azure SDK** ve **Service Fabric SDK ve Visual Studio 2015 Araçları** için yüklemenin en hızlı ve en kolay yolu Web Platform [Installer'ı](https://www.microsoft.com/web/downloads/platform.aspx)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="c2f4c-105">Microsoft Web Platform Installer, Visual Studio 2015 için Azure araçları da dahil olmak üzere Microsoft Web Platformu'nun bazı bileşenlerini indirme, yükleme ve güncelleştirmeyi kolaylaştıran ücretsiz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span> <span data-ttu-id="c2f4c-106">Bu [SDK'lar, Azure İndirmeler sayfasından](https://azure.microsoft.com/downloads/)tek tek bileşenler olarak indirilebilir ve yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span>

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="c2f4c-107">Web Platform Yükleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c2f4c-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="c2f4c-108">İndirin ve bu [Web Platformu Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>

2. <span data-ttu-id="c2f4c-109">Bootstrapper Web Platform Installer'ı (gerekirse) yükler ve visual **studio 2015 için Azure SDK'nın** en son sürümlerini ve **Hizmet Kumaşı SDK ve Visual Studio için Araçlar 2015** öğelerini öğelerinize otomatik olarak *yüklenecek öğelere* koyar.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span> <span data-ttu-id="c2f4c-110">**Yükle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-110">Click **Install**.</span></span>

    ![Web Platformu Yükleyicisi](../media/sdk/vs2015-install/webpi.png)

3. <span data-ttu-id="c2f4c-112">Sonraki ekranda Kabul **Ediyorum'u**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-112">On the next screen, click **I Accept**.</span></span> <span data-ttu-id="c2f4c-113">Web PI, seçtiğiniz bileşenleri indirmeye ve yüklemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="c2f4c-114">Yükleme tamamlandıktan sonra bir onay ekranı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-114">After the installation is finished, it will display a confirmation screen.</span></span> <span data-ttu-id="c2f4c-115">**Son**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-115">Click **Finish**.</span></span> <span data-ttu-id="c2f4c-116">Artık Web Platformu Yükleyici'yi kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="c2f4c-117">Yüklemenin doğrulanması</span><span class="sxs-lookup"><span data-stu-id="c2f4c-117">Verifying the installation</span></span>

1. <span data-ttu-id="c2f4c-118">Visual Studio 2015'te **Araçlar** menüsüne tıklayın ve **ardından Uzantılar ve Güncellemeler'i tıklatın...**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="c2f4c-119">Görüntülenen listede **Microsoft Azure Uygulama Hizmet Araçları, Microsoft** **Azure Depolama Bağlantılı Hizmet**ve Hizmet Kumaş **Araçları**gibi çeşitli Azure araçları bulunur.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Uzantılar ve güncellemeler](../media/sdk/vs2015-install/ext-tools.png)
