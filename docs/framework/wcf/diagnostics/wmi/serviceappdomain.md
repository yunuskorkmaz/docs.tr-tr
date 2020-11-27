---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 243c9112dd9caf5c92ef77aa0f45b4b1e71a4e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273262"
---
# <a name="serviceappdomain"></a>ServiceAppDomain

Bir hizmeti bir uygulama etki alanına eşler.  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceAppDomain sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceAppDomain sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  

 Veri türü: hizmet  
Niteleyiciler: anahtar  
  
 Erişim türü: salt okunurdur  
  
 Bu uygulama etki alanının hizmeti.  
  
### <a name="ref"></a>ref  

 Veri türü: AppDomainInfo  
Niteleyiciler: anahtar  
  
 Erişim türü: salt okunurdur  
  
 Uygulama etki alanının özelliklerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|
