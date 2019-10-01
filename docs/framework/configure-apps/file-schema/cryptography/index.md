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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699810"
---
# <a name="cryptography-settings-schema"></a>Şifreleme Ayarları Şeması
Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<Cryptographrivsettings >** ](cryptographysettings-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<Oıdmap >** ](oidmap-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<Oıdentry >** ](oidentry-element.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|**@No__t-1nameEntry >** öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|**@No__t-1nameEntry >** öğesinde kolay bir adla eşleşen bir şifreleme sınıfı içerir.|  
|[ **\<Cryptographrivsettings**>](cryptographysettings-element.md)|Şifreleme ayarlarını içerir.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Kolay adlarla sınıfların eşlemelerini içerir.|  
|[şifreleme ayarları için **\<mscorlib >** öğesi](mscorlib-element-for-cryptography-settings.md)|**@No__t-1Cryptographyısettings >** öğesini içerir.|  
|[ **\<nameEntry >** ](nameentry-element.md)|Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.|  
|[ **\<Oıdentry >** ](oidentry-element.md)|Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.|  
|[ **\<Oıdmap >** ](oidmap-element.md)|Sınıflara ASN. 1 OID eşlemelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
