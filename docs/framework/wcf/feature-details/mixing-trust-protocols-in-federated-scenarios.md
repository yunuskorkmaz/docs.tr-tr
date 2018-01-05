---
title: "Federe Senaryolarda Güven Protokollerini Karıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="2b2bc-102">Federe Senaryolarda Güven Protokollerini Karıştırma</span><span class="sxs-lookup"><span data-stu-id="2b2bc-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="2b2bc-103">Aynı güven sürümüne sahip değil Federasyon istemciler bir hizmeti ve bir güvenlik belirteci hizmeti (STS) ile iletişim senaryolar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="2b2bc-104">WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS daha farklı sürümlerini WS-Trust öğeleri onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="2b2bc-105">Böyle durumlarda, bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci dönüştürür alınan WS-Trust öğeleri `RequestSecurityTokenTemplate` eşleşecek şekilde STS sürümü güvenen.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-106">yalnızca standart bağlamaları için eşleşmeyen tanıtıcıları güven sürümleri.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="2b2bc-107">Tarafından tanınan tüm standart algoritma parametreleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standart bağlama parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="2b2bc-108">Bu konuda açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] davranışa çeşitli ayarları hizmeti ve STS arasında güven.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="2b2bc-109">RP Şub 2005 ve STS Şub 2005</span><span class="sxs-lookup"><span data-stu-id="2b2bc-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="2b2bc-110">WSDL için bağlı olan taraf (RP) içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="2b2bc-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="2b2bc-111">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-112">İstemci ve hizmeti parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="2b2bc-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="2b2bc-113">RP güven 1.3 ve STS güven 1.3</span><span class="sxs-lookup"><span data-stu-id="2b2bc-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="2b2bc-114">RP WSDL içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="2b2bc-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2b2bc-115">İstemci yapılandırma dosyası içeren bir `secondaryParameters` RP tarafından belirtilen parametreler sarmalar öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-116">kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olup olmadığını RST altında en üst düzey öğesi öğelerinden `SecondaryParameters` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-117">ekler `SecondaryParameters` değiştirilmemiş giden RST öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="2b2bc-118">RP güven Şub 2005 ve STS 1.3 güven</span><span class="sxs-lookup"><span data-stu-id="2b2bc-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="2b2bc-119">RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="2b2bc-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="2b2bc-120">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="2b2bc-121">İstemci yapılandırma dosyasından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve istemci parametreleri arasında ayrım.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="2b2bc-122">Bu nedenle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güven sürüm 1.3 ad alanı için tüm parametreleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-123">tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:</span><span class="sxs-lookup"><span data-stu-id="2b2bc-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="2b2bc-124">WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="2b2bc-125">İstemci yapılandırma dosyası sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="2b2bc-126">İstemci yapılandırma dosyasındaki herhangi bir parametre artık değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="2b2bc-127">Çalışma zamanı boyunca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içine belirtilen tüm parametreleri kopyalayan `AdditionalTokenParameters` istemci yapılandırma dosyasının dışında `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma sırasında hesaba Dosya oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="2b2bc-128">RP güven 1.3 ve STS güven Şub 2005</span><span class="sxs-lookup"><span data-stu-id="2b2bc-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="2b2bc-129">RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="2b2bc-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2b2bc-130">İstemci yapılandırma dosyası içeren bir `secondaryParamters` RP tarafından belirtilen parametreler sarmalar öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2b2bc-131">içinde belirtilen tüm parametreleri kopyalayan `SecondaryParameters` en üst düzey RST öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="2b2bc-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
