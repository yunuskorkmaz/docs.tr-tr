---
title: COM Uygulamaları ile Tümleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, reusing code
- Windows Communication Foundation, reusing code
- Windows Communication Foundation, COM+ integration
- COM+ [WCF], Windows Communication Foundation integration
- COM+ [WCF]
- WCF, COM+ integration
ms.assetid: 98bf7dc4-d49a-4129-a59b-db7a7ec8c241
ms.openlocfilehash: cd72265fe8e49c7def91ebbf05ad84618dd71d19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046937"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="6ac3d-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6ac3d-102">Integrating with COM+ Applications</span></span>
<span data-ttu-id="6ac3d-103">Windows Communication Foundation (WCF) dağıtılmış uygulamalar oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-103">Windows Communication Foundation (WCF) provides a rich environment for creating distributed applications.</span></span> <span data-ttu-id="6ac3d-104">COM +'da barındırılan bir bileşen tabanlı uygulama mantığı önemli ölçüde yatırımınız varsa, WCF, yeniden yazmak zorunda kalmadan yerine mevcut mantığınızı genişletmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-104">If you have a substantial investment in component-based application logic hosted in COM+, you can use WCF to extend your existing logic rather than having to rewrite it.</span></span> <span data-ttu-id="6ac3d-105">Bu bölüm içindeki konuları COM + ile WCF nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-105">The topics within this section describe how to use COM+ with WCF.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ac3d-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ac3d-106">In This Section</span></span>  
 [<span data-ttu-id="6ac3d-107">COM+ Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6ac3d-107">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 <span data-ttu-id="6ac3d-108">Ne zaman ve nasıl tümleştireceğinizi COM + bileşenleri hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-108">Gives an overview of when and how to integrate COM+ components.</span></span>  
  
 [<span data-ttu-id="6ac3d-109">Nasıl yapılır: COM + hizmet modeli yapılandırma aracı kullanın</span><span class="sxs-lookup"><span data-stu-id="6ac3d-109">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)  
 <span data-ttu-id="6ac3d-110">COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe), WCF hizmetleri kullanıma sunulan istediğiniz uygulama arabirimi yapılandırmak için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-110">Explains how to use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that you want exposed as WCF services.</span></span>  
  
 [<span data-ttu-id="6ac3d-111">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ac3d-111">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 <span data-ttu-id="6ac3d-112">Bir WCF hizmeti olarak bir COM nesnesi yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-112">Explains how to configure a COM+ object as a WCF service.</span></span>  
  
 [<span data-ttu-id="6ac3d-113">Nasıl yapılır: COM + tümleştirme uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="6ac3d-113">How to: Deploy a COM+ Integration Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-deploy-a-com-integration-application.md)  
 <span data-ttu-id="6ac3d-114">COM + tümleştirme uygulaması taşınacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-114">Explains how to move a COM+ integration application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ac3d-115">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6ac3d-115">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="6ac3d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ac3d-116">See also</span></span>

- [<span data-ttu-id="6ac3d-117">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="6ac3d-117">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
