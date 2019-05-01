---
title: Federe Senaryolarda Güven Protokollerini Karıştırma
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: ce5c3a1875d84d98068dcc78d8346a88bc0b28f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046698"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Federe Senaryolarda Güven Protokollerini Karıştırma
Aynı güven sürümüne sahip değilseniz, Federasyon istemcileri bir güvenlik belirteci hizmeti (STS) bir hizmet ile iletişim kurmak senaryolar olabilir. WSDL içerebilir hizmeti bir `RequestSecurityTokenTemplate` STS farklı sürümlerine, WS-Trust öğelerle onaylama. Bu gibi durumlarda, alınan WS-Trust öğeleri bir Windows Communication Foundation (WCF) istemci dönüştürür `RequestSecurityTokenTemplate` eşleştirilecek sürüm STS güven. WCF eşleşmeyen güven sürümleri yalnızca standart bağlamaları için işler. WCF tarafından tanınan tüm standart algoritma parametreleriyle standart bağlama'nın bir parçasıdır. Bu konuda, STS ile hizmet arasındaki farklı güven ayarlarla WCF davranışı açıklanmaktadır.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Şubat 2005 ve STS Şubat 2005  
 WSDL için bağlı olan taraf (RP) içinde şu öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 WCF istemci ve hizmet parametreleri arasında ayrım; tüm parametreleri ekler ve bunları gönderir `RequestSecurityTokenTemplate` (k).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP güven 1.3 ve STS güven 1.3  
 RP için WSDL içinde şu öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası içeren bir `secondaryParameters` RP tarafından belirtilen parametreler sarmalayan öğesi.  
  
 WCF kaldırır `EncryptionAlgorithm`, `CanonicalizationAlgorithm` ve `KeyWrapAlgorithm` bunlar içinde mevcut olması durumunda lk altında en üst düzey öğe öğelerden `SecondaryParameters` öğesi. WCF ekler `SecondaryParameters` değiştirilmemiş giden lk öğesi.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP güven Şubat 2005 ve STS güven 1.3  
 RP için WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 İstemci yapılandırma dosyası parametrelerinin listesini içerir.  
  
 İstemci yapılandırma dosyasından WCF hizmet ve istemci parametreleri arasında ayırt edemez. Bu nedenle WCF güven 1.3 sürümü olmak şartıyla ad alanı için tüm parametreleri dönüştürür.  
  
 WCF tanıtıcıları `KeyType`, `KeySize`, ve `TokenType` aşağıdaki gibi öğeleri:  
  
- WSDL indirin, bağlama oluşturmak ve atamak `KeyType`, `KeySize`, ve `TokenType` RP parametrelerinden. Ardından, istemci yapılandırma dosyası oluşturulur.  
  
- İstemci, artık yapılandırma dosyasındaki herhangi bir parametre değiştirebilirsiniz.  
  
- Çalışma zamanı sırasında WCF içinde belirtilen tüm parametreler kopyalar `AdditionalTokenParameters` istemci yapılandırma dosyasının `KeyType`, `KeySize` ve `TokenType`, bu parametreler için yapılandırma dosyası sırasında tüketici oluşturma.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP güven 1.3 ve STS güven Şubat 2005  
 RP için WSDL aşağıdaki öğeleri içeren `RequestSecurityTokenTemplate` bölümü:  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası içeren bir `secondaryParamters` RP tarafından belirtilen parametreler sarmalayan öğesi.  
  
 WCF kopyalar içinde belirtilen tüm parametreler `SecondaryParameters` en üst düzey lk öğesi bölümüne ancak bunları 2005 WS-Trust ad alanına dönüştürmez.
