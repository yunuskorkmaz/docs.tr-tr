---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Uygulama etki alanı için bir hizmet eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceAppDomain sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceAppDomain sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  
 Veri türü: hizmeti  
Niteleyiciler: anahtar  
  
 Erişim türüne: salt okunur  
  
 Bu uygulama etki alanı hizmeti.  
  
### <a name="ref"></a>ref  
 Veri türü: AppDomainInfo  
Niteleyiciler: anahtar  
  
 Erişim türüne: salt okunur  
  
 Uygulama etki alanı özelliklerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|
