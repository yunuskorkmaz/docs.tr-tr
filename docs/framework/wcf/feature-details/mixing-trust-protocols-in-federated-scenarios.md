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
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Federe Senaryolarda Güven Protokollerini Karıştırma
Aynı güven sürümüne sahip değil Federasyon istemciler bir hizmeti ve bir güvenlik belirteci hizmeti (STS) ile iletişim senaryolar olabilir. WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS daha farklı sürümlerini WS-Trust öğeleri onaylama işlemi. Böyle durumlarda, bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci dönüştürür alınan WS-Trust öğeleri `RequestSecurityTokenTemplate` eşleşecek şekilde STS sürümü güvenen. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]yalnızca standart bağlamaları için eşleşmeyen tanıtıcıları güven sürümleri. Tarafından tanınan tüm standart algoritma parametreleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standart bağlama parçasıdır. Bu konuda açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] davranışa çeşitli ayarları hizmeti ve STS arasında güven.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Şub 2005 ve STS Şub 2005  
 WSDL için bağlı olan taraf (RP) içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]İstemci ve hizmeti parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP güven 1.3 ve STS güven 1.3  
 RP WSDL içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası içeren bir `secondaryParameters` RP tarafından belirtilen parametreler sarmalar öğesi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olup olmadığını RST altında en üst düzey öğesi öğelerinden `SecondaryParameters` öğesi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ekler `SecondaryParameters` değiştirilmemiş giden RST öğesi.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP güven Şub 2005 ve STS 1.3 güven  
 RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 İstemci yapılandırma dosyasından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve istemci parametreleri arasında ayrım. Bu nedenle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güven sürüm 1.3 ad alanı için tüm parametreleri dönüştürür.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:  
  
-   WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden. İstemci yapılandırma dosyası sonra oluşturulur.  
  
-   İstemci yapılandırma dosyasındaki herhangi bir parametre artık değiştirebilirsiniz.  
  
-   Çalışma zamanı boyunca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içine belirtilen tüm parametreleri kopyalayan `AdditionalTokenParameters` istemci yapılandırma dosyasının dışında `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma sırasında hesaba Dosya oluşturma.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP güven 1.3 ve STS güven Şub 2005  
 RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası içeren bir `secondaryParamters` RP tarafından belirtilen parametreler sarmalar öğesi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]içinde belirtilen tüm parametreleri kopyalayan `SecondaryParameters` en üst düzey RST öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.
