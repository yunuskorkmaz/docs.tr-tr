---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 61eae75de04f75b6ad6e78d16569595732b3d28f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273314"
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
