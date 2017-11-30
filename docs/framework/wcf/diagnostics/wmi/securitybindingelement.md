---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b567c173c5a04421bce57585d96b8b45144c5625
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
