---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452715"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Bir uç nokta için bir hizmet eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceToEndpointAssociation sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceToEndpointAssociation sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  
 Veri türü: hizmet  
  
 Erişim türü: salt okunur  
Niteleyiciler: anahtar  
  
 Hizmet uç noktası ile ilişkili.  
  
### <a name="ref"></a>ref  
 Veri türü: uç nokta  
  
 Erişim türü: salt okunur  
Niteleyiciler: anahtar  
  
 Hizmetle ilişkili uç noktası.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
