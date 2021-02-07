---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: COM+ tümleştirme uygulaması dağıtma'
title: 'Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 4bf9e72a631c97f3b791ecd01abb5cb74365772d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734392"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="7102d-103">Nasıl yapılır: COM+ Tümleştirme Uygulaması Dağıtma</span><span class="sxs-lookup"><span data-stu-id="7102d-103">How to: Deploy a COM+ Integration Application</span></span>

<span data-ttu-id="7102d-104">Bir COM+ tümleştirme uygulaması yazdıktan sonra, bunu başka bir makineye dağıtmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7102d-104">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="7102d-105">Bu konu, bir COM+ tümleştirme uygulamasının bir makineden diğerine nasıl taşınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7102d-105">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="7102d-106">COM+ barındırılan tümleştirme uygulamasını taşıma</span><span class="sxs-lookup"><span data-stu-id="7102d-106">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="7102d-107">WCF 'nin her iki makinede de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7102d-107">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="7102d-108">Uygulamayı A makinesinden dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="7102d-108">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="7102d-109">Uygulamayı B makinesinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="7102d-109">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="7102d-110">Uygulama kök dizini ' ni ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7102d-110">Set the Application Root Directory.</span></span> <span data-ttu-id="7102d-111">Kurala göre, bu% PROGRAMFILES%/ComPlus Applications/{appGUID}.</span><span class="sxs-lookup"><span data-stu-id="7102d-111">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="7102d-112">Application.config ve Application. manifest dosyalarını A makinesindeki uygulama kök dizininden B makinesindeki uygulama kök dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7102d-112">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="7102d-113">Uygun makineyi belirlemek için B makinesindeki Application.config dosyasında hizmet uç noktası adreslerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="7102d-113">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="7102d-114">Örneğin, olarak değiştirin `http://machineA/MyService` `http://machineB/MyService` .</span><span class="sxs-lookup"><span data-stu-id="7102d-114">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="7102d-115">Web 'de barındırılan tümleştirme uygulamasını taşıma</span><span class="sxs-lookup"><span data-stu-id="7102d-115">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="7102d-116">WCF 'nin her iki makinede de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7102d-116">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="7102d-117">Uygulamayı A makinesinden dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="7102d-117">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="7102d-118">Uygulamayı B makinesinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="7102d-118">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="7102d-119">B makinesi üzerinde bir IIS vroot oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7102d-119">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="7102d-120">. Svc dosyasını (componentName. svc) ve Web.config dosyasını A makinesindeki sanal gruptan B makinesinde yeni oluşturulan vroot öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7102d-120">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7102d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7102d-121">See also</span></span>

- [<span data-ttu-id="7102d-122">COM+ uygulamaları ile tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="7102d-122">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="7102d-123">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7102d-123">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="7102d-124">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7102d-124">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
