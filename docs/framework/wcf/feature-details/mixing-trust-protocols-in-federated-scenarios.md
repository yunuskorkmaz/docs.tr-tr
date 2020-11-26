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
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Federe Senaryolarda Güven Protokollerini Karıştırma

Federasyon istemcilerinin bir hizmetle iletişim kurduğu senaryolar ve aynı güven sürümüne sahip olmayan bir güvenlik belirteci hizmeti (STS) olabilir. Service WSDL, `RequestSecurityTokenTemplate` STS 'den farklı sürümlerindeki WS-Trust öğeleriyle bir onaylama işlemi içerebilir. Böyle durumlarda, bir Windows Communication Foundation (WCF) istemcisi öğesinden alınan WS-Trust öğelerini `RequestSecurityTokenTemplate` STS güven sürümüyle eşleşecek şekilde dönüştürür. WCF yalnızca standart bağlamalar için eşleşmeyen güven sürümlerini işler. WCF tarafından tanınan tüm standart algoritma parametreleri standart bağlamanın bir parçasıdır. Bu konuda, hizmet ve STS arasında çeşitli güven ayarlarına sahip WCF davranışı açıklanmaktadır.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP Şub 2005 ve STS Şub 2005  

 Bağlı olan taraf (RP) için WSDL, bölümünde yer alan aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 İstemci yapılandırma dosyası bir parametre listesi içerir.  
  
 WCF, istemci ve hizmet parametrelerini ayırt edemez; tüm parametreleri ekler ve `RequestSecurityTokenTemplate` (RST) içinde gönderir.  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP güveni 1,3 ve STS güveni 1,3  

 RP için WSDL, bölümünde yer alan aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası, `secondaryParameters` RP tarafından belirtilen parametreleri sarmalayan bir öğesi içerir.  
  
 WCF `EncryptionAlgorithm` , `CanonicalizationAlgorithm` ve öğelerini, `KeyWrapAlgorithm` öğesi içinde mevcutsa, RST altındaki en üst düzey öğeden kaldırır `SecondaryParameters` . WCF `SecondaryParameters` öğeyi giden RST değiştirilmemiş olarak ekler.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP güveni Şub 2005 ve STS güveni 1,3  

 RP için WSDL, bölümünde aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 İstemci yapılandırma dosyası bir parametre listesi içerir.  
  
 WCF, istemci yapılandırma dosyasından hizmet ve istemci parametrelerini ayırt edemez. Bu nedenle, WCF tüm parametreleri bir güven sürümü 1,3 ad alanına dönüştürür.  
  
 WCF,, `KeyType` `KeySize` ve `TokenType` öğelerini aşağıdaki şekilde işler:  
  
- WSDL 'yi indirin, bağlamayı oluşturun ve `KeyType` `KeySize` `TokenType` RP parametrelerini atayın. İstemci yapılandırma dosyası daha sonra oluşturulur.  
  
- İstemci artık yapılandırma dosyasındaki herhangi bir parametreyi değiştirebilir.  
  
- Çalışma zamanı sırasında, WCF, `AdditionalTokenParameters` `KeyType` `KeySize` `TokenType` Bu parametreler yapılandırma dosyası oluşturma sırasında ' de hesaba katılmış olduğundan, istemci yapılandırma dosyasının bölümünde belirtilen tüm parametreleri kopyalar.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP güveni 1,3 ve STS güven 2005  

 RP için WSDL, bölümünde aşağıdaki öğeleri içerir `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 İstemci yapılandırma dosyası, `secondaryParamters` RP tarafından belirtilen parametreleri sarmalayan bir öğesi içerir.  
  
 WCF, bölüm içinde belirtilen tüm parametreleri `SecondaryParameters` en üst düzey RST öğesine kopyalar, ancak bunları 2005 WS-Trust ad alanına dönüştürmez.
