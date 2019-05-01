---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957079"
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
 Veri türü: Hizmet  
Qualifiers: Anahtar  
  
 Erişim türü: salt okunur  
  
 Bu uygulama etki alanının hizmet.  
  
### <a name="ref"></a>ref  
 Veri türü: AppDomainInfo  
Qualifiers: Anahtar  
  
 Erişim türü: salt okunur  
  
 Uygulama etki alanı özelliklerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|
