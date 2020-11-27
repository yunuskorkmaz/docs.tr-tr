---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273951"
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
