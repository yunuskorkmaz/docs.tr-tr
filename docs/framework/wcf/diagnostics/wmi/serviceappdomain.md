---
description: Daha fazla bilgi için bkz. ServiceAppDomain
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 1ac32b1fbd88518ffb260be9dd3ed2adb88d211c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715645"
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
