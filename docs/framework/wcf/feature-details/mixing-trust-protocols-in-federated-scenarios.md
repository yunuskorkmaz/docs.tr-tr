---
title: Federe Senaryolarda Güven Protokollerini Karıştırma
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030083"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="4f6d3-102">Federe Senaryolarda Güven Protokollerini Karıştırma</span><span class="sxs-lookup"><span data-stu-id="4f6d3-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="4f6d3-103">Aynı güven sürümüne sahip değilseniz, Federasyon istemcileri bir güvenlik belirteci hizmeti (STS) bir hizmet ile iletişim kurmak senaryolar olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="4f6d3-104">WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS farklı sürümlerine, WS-Trust öğelerle onaylama.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="4f6d3-105">Bu gibi durumlarda, alınan WS-Trust öğeleri bir Windows Communication Foundation (WCF) istemci dönüştürür `RequestSecurityTokenTemplate` eşleştirilecek sürüm STS güven.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="4f6d3-106">WCF eşleşmeyen güven sürümleri yalnızca standart bağlamaları için işler.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="4f6d3-107">WCF tarafından tanınan tüm standart algoritma parametreleriyle standart bağlama'nın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="4f6d3-108">Bu konuda, STS ile hizmet arasındaki farklı güven ayarlarla WCF davranışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="4f6d3-109">RP Şubat 2005 ve STS Şubat 2005</span><span class="sxs-lookup"><span data-stu-id="4f6d3-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="4f6d3-110">WSDL için bağlı olan taraf (RP) içinde şu öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="4f6d3-111">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="4f6d3-112">WCF istemci ve hizmet parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (k).</span><span class="sxs-lookup"><span data-stu-id="4f6d3-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="4f6d3-113">RP güven 1.3 ve STS güven 1.3</span><span class="sxs-lookup"><span data-stu-id="4f6d3-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="4f6d3-114">RP için WSDL içinde şu öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="4f6d3-115">İstemci yapılandırma dosyası içeren bir `secondaryParameters` RP tarafından belirtilen parametreler sarmalayan öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="4f6d3-116">WCF kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olması durumunda lk altında en üst düzey öğe öğelerden `SecondaryParameters` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="4f6d3-117">WCF ekler `SecondaryParameters` değiştirilmemiş giden lk öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="4f6d3-118">RP güven Şubat 2005 ve STS güven 1.3</span><span class="sxs-lookup"><span data-stu-id="4f6d3-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="4f6d3-119">RP için WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="4f6d3-120">İstemci yapılandırma dosyası parametrelerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="4f6d3-121">İstemci yapılandırma dosyasından WCF hizmet ve istemci parametreleri arasında ayırt edemez.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="4f6d3-122">Bu nedenle WCF güven 1.3 sürümü olmak şartıyla ad alanı için tüm parametreleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="4f6d3-123">WCF tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="4f6d3-124">WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="4f6d3-125">Ardından, istemci yapılandırma dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="4f6d3-126">İstemci, artık yapılandırma dosyasındaki herhangi bir parametre değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="4f6d3-127">Çalışma zamanı sırasında WCF içinde belirtilen tüm parametreler kopyalar `AdditionalTokenParameters` istemci yapılandırma dosyasının `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma dosyası sırasında tüketici oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="4f6d3-128">RP güven 1.3 ve STS güven Şubat 2005</span><span class="sxs-lookup"><span data-stu-id="4f6d3-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="4f6d3-129">RP için WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="4f6d3-130">İstemci yapılandırma dosyası içeren bir `secondaryParamters` RP tarafından belirtilen parametreler sarmalayan öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="4f6d3-131">WCF kopyalar içinde belirtilen tüm parametreler `SecondaryParameters` en üst düzey lk öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
