---
title: "COM Uygulamaları ile Tümleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe452b41c39598e237633490d09cd267fda04ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="9129d-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9129d-102">Integrating with COM Applications</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9129d-103">Hizmetleri tümleştirilebilir doğrudan varolan kodunuza kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bilinen adı.</span><span class="sxs-lookup"><span data-stu-id="9129d-103"> services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="9129d-104">Hizmet adının Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9129d-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9129d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9129d-105">In This Section</span></span>  
 [<span data-ttu-id="9129d-106">COM uygulamaları ile tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="9129d-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="9129d-107">Tümleştirme işlemini başlıca parçaları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9129d-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="9129d-108">Nasıl yapılır: kaydetmek ve hizmet bilinen adı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9129d-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="9129d-109">Kullanılacak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bilinen adını COM uygulama içinde gerekli öznitelikli türleri COM ile kaydetme ve COM uygulama ve ad ile gerekli bağlama yapılandırması yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="9129d-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="9129d-110">Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="9129d-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="9129d-111">Formu Web Hizmetleri tanım dili (WSDL) belgenin veya bir WS-MetadataExchange uç noktasından sözleşmede tanımını elde etme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9129d-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="9129d-112">Nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="9129d-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="9129d-113">Nasıl çağrılacağını açıklar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak örnek bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL ad.</span><span class="sxs-lookup"><span data-stu-id="9129d-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="9129d-114">Nasıl yapılır: meta veri değişimi sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="9129d-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="9129d-115">Nasıl çağrılacağını açıklar bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak örnek bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Mex uç nokta belirtir ad.</span><span class="sxs-lookup"><span data-stu-id="9129d-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="9129d-116">Nasıl yapılır: kanal güvenliği kimlik bilgilerini belirtin</span><span class="sxs-lookup"><span data-stu-id="9129d-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="9129d-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet bilinen adı destekler `IChannelCredentials` kanal kimlik bilgilerini belirtmek için alternatif yöntemler çeşitli arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9129d-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9129d-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9129d-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="9129d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9129d-119">See Also</span></span>  
 [<span data-ttu-id="9129d-120">COM + uygulamaları ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="9129d-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
