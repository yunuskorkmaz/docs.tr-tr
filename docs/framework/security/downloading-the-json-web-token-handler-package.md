---
title: "JSON Web Belirteci İşleyicisi Paketini İndirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="a3ebb-102">JSON Web Belirteci İşleyicisi Paketini İndirme</span><span class="sxs-lookup"><span data-stu-id="a3ebb-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="a3ebb-103">Bu konu, indirin ve JSON Web belirteci işleyicisi projenizde nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="a3ebb-104">JSON Web Belirteci İşleyicisini İndirme</span><span class="sxs-lookup"><span data-stu-id="a3ebb-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="a3ebb-105">JSON Web belirteci işleyicisi uzantısı gerekli derlemeler ve başvuruları projenize ekler bir NuGet paketi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="a3ebb-106">Yüklü NuGet zaten yoksa, Git [nuget.org](http://nuget.org) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="a3ebb-107">NuGet üzerinde kendi sayfasını ziyaret ederek uzantısı sürüm geçmişini görebilirsiniz: [NuGet üzerinde JSON Web belirteci işleyicisi](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="a3ebb-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="a3ebb-108">Paket Yöneticisi GUI'sini kullanarak JSON Web belirteci işleyicisi indirme</span><span class="sxs-lookup"><span data-stu-id="a3ebb-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="a3ebb-109">Visual Studio'da, projenize sağ **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="a3ebb-110">İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `JWT Token Handler` ve basın **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="a3ebb-111">Sonuçlar bölmesinde, tıklatın **yüklemek** ilk sonucu düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="a3ebb-112">Paket, karşıdan yükleme başlar.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-112">The package will begin downloading.</span></span> <span data-ttu-id="a3ebb-113">Projenize eklenmeden önce lisans kabulünü iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="a3ebb-114">Lisans koşullarını kabul ediyorsa **kabul ediyorum**.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="a3ebb-115">En son JSON Web belirteci işleyicisi derlemeler indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="a3ebb-116">Paket Yöneticisi konsolu kullanılarak JSON Web belirteci işleyicisi indirme</span><span class="sxs-lookup"><span data-stu-id="a3ebb-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="a3ebb-117">Visual Studio'da sırasıyla **Araçları**, **kitaplık Paket Yöneticisi**ve ardından **Paket Yöneticisi Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="a3ebb-118">**Paket Yöneticisi Konsolu** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="a3ebb-119">Aşağıdaki metin ve ENTER tuşuna basın **Enter**:</span><span class="sxs-lookup"><span data-stu-id="a3ebb-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="a3ebb-120">En son JSON Web belirteci işleyicisi derlemeler indirilir ve projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="a3ebb-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
