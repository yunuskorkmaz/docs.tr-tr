---
title: Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631841"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="1379c-102">Doğrulama verenin adı kaydı paketini indirme</span><span class="sxs-lookup"><span data-stu-id="1379c-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="1379c-103">Bu konuda, indirin ve doğrulama verenin ad kayıt defteri (VINR) projenizde anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1379c-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="1379c-104">VINR, gerekli derlemeleri ve başvuruları projenize ekleyen bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1379c-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="1379c-105">Yüklü olan NuGet zaten yoksa, Git [nuget.org](https://nuget.org) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1379c-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="1379c-106">Kendi sayfasını ziyaret ederek uzantının sürüm geçmişini görebilirsiniz: [Microsoft NuGet üzerindeki yayınlayıcı adı kaydını doğrulama](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="1379c-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="1379c-107">Paket Yöneticisi GUI kullanma</span><span class="sxs-lookup"><span data-stu-id="1379c-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="1379c-108">Visual Studio'da, projenize sağ tıklayın **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="1379c-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="1379c-109">İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `ValidatingIssuerNameRegistry` basın **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1379c-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="1379c-110">Sonuçlar bölmesinde, tıklayın **yükleme** düğmesine ilk sonuç.</span><span class="sxs-lookup"><span data-stu-id="1379c-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="1379c-111">Paketin indirilmesi başlar.</span><span class="sxs-lookup"><span data-stu-id="1379c-111">The package will begin downloading.</span></span> <span data-ttu-id="1379c-112">Projenize eklenmeden önce lisans kabulü iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="1379c-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="1379c-113">Lisans koşullarını kabul ediyorsanız tıklayın **kabul ediyorum**.</span><span class="sxs-lookup"><span data-stu-id="1379c-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="1379c-114">Son VINR derlemeleri indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="1379c-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="1379c-115">Paket Yöneticisi Konsolu</span><span class="sxs-lookup"><span data-stu-id="1379c-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="1379c-116">Visual Studio'da **Araçları** > **NuGet Paket Yöneticisi** > **Paket Yöneticisi Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="1379c-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="1379c-117">**Paket Yöneticisi Konsolu** görünür.</span><span class="sxs-lookup"><span data-stu-id="1379c-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="1379c-118">Aşağıdaki metni ve enter tuşuna basın **Enter**:</span><span class="sxs-lookup"><span data-stu-id="1379c-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="1379c-119">Son VINR derlemeleri indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="1379c-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>
