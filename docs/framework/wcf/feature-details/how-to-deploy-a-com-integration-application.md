---
title: 'Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490145"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="8982a-102">Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma</span><span class="sxs-lookup"><span data-stu-id="8982a-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="8982a-103">Bir kez bir COM + tümleştirme uygulaması, başka bir makinede dağıtmak isteyebilirsiniz yazmıştır.</span><span class="sxs-lookup"><span data-stu-id="8982a-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="8982a-104">Bu konuda, bir COM + tümleştirme uygulaması bir makineden diğerine taşımak açıklar.</span><span class="sxs-lookup"><span data-stu-id="8982a-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="8982a-105">Taşıma COM + tümleştirme uygulaması barındırılan</span><span class="sxs-lookup"><span data-stu-id="8982a-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="8982a-106">WCF hem makinelerde yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8982a-106">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="8982a-107">Uygulama makine A'dan dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="8982a-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="8982a-108">B. makinedeki uygulama alma</span><span class="sxs-lookup"><span data-stu-id="8982a-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="8982a-109">Uygulama kök dizini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8982a-109">Set the Application Root Directory.</span></span> <span data-ttu-id="8982a-110">Kurala göre %PROGRAMFILES%/ComPlus uygulamaları budur / {UygulamaGUID'i}.</span><span class="sxs-lookup"><span data-stu-id="8982a-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="8982a-111">Uygulama kök dizini makine a Application.config ve Application.manifest dosyalarını B. makinedeki uygulama kök dizini kopyalayın</span><span class="sxs-lookup"><span data-stu-id="8982a-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="8982a-112">Hizmet uç noktası adresleri uygun makine tanımlamak için B makinede Application.config dosyasında düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="8982a-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="8982a-113">Örneğin, değiştirme http://machineA/MyService için http://machineB/MyService.</span><span class="sxs-lookup"><span data-stu-id="8982a-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="8982a-114">Bir Web barındırılan tümleştirme uygulaması taşıma</span><span class="sxs-lookup"><span data-stu-id="8982a-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="8982a-115">WCF hem makinelerde yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8982a-115">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="8982a-116">Uygulama makine A'dan dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="8982a-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="8982a-117">B. makinedeki uygulama alma</span><span class="sxs-lookup"><span data-stu-id="8982a-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="8982a-118">B. makinesinde IIS vroot oluşturma</span><span class="sxs-lookup"><span data-stu-id="8982a-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="8982a-119">.Svc dosyasını (componentName.svc) ve Web.config dosyasını vroot makine a b makinedeki yeni oluşturulan vroot kopyalayın</span><span class="sxs-lookup"><span data-stu-id="8982a-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8982a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8982a-120">See Also</span></span>  
 [<span data-ttu-id="8982a-121">COM+ Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8982a-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="8982a-122">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8982a-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="8982a-123">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8982a-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
