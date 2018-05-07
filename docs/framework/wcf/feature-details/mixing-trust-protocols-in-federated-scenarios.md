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
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Federe Senaryolarda Güven Protokollerini Karıştırma
Aynı güven sürümüne sahip değil Federasyon istemciler bir hizmeti ve bir güvenlik belirteci hizmeti (STS) ile iletişim senaryolar olabilir. WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS daha farklı sürümlerini WS-Trust öğeleri onaylama işlemi. Böyle durumlarda, bir Windows Communication Foundation (WCF) istemci alınan WS-Trust öğeleri dönüştürür `RequestSecurityTokenTemplate` eşleşecek şekilde STS sürümü güvenen. WCF eşleşmeyen güven sürümleri yalnızca standart bağlamaları için işler. WCF tarafından tanınan tüm standart algoritma parametreleri standart bağlama bir parçasıdır. Bu konuda hizmeti ve STS arasında çeşitli güven ayarlarla WCF davranışını tanımlar.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Şub 2005 ve STS Şub 2005  
 WSDL için bağlı olan taraf (RP) içinde aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 WCF istemcisi ve hizmeti parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (RST).  
  
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
  
 WCF kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olup olmadığını RST altında en üst düzey öğesi öğelerinden `SecondaryParameters` öğesi. WCF ekler `SecondaryParameters` değiştirilmemiş giden RST öğesi.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP güven Şub 2005 ve STS 1.3 güven  
 RP WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 İstemci yapılandırma dosyasından WCF hizmeti ve istemci parametreleri arasında ayrım. Bu nedenle WCF güven sürüm 1.3 ad alanı için tüm parametreleri dönüştürür.  
  
 WCF tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:  
  
-   WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden. İstemci yapılandırma dosyası sonra oluşturulur.  
  
-   İstemci yapılandırma dosyasındaki herhangi bir parametre artık değiştirebilirsiniz.  
  
-   Çalışma zamanı sırasında WCF içine belirtilen tüm parametreleri kopyalar `AdditionalTokenParameters` istemci yapılandırma dosyasının dışında `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma dosyası sırasında hesaba oluşturma.  
  
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
  
 WCF kopyalar içinde belirtilen tüm parametreleri `SecondaryParameters` en üst düzey RST öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.
