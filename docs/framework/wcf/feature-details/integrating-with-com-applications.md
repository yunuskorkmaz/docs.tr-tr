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
ms.openlocfilehash: 51626da6e97e346f43cfe606a5164024580a2ac7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155330"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="027c4-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="027c4-102">Integrating with COM Applications</span></span>
<span data-ttu-id="027c4-103">Windows Communication Foundation (WCF) Hizmetleri, WCF Hizmeti bilinen adını kullanarak doğrudan mevcut kodunuza tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="027c4-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="027c4-104">Hizmet bilinen adı, Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="027c4-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="027c4-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="027c4-105">In This Section</span></span>  
 [<span data-ttu-id="027c4-106">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="027c4-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="027c4-107">Tümleştirme işlemi ana parçalarını genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="027c4-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="027c4-108">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="027c4-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="027c4-109">WCF hizmet bilinen adını COM uygulaması içinde kullanmak için gerekli öznitelik türleri COM ile kaydetme ve COM uygulaması ve ad gerekli bağlama yapılandırması ile yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="027c4-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="027c4-110">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="027c4-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="027c4-111">Web Hizmetleri tanım dili (WSDL) belgenin veya WS-MetadataExchange uç noktasından biçiminde sözleşme tanımı elde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="027c4-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="027c4-112">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="027c4-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="027c4-113">Bir WSDL WCF bilinen adını kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="027c4-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="027c4-114">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="027c4-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="027c4-115">Mex uç noktasını belirtir bir WCF bilinen adını kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="027c4-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="027c4-116">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="027c4-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="027c4-117">WCF hizmet bilinen adı destekler `IChannelCredentials` kanal kimlik bilgilerini belirtmek için alternatif yöntemler çeşitli arabirimi.</span><span class="sxs-lookup"><span data-stu-id="027c4-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="027c4-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="027c4-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="027c4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="027c4-119">See also</span></span>

- [<span data-ttu-id="027c4-120">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="027c4-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
