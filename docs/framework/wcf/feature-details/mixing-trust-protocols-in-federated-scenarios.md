---
title: Federe Senaryolarda Güven Protokollerini Karıştırma
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248181"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="38e84-102">Federe Senaryolarda Güven Protokollerini Karıştırma</span><span class="sxs-lookup"><span data-stu-id="38e84-102">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="38e84-103">Federasyon istemcilerinin bir hizmetle iletişim kurduğu senaryolar ve aynı güven sürümüne sahip olmayan bir güvenlik belirteci hizmeti (STS) olabilir.</span><span class="sxs-lookup"><span data-stu-id="38e84-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="38e84-104">Service WSDL, `RequestSecurityTokenTemplate` STS 'den farklı sürümlerindeki WS-Trust öğeleriyle bir onaylama işlemi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="38e84-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="38e84-105">Böyle durumlarda, bir Windows Communication Foundation (WCF) istemcisi öğesinden alınan WS-Trust öğelerini `RequestSecurityTokenTemplate` STS güven sürümüyle eşleşecek şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="38e84-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="38e84-106">WCF yalnızca standart bağlamalar için eşleşmeyen güven sürümlerini işler.</span><span class="sxs-lookup"><span data-stu-id="38e84-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="38e84-107">WCF tarafından tanınan tüm standart algoritma parametreleri standart bağlamanın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="38e84-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="38e84-108">Bu konuda, hizmet ve STS arasında çeşitli güven ayarlarına sahip WCF davranışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38e84-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="38e84-109">RP Şub 2005 ve STS Şub 2005</span><span class="sxs-lookup"><span data-stu-id="38e84-109">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="38e84-110">Bağlı olan taraf (RP) için WSDL, bölümünde yer alan aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="38e84-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="38e84-111">İstemci yapılandırma dosyası bir parametre listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="38e84-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="38e84-112">WCF, istemci ve hizmet parametrelerini ayırt edemez; tüm parametreleri ekler ve `RequestSecurityTokenTemplate` (RST) içinde gönderir.</span><span class="sxs-lookup"><span data-stu-id="38e84-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="38e84-113">RP güveni 1,3 ve STS güveni 1,3</span><span class="sxs-lookup"><span data-stu-id="38e84-113">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="38e84-114">RP için WSDL, bölümünde yer alan aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="38e84-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="38e84-115">İstemci yapılandırma dosyası, `secondaryParameters` RP tarafından belirtilen parametreleri sarmalayan bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="38e84-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="38e84-116">WCF `EncryptionAlgorithm` , `CanonicalizationAlgorithm` ve öğelerini, `KeyWrapAlgorithm` öğesi içinde mevcutsa, RST altındaki en üst düzey öğeden kaldırır `SecondaryParameters` .</span><span class="sxs-lookup"><span data-stu-id="38e84-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="38e84-117">WCF `SecondaryParameters` öğeyi giden RST değiştirilmemiş olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="38e84-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="38e84-118">RP güveni Şub 2005 ve STS güveni 1,3</span><span class="sxs-lookup"><span data-stu-id="38e84-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="38e84-119">RP için WSDL, bölümünde aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="38e84-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="38e84-120">İstemci yapılandırma dosyası bir parametre listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="38e84-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="38e84-121">WCF, istemci yapılandırma dosyasından hizmet ve istemci parametrelerini ayırt edemez.</span><span class="sxs-lookup"><span data-stu-id="38e84-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="38e84-122">Bu nedenle, WCF tüm parametreleri bir güven sürümü 1,3 ad alanına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="38e84-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="38e84-123">WCF,, `KeyType` `KeySize` ve `TokenType` öğelerini aşağıdaki şekilde işler:</span><span class="sxs-lookup"><span data-stu-id="38e84-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="38e84-124">WSDL 'yi indirin, bağlamayı oluşturun ve `KeyType` `KeySize` `TokenType` RP parametrelerini atayın.</span><span class="sxs-lookup"><span data-stu-id="38e84-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="38e84-125">İstemci yapılandırma dosyası daha sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="38e84-125">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="38e84-126">İstemci artık yapılandırma dosyasındaki herhangi bir parametreyi değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="38e84-126">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="38e84-127">Çalışma zamanı sırasında, WCF, `AdditionalTokenParameters` `KeyType` `KeySize` `TokenType` Bu parametreler yapılandırma dosyası oluşturma sırasında ' de hesaba katılmış olduğundan, istemci yapılandırma dosyasının bölümünde belirtilen tüm parametreleri kopyalar.</span><span class="sxs-lookup"><span data-stu-id="38e84-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="38e84-128">RP güveni 1,3 ve STS güven 2005</span><span class="sxs-lookup"><span data-stu-id="38e84-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="38e84-129">RP için WSDL, bölümünde aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :</span><span class="sxs-lookup"><span data-stu-id="38e84-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="38e84-130">İstemci yapılandırma dosyası, `secondaryParamters` RP tarafından belirtilen parametreleri sarmalayan bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="38e84-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="38e84-131">WCF, bölüm içinde belirtilen tüm parametreleri `SecondaryParameters` en üst düzey RST öğesine kopyalar, ancak bunları 2005 WS-Trust ad alanına dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="38e84-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
