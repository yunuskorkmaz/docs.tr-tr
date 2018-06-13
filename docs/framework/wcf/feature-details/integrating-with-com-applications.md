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
ms.openlocfilehash: 292892ef572bd63fff055aeed88073573fadb934
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491848"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="7705a-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7705a-102">Integrating with COM Applications</span></span>
<span data-ttu-id="7705a-103">Windows Communication Foundation (WCF) hizmetlerini WCF Hizmeti bilinen adını kullanarak doğrudan varolan kodunuza tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7705a-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="7705a-104">Hizmet adının Office VBA, Visual Basic 6.0 veya Visual C++ 6.0 gibi bir geniş aralığı, COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7705a-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7705a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7705a-105">In This Section</span></span>  
 [<span data-ttu-id="7705a-106">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7705a-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="7705a-107">Tümleştirme işlemini başlıca parçaları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7705a-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="7705a-108">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7705a-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="7705a-109">WCF hizmet bilinen adını COM uygulama içinde kullanmak için gerekli öznitelikli türleri COM ile kaydetme ve COM uygulama ve ad ile gerekli bağlama yapılandırmasını.</span><span class="sxs-lookup"><span data-stu-id="7705a-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="7705a-110">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="7705a-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="7705a-111">Formu Web Hizmetleri tanım dili (WSDL) belgenin veya bir WS-MetadataExchange uç noktasından sözleşmede tanımını elde etme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7705a-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="7705a-112">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7705a-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="7705a-113">Bir WCF WSDL ad kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7705a-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="7705a-114">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7705a-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="7705a-115">Mex uç nokta belirtir WCF bilinen adını kullanarak bir WCF örnek çağrı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7705a-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="7705a-116">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="7705a-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="7705a-117">WCF hizmet adının destekleyen `IChannelCredentials` kanal kimlik bilgilerini belirtmek için alternatif yöntemler çeşitli arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7705a-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7705a-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7705a-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="7705a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7705a-119">See Also</span></span>  
 [<span data-ttu-id="7705a-120">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7705a-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
