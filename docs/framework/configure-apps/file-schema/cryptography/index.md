---
title: Şifreleme Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927626"
---
# <a name="cryptography-settings-schema"></a>Şifreleme Ayarları Şeması
Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.  
  
 [ **\<Yapılandırma >** ](../configuration-element.md)  
  
 [ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<Cryptographyısettings >** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses >** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass >** ](cryptoclass-element.md)  
  
 [ **\<nameEntry >** ](nameentry-element.md)  
  
 [ **\<Oıdmap >** ](oidmap-element.md)  
  
 [ **\<Oıdentry >** ](oidentry-element.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|NameEntry > öğesinde kolay bir ada  **\<** eşleme olan şifreleme sınıflarının bir listesini içerir.|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|NameEntry > öğesinde kolay bir ad  **\<** ile eşleşen bir şifreleme sınıfı içerir.|  
|[ **\<Cryptographrivsettings**>](cryptographysettings-element.md)|Şifreleme ayarlarını içerir.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Kolay adlarla sınıfların eşlemelerini içerir.|  
|[şifreleme ayarları için mscorlib > öğesi  **\<** ](mscorlib-element-for-cryptography-settings.md)|Cryptographrivsettings > öğesini içerir.  **\<**|  
|[ **\<nameEntry >** ](nameentry-element.md)|Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.|  
|[ **\<Oıdentry >** ](oidentry-element.md)|Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.|  
|[ **\<Oıdmap >** ](oidmap-element.md)|Sınıflara ASN. 1 OID eşlemelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
