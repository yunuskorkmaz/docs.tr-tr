---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192245"
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Uygulama etki alanı için bir hizmet eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceAppDomain sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceAppDomain sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="ref"></a>ref  
 Veri türü: hizmet  
Niteleyiciler: anahtar  
  
 Erişim türü: salt okunur  
  
 Bu uygulama etki alanının hizmet.  
  
### <a name="ref"></a>ref  
 Veri türü: AppDomainInfo  
Niteleyiciler: anahtar  
  
 Erişim türü: salt okunur  
  
 Uygulama etki alanı özelliklerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
