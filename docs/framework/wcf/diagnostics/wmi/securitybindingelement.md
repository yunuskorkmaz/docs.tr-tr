---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975565"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 SecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="defaultalgorithmsuite"></a>defaultAlgorithmSuite  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bağlama ile kullanmak için algoritmalar belirtir.  
  
### <a name="includetimestamp"></a>includeTimestamp  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.  
  
### <a name="keyentropymode"></a>keyEntropyMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Anahtarları oluşturmak için kullanılan entropi kaynağı.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Veri türü: LocalServiceSecuritySettings  
  
 Erişim türü: salt okunur  
  
 Yerel hizmet bağlama belirli güvenlik özelliklerini.  
  
### <a name="messagesecurityversion"></a>messageSecurityVersion  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İleti güvenliği için kullanılan sürümü.  
  
### <a name="securityheaderlayout"></a>securityHeaderLayout  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Güvenlik üst bilgisindeki öğelerin sırasını Bu bağlama için.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
