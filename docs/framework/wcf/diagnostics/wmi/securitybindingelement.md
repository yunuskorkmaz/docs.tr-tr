---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ceb674ea7c20386acb821d3a41c1ad0c743a7607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 SecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bağlama ile birlikte kullanılacak algoritmaları belirler.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Anahtarlar oluşturmak için kullanılan entropi kaynağı.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Veri türü: LocalServiceSecuritySettings  
  
 Erişim türüne: salt okunur  
  
 Yerel hizmet bağlama belirli güvenlik özellikleri.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İleti güvenliği için kullanılan sürümü.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Güvenlik üstbilgisinde öğelerin sırasını Bu bağlama için.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
