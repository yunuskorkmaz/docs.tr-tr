---
title: 'Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: b4ae7f730296d54debc1cf2971b61e5700503430
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595433"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="54dbc-102">Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma</span><span class="sxs-lookup"><span data-stu-id="54dbc-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="54dbc-103">Bir COM+ tümleştirme uygulaması yazdıktan sonra, bunu başka bir makineye dağıtmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54dbc-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="54dbc-104">Bu konu, bir COM+ tümleştirme uygulamasının bir makineden diğerine nasıl taşınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="54dbc-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="54dbc-105">COM+ barındırılan tümleştirme uygulamasını taşıma</span><span class="sxs-lookup"><span data-stu-id="54dbc-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="54dbc-106">WCF 'nin her iki makinede de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54dbc-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="54dbc-107">Uygulamayı A makinesinden dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="54dbc-108">Uygulamayı B makinesinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="54dbc-109">Uygulama kök dizini ' ni ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-109">Set the Application Root Directory.</span></span> <span data-ttu-id="54dbc-110">Kurala göre, bu% PROGRAMFILES%/ComPlus Applications/{appGUID}.</span><span class="sxs-lookup"><span data-stu-id="54dbc-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="54dbc-111">Application. config ve Application. manifest dosyalarını A makinesindeki uygulama kök dizininden B makinesindeki uygulama kök dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="54dbc-112">Uygun makineyi belirlemek için B makinesindeki Application. config dosyasında hizmet uç noktası adreslerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="54dbc-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="54dbc-113">Örneğin, olarak değiştirin `http://machineA/MyService` `http://machineB/MyService` .</span><span class="sxs-lookup"><span data-stu-id="54dbc-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="54dbc-114">Web 'de barındırılan tümleştirme uygulamasını taşıma</span><span class="sxs-lookup"><span data-stu-id="54dbc-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="54dbc-115">WCF 'nin her iki makinede de yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54dbc-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="54dbc-116">Uygulamayı A makinesinden dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="54dbc-117">Uygulamayı B makinesinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="54dbc-118">B makinesi üzerinde bir IIS vroot oluşturun.</span><span class="sxs-lookup"><span data-stu-id="54dbc-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="54dbc-119">. Svc dosyasını (componentName. svc) ve Web. config dosyasını A makinesindeki sanal ağ grubundan B makinesinde yeni oluşturulan vroot öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="54dbc-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dbc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54dbc-120">See also</span></span>

- [<span data-ttu-id="54dbc-121">COM+ uygulamaları ile tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="54dbc-121">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="54dbc-122">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="54dbc-122">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="54dbc-123">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="54dbc-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
