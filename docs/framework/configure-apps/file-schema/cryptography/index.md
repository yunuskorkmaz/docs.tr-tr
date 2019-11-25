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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088001"
---
# <a name="cryptography-settings-schema"></a>Şifreleme Ayarları Şeması
Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Cryptographyısettings >** ](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoClasses >** ](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry >** ](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oıdmap >** ](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oıdentry >** ](oidentry-element.md)

|Öğe|Açıklama|  
|-------------|-----------------|  
|[**cryptoClasses\<** >](cryptoclasses-element.md)|**\<nameEntry >** öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|**\<nameEntry >** öğesinde kolay bir ad ile eşleşen bir şifreleme sınıfı içerir.|  
|[ **\<Cryptographi settings**>](cryptographysettings-element.md)|Şifreleme ayarlarını içerir.|  
|[**cryptoNameMapping>\<** ](cryptonamemapping-element.md)|Kolay adlarla sınıfların eşlemelerini içerir.|  
|[şifreleme ayarları için **mscorlib > öğesi\<** ](mscorlib-element-for-cryptography-settings.md)|**\<Cryptographyısettings >** öğesini içerir.|  
|[ **\<nameEntry >** ](nameentry-element.md)|Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.|  
|[ **\<Oıdentry >** ](oidentry-element.md)|Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.|  
|[ **\<Oıdmap >** ](oidmap-element.md)|Sınıflara ASN. 1 OID eşlemelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
