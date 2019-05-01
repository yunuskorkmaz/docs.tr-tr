---
title: JSON Web Belirteci İşleyicisi Paketini İndirme
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792762"
---
# <a name="download-the-json-web-token-handler-package"></a><span data-ttu-id="559ee-102">JSON Web belirteci işleyicisi paketini indirme</span><span class="sxs-lookup"><span data-stu-id="559ee-102">Download the JSON Web Token Handler Package</span></span>

<span data-ttu-id="559ee-103">Bu konuda, indirin ve JSON Web belirteci işleyicisi projenizde anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="559ee-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>

<span data-ttu-id="559ee-104">JSON Web belirteci işleyicisi uzantısı, gerekli derlemeleri ve başvuruları projenize ekleyen bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="559ee-104">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="559ee-105">Yüklü olan NuGet zaten yoksa, Git [nuget.org](https://nuget.org) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="559ee-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="559ee-106">Kendi sayfasını ziyaret ederek uzantının sürüm geçmişini görebilirsiniz: [NuGet üzerinde JSON Web belirteci işleyicisi](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="559ee-106">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="559ee-107">Paket Yöneticisi GUI kullanma</span><span class="sxs-lookup"><span data-stu-id="559ee-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="559ee-108">Visual Studio'da, projenize sağ tıklayın **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="559ee-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="559ee-109">İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `JWT Token Handler` basın **Enter**.</span><span class="sxs-lookup"><span data-stu-id="559ee-109">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>

3. <span data-ttu-id="559ee-110">Sonuçlar bölmesinde, tıklayın **yükleme** düğmesine ilk sonuç.</span><span class="sxs-lookup"><span data-stu-id="559ee-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="559ee-111">Paketin indirilmesi başlar.</span><span class="sxs-lookup"><span data-stu-id="559ee-111">The package will begin downloading.</span></span> <span data-ttu-id="559ee-112">Projenize eklenmeden önce lisans kabulü iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="559ee-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="559ee-113">Lisans koşullarını kabul ediyorsanız tıklayın **kabul ediyorum**.</span><span class="sxs-lookup"><span data-stu-id="559ee-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="559ee-114">Son JSON Web belirteci işleyici derlemeleri indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="559ee-114">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="559ee-115">Paket Yöneticisi Konsolu</span><span class="sxs-lookup"><span data-stu-id="559ee-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="559ee-116">Visual Studio'da **Araçları** > **NuGet Paket Yöneticisi** > **Paket Yöneticisi Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="559ee-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="559ee-117">**Paket Yöneticisi Konsolu** görünür.</span><span class="sxs-lookup"><span data-stu-id="559ee-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="559ee-118">Aşağıdaki metni ve enter tuşuna basın **Enter**:</span><span class="sxs-lookup"><span data-stu-id="559ee-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. <span data-ttu-id="559ee-119">Son JSON Web belirteci işleyici derlemeleri indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="559ee-119">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>