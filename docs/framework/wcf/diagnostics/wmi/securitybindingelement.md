---
description: 'Daha fazla bilgi edinin: SecurityBindingElement'
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: bc9a519978a9cccccd80a58abb8d109fa9bc9337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743817"
---
# <a name="securitybindingelement"></a>SecurityBindingElement

SecurityBindingElement  
  
## <a name="syntax"></a>Syntax  
  
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

 SecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlamakla kullanılacak algoritmaları belirtir.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Her iletinin bir zaman damgası içerip içermediğini belirten Boolean bir değer.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Anahtar oluşturmak için kullanılan entropi kaynağı.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  

 Veri türü: LocalServiceSecuritySettings  
  
 Erişim türü: salt okunurdur  
  
 Yerel hizmet için bağlamaya özgü güvenlik özellikleri.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İleti güvenliği için kullanılan sürüm.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlamanın güvenlik üstbilgisindeki öğelerin sırası.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
