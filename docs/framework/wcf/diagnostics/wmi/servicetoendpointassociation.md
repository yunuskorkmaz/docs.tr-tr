---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
