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
ms.openlocfilehash: 00b04cc2175f4bb4cc0b74602cd3c26f4a4e342f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705213"
---
# <a name="cryptography-settings-schema"></a>Şifreleme Ayarları Şeması
Şifreleme Ayarları Şeması kolay algoritma adlarını şifreleme algoritmalarını uygulayan sınıflar için eşleme belirten öğeleri içerir.  
  
 [**\<Yapılandırma >**](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [**\<mscorlib>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [**\<cryptographySettings >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [**\<cryptoNameMapping >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [**\<cryptoClasses >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [**\<cryptoClass >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [**\<nameEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [**\<oidMap>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [**\<oidEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.|  
|[**\<cryptoClass**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.|  
|[**\<cryptographySettings**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|Şifreleme ayarlarını içerir.|  
|[**\<cryptoNameMapping**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Sınıf için kolay adlar eşlemeleri içerir.|  
|[**\<mscorlib >** öğesi için şifreleme ayarları](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|İçeren  **\<cryptographySettings >** öğesi.|  
|[**\<nameEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.|  
|[**\<oidEntry >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.|  
|[**\<oidMap>**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|ASN.1 OID eşlemeleri için sınıflar içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Şifreleme Hizmetleri](../../../../../docs/standard/security/cryptographic-services.md)
