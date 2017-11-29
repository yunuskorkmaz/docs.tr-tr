---
title: "Bir WCF Kitaplık Projesini Dağıtma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04567b0b06ef5c8f105e866e150bfaa221d64057
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="d40d5-102">Bir WCF Kitaplık Projesini Dağıtma</span><span class="sxs-lookup"><span data-stu-id="d40d5-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="d40d5-103">Bu konuda, nasıl dağıtılacağı açıklanmaktadır bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="d40d5-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="d40d5-104">Bir WCF Hizmeti kitaplığı dağıtma</span><span class="sxs-lookup"><span data-stu-id="d40d5-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="d40d5-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığıdır dinamik bağlantı kitaplığı (DLL).</span><span class="sxs-lookup"><span data-stu-id="d40d5-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="d40d5-106">Bu nedenle, bu, kendi yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="d40d5-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="d40d5-107">Bir barındırma ortamına dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d40d5-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="d40d5-108">Bu işlem hakkında daha fazla bilgi için bkz: [barındırma ve WCF hizmetlerini tüketen](http://go.microsoft.com/fwlink/?LinkId=99932).</span><span class="sxs-lookup"><span data-stu-id="d40d5-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="d40d5-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı gibi diğer dağıtılabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="d40d5-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="d40d5-110">Ancak, farkında olması, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırmasını DLL'ler için desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d40d5-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="d40d5-111"><xref:System.Configuration>uygulama etki alanı başına bir yapılandırma dosyası destekler.</span><span class="sxs-lookup"><span data-stu-id="d40d5-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="d40d5-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet kitaplığı projesi, geliştirme sırasında bir App.config dosyası kitaplığın sağlayarak bu sınırlamaya ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d40d5-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="d40d5-113">Ancak, App.config dosyasını dağıtımdan sonra tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="d40d5-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="d40d5-114">Barındırma ortamı tarafından tanınan yapılandırma dosyasına yapılandırma kodunuzu taşıyın gerekir.</span><span class="sxs-lookup"><span data-stu-id="d40d5-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="d40d5-115">Kendi kendine barındırma için barındırma yürütülebilir App.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d40d5-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="d40d5-116">Hizmetinizi barındırmak için IIS kullanıyorsanız, sanal dizin Web.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d40d5-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
