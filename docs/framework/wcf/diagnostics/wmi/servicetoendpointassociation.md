---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484335"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Bir hizmet için bir uç nokta eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceToEndpointAssociation sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceToEndpointAssociation sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  
 Veri türü: hizmeti  
  
 Erişim türüne: salt okunur  
Niteleyiciler: anahtar  
  
 Bitiş noktası ile ilişkilendirilmiş hizmet.  
  
### <a name="ref"></a>ref  
 Veri türü: uç noktası  
  
 Erişim türüne: salt okunur  
Niteleyiciler: anahtar  
  
 Hizmetle ilişkilendirilmiş uç nokta.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
