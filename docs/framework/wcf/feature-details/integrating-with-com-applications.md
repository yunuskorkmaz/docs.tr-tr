---
title: COM Uygulamaları ile Tümleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 8fa802ce20bfde3579258a5d34bc5d7f68aaaea3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657408"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="7ef7f-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7ef7f-102">Integrating with COM Applications</span></span>
<span data-ttu-id="7ef7f-103">Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmeti bilinen adını kullanarak doğrudan mevcut kodunuza tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="7ef7f-104">Hizmet bilinen adı, Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ef7f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7ef7f-105">In This Section</span></span>  
 [<span data-ttu-id="7ef7f-106">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ef7f-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="7ef7f-107">Tümleştirme işlemi ana parçalarını genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="7ef7f-108">Nasıl yapılır: Kaydetme ve hizmet bilinen adı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7ef7f-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="7ef7f-109">WCF hizmet bilinen adını COM uygulaması içinde kullanmak için gerekli öznitelik türleri COM ile kaydetme ve COM uygulaması ve ad gerekli bağlama yapılandırması ile yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="7ef7f-110">Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma</span><span class="sxs-lookup"><span data-stu-id="7ef7f-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="7ef7f-111">Web Hizmetleri tanım dili (WSDL) belgenin veya WS-MetadataExchange uç noktasından biçiminde sözleşme tanımı elde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="7ef7f-112">Nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="7ef7f-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="7ef7f-113">Bir WSDL WCF bilinen adını kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="7ef7f-114">Nasıl yapılır: Meta veri değişimi sözleşmeleriyle hizmet bilinen adı kullanma</span><span class="sxs-lookup"><span data-stu-id="7ef7f-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="7ef7f-115">Mex uç noktasını belirtir bir WCF bilinen adını kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="7ef7f-116">Nasıl yapılır: Kanal güvenliği kimlik bilgilerini belirtin</span><span class="sxs-lookup"><span data-stu-id="7ef7f-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="7ef7f-117">WCF hizmet bilinen adı destekler `IChannelCredentials` kanal kimlik bilgilerini belirtmek için alternatif yöntemler çeşitli arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ef7f-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7ef7f-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="7ef7f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-119">See also</span></span>
- [<span data-ttu-id="7ef7f-120">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7ef7f-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
