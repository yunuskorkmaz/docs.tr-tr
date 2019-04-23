---
title: 'Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343388"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="e7553-102">Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma</span><span class="sxs-lookup"><span data-stu-id="e7553-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="e7553-103">Bir kez, başka bir makineye dağıtmak istediğiniz bir COM + tümleştirme uygulaması, yazdınız.</span><span class="sxs-lookup"><span data-stu-id="e7553-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="e7553-104">Bu konu, bir COM + tümleştirme uygulaması bir makineden diğerine taşıyabilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7553-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="e7553-105">Taşıma bir COM + tümleştirme uygulaması barındırılan</span><span class="sxs-lookup"><span data-stu-id="e7553-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="e7553-106">WCF'ın her iki makinelerde yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e7553-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="e7553-107">Makine A'dan uygulamayı dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="e7553-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="e7553-108">B. makinedeki uygulamanın içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="e7553-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="e7553-109">Uygulama kök dizinini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e7553-109">Set the Application Root Directory.</span></span> <span data-ttu-id="e7553-110">Kural olarak, bu %PROGRAMFILES%/ComPlus uygulamaları, / {appGUID}.</span><span class="sxs-lookup"><span data-stu-id="e7553-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="e7553-111">Makine a uygulaması kök dizini Application.config ve Application.manifest dosyaları b makinede uygulamanın kök dizinine kopyalayın</span><span class="sxs-lookup"><span data-stu-id="e7553-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="e7553-112">Hizmet uç noktası adreslerini makineye uygun makineyi tanımlamak için B Application.config dosyasındaki düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e7553-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="e7553-113">Örneğin, değiştirme `http://machineA/MyService` için `http://machineB/MyService`.</span><span class="sxs-lookup"><span data-stu-id="e7553-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="e7553-114">Bir Web barındırılan bir tümleştirme uygulaması taşıma</span><span class="sxs-lookup"><span data-stu-id="e7553-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="e7553-115">WCF'ın her iki makinelerde yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e7553-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="e7553-116">Makine A'dan uygulamayı dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="e7553-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="e7553-117">B. makinedeki uygulamanın içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="e7553-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="e7553-118">B. makinede IIS vroot oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7553-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="e7553-119">.Svc dosyasını (componentName.svc) ve Web.config dosyasını vroot makine a b makinede yeni oluşturulan vroot kopyalayın</span><span class="sxs-lookup"><span data-stu-id="e7553-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7553-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7553-120">See also</span></span>

- [<span data-ttu-id="e7553-121">COM+ Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e7553-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="e7553-122">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7553-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [<span data-ttu-id="e7553-123">Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın</span><span class="sxs-lookup"><span data-stu-id="e7553-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
