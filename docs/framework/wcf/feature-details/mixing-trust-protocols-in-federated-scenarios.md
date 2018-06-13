---
title: Federe Senaryolarda Güven Protokollerini Karıştırma
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494475"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="0392f-102">Federe Senaryolarda Güven Protokollerini Karıştırma</span><span class="sxs-lookup"><span data-stu-id="0392f-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="0392f-103">Aynı güven sürümüne sahip değil Federasyon istemciler bir hizmeti ve bir güvenlik belirteci hizmeti (STS) ile iletişim senaryolar olabilir.</span><span class="sxs-lookup"><span data-stu-id="0392f-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="0392f-104">WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS daha farklı sürümlerini WS-Trust öğeleri onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="0392f-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="0392f-105">Böyle durumlarda, bir Windows Communication Foundation (WCF) istemci alınan WS-Trust öğeleri dönüştürür `RequestSecurityTokenTemplate` eşleşecek şekilde STS sürümü güvenen.</span><span class="sxs-lookup"><span data-stu-id="0392f-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="0392f-106">WCF eşleşmeyen güven sürümleri yalnızca standart bağlamaları için işler.</span><span class="sxs-lookup"><span data-stu-id="0392f-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="0392f-107">WCF tarafından tanınan tüm standart algoritma parametreleri standart bağlama bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0392f-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="0392f-108">Bu konuda hizmeti ve STS arasında çeşitli güven ayarlarla WCF davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0392f-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="0392f-109">RP Şub 2005 ve STS Şub 2005</span><span class="sxs-lookup"><span data-stu-id="0392f-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="0392f-110">WSDL için bağlı olan taraf (RP) içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="0392f-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="0392f-111">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0392f-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="0392f-112">WCF istemcisi ve hizmeti parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="0392f-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="0392f-113">RP güven 1.3 ve STS güven 1.3</span><span class="sxs-lookup"><span data-stu-id="0392f-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="0392f-114">RP WSDL içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="0392f-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="0392f-115">İstemci yapılandırma dosyası içeren bir `secondaryParameters` RP tarafından belirtilen parametreler sarmalar öğesi.</span><span class="sxs-lookup"><span data-stu-id="0392f-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="0392f-116">WCF kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olup olmadığını RST altında en üst düzey öğesi öğelerinden `SecondaryParameters` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0392f-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="0392f-117">WCF ekler `SecondaryParameters` değiştirilmemiş giden RST öğesi.</span><span class="sxs-lookup"><span data-stu-id="0392f-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="0392f-118">RP güven Şub 2005 ve STS 1.3 güven</span><span class="sxs-lookup"><span data-stu-id="0392f-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="0392f-119">RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="0392f-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="0392f-120">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0392f-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="0392f-121">İstemci yapılandırma dosyasından WCF hizmeti ve istemci parametreleri arasında ayrım.</span><span class="sxs-lookup"><span data-stu-id="0392f-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="0392f-122">Bu nedenle WCF güven sürüm 1.3 ad alanı için tüm parametreleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0392f-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="0392f-123">WCF tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:</span><span class="sxs-lookup"><span data-stu-id="0392f-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="0392f-124">WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden.</span><span class="sxs-lookup"><span data-stu-id="0392f-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="0392f-125">İstemci yapılandırma dosyası sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0392f-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="0392f-126">İstemci yapılandırma dosyasındaki herhangi bir parametre artık değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0392f-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="0392f-127">Çalışma zamanı sırasında WCF içine belirtilen tüm parametreleri kopyalar `AdditionalTokenParameters` istemci yapılandırma dosyasının dışında `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma dosyası sırasında hesaba oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0392f-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="0392f-128">RP güven 1.3 ve STS güven Şub 2005</span><span class="sxs-lookup"><span data-stu-id="0392f-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="0392f-129">RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="0392f-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="0392f-130">İstemci yapılandırma dosyası içeren bir `secondaryParamters` RP tarafından belirtilen parametreler sarmalar öğesi.</span><span class="sxs-lookup"><span data-stu-id="0392f-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="0392f-131">WCF kopyalar içinde belirtilen tüm parametreleri `SecondaryParameters` en üst düzey RST öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="0392f-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
