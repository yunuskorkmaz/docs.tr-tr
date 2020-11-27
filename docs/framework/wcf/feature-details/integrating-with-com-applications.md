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
ms.openlocfilehash: bc58e22b64284d66367302d55b5c9554c9ec0d72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268241"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="38509-102">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="38509-102">Integrating with COM Applications</span></span>

<span data-ttu-id="38509-103">Windows Communication Foundation (WCF) Hizmetleri, WCF hizmeti bilinen adı kullanılarak doğrudan mevcut kodunuzla tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="38509-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="38509-104">Hizmet bilinen adı, Office VBA, Visual Basic 6,0 veya Visual C++ 6,0 gibi çok çeşitli COM tabanlı geliştirme ortamlarından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38509-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38509-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="38509-105">In This Section</span></span>  

 [<span data-ttu-id="38509-106">COM Uygulamaları ile Tümleştirme Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38509-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="38509-107">Tümleştirme sürecinin ana bölümlerine genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="38509-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="38509-108">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="38509-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="38509-109">Bir COM uygulamasında WCF hizmeti bilinen adını kullanmak için, gerekli olan türleri COM 'a kaydedin ve COM uygulamasını ve bilinen adı gerekli bağlama yapılandırmasıyla yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="38509-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="38509-110">Nasıl yapılır: Windows Communication Foundation Hizmeti Bilinen Adını Kaydolmadan Kullanma</span><span class="sxs-lookup"><span data-stu-id="38509-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="38509-111">Bir Web Hizmetleri tanım dili (WSDL) belgesi veya WS-MetadataExchange uç noktasından sözleşmenin tanımının nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38509-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="38509-112">Nasıl yapılır: WSDL Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="38509-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="38509-113">WCF WSDL bilinen adı kullanılarak bir WCF örneğinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38509-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="38509-114">Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma</span><span class="sxs-lookup"><span data-stu-id="38509-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="38509-115">Bir MEX uç noktası belirten WCF bilinen adını kullanarak bir WCF örneğinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="38509-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="38509-116">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="38509-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="38509-117">WCF hizmeti bilinen adı, `IChannelCredentials` kanal kimlik bilgilerini belirtmek için bir dizi alternatif yöntemi sağlayan arabirimi destekler.</span><span class="sxs-lookup"><span data-stu-id="38509-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="38509-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="38509-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="38509-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38509-119">See also</span></span>

- [<span data-ttu-id="38509-120">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="38509-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
