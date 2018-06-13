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
ms.openlocfilehash: d321d1585b04a8a22ecc138ceef11630229b1054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490503"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="bc9b3-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="bc9b3-102">Integrating with COM+ Applications</span></span>
<span data-ttu-id="bc9b3-103">Windows Communication Foundation (WCF) dağıtılmış uygulamaları oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-103">Windows Communication Foundation (WCF) provides a rich environment for creating distributed applications.</span></span> <span data-ttu-id="bc9b3-104">COM + barındırılan bir bileşen tabanlı uygulama mantığı önemli ölçüde yatırımınız varsa, onu yeniden yazmaya gerek yerine mevcut mantığınızı genişletmek için WCF kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-104">If you have a substantial investment in component-based application logic hosted in COM+, you can use WCF to extend your existing logic rather than having to rewrite it.</span></span> <span data-ttu-id="bc9b3-105">Bu bölüm içindeki konuları COM + WCF ile nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-105">The topics within this section describe how to use COM+ with WCF.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc9b3-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc9b3-106">In This Section</span></span>  
 [<span data-ttu-id="bc9b3-107">COM+ Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc9b3-107">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 <span data-ttu-id="bc9b3-108">COM + bileşenleri bütünleştirmek nasıl ve ne zaman bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-108">Gives an overview of when and how to integrate COM+ components.</span></span>  
  
 [<span data-ttu-id="bc9b3-109">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc9b3-109">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)  
 <span data-ttu-id="bc9b3-110">COM + hizmet modeli yapılandırma komut satırı aracı (ComSvcConfig.exe) WCF hizmetleri sunulan istediğiniz uygulama arabirimleri yapılandırmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-110">Explains how to use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that you want exposed as WCF services.</span></span>  
  
 [<span data-ttu-id="bc9b3-111">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc9b3-111">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 <span data-ttu-id="bc9b3-112">WCF hizmet olarak bir COM + nesnesi yapılandırmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-112">Explains how to configure a COM+ object as a WCF service.</span></span>  
  
 [<span data-ttu-id="bc9b3-113">Nasıl Yapılır: COM+ Tümleştirme Uygulaması Dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc9b3-113">How to: Deploy a COM+ Integration Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-deploy-a-com-integration-application.md)  
 <span data-ttu-id="bc9b3-114">COM + tümleştirme uygulaması taşınacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-114">Explains how to move a COM+ integration application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bc9b3-115">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bc9b3-115">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="bc9b3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc9b3-116">See Also</span></span>  
 [<span data-ttu-id="bc9b3-117">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="bc9b3-117">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
