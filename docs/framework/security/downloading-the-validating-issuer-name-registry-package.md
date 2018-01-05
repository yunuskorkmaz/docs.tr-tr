---
title: "Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="c09bc-102">Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme</span><span class="sxs-lookup"><span data-stu-id="c09bc-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="c09bc-103">Bu konu, indirin ve doğrulama verenin adı kayıt defteri (VINR) projenizde nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c09bc-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="c09bc-104">Doğrulama yayınlayıcı adı kaydını indirme</span><span class="sxs-lookup"><span data-stu-id="c09bc-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="c09bc-105">VINR gerekli derlemeler ve başvuruları projenize ekler bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c09bc-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="c09bc-106">Yüklü NuGet zaten yoksa, Git [nuget.org](http://nuget.org) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="c09bc-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="c09bc-107">NuGet üzerinde kendi sayfasını ziyaret ederek uzantısı sürüm geçmişini görebilirsiniz: [Microsoft doğrulama yayınlayıcı adı kaydını NuGet üzerinde](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="c09bc-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="c09bc-108">Paket Yöneticisi GUI'sini kullanarak doğrulama yayınlayıcı adı kaydını indirme</span><span class="sxs-lookup"><span data-stu-id="c09bc-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="c09bc-109">Visual Studio'da, projenize sağ **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="c09bc-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="c09bc-110">İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `ValidatingIssuerNameRegistry` ve basın **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c09bc-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="c09bc-111">Sonuçlar bölmesinde, tıklatın **yüklemek** ilk sonucu düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c09bc-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="c09bc-112">Paket, karşıdan yükleme başlar.</span><span class="sxs-lookup"><span data-stu-id="c09bc-112">The package will begin downloading.</span></span> <span data-ttu-id="c09bc-113">Projenize eklenmeden önce lisans kabulünü iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c09bc-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="c09bc-114">Lisans koşullarını kabul ediyorsa **kabul ediyorum**.</span><span class="sxs-lookup"><span data-stu-id="c09bc-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="c09bc-115">En son VINR derlemeler indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="c09bc-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="c09bc-116">Paket Yöneticisi konsolunu kullanarak doğrulama yayınlayıcı adı kaydını indirme</span><span class="sxs-lookup"><span data-stu-id="c09bc-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="c09bc-117">Visual Studio'da sırasıyla **Araçları**, **kitaplık Paket Yöneticisi**ve ardından **Paket Yöneticisi Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="c09bc-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="c09bc-118">**Paket Yöneticisi Konsolu** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c09bc-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="c09bc-119">Aşağıdaki metin ve ENTER tuşuna basın **Enter**:</span><span class="sxs-lookup"><span data-stu-id="c09bc-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="c09bc-120">En son VINR derlemeler indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="c09bc-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>
