---
description: 'Hakkında daha fazla bilgi edinin: ServiceToEndpointAssociation'
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 1ae2ce2bcc0b3494b00fffa750f3ca46d26fe08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715346"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation

Bir hizmeti uç noktayla eşleştirir.  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceToEndpointAssociation sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceToEndpointAssociation sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  

 Veri türü: hizmet  
  
 Erişim türü: salt okunurdur  
Niteleyiciler: anahtar  
  
 Uç noktayla ilişkili hizmet.  
  
### <a name="ref"></a>ref  

 Veri türü: uç nokta  
  
 Erişim türü: salt okunurdur  
Niteleyiciler: anahtar  
  
 Hizmetle ilişkili uç nokta.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
