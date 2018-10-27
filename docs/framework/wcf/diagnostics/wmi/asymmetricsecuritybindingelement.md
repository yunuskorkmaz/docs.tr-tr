---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185124"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 AsymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="messageprotectionorder"></a>messageProtectionOrder  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İleti şifreleme ve imzalama için bu bağlama sırası.  
  
### <a name="requiresignatureconfirmation"></a>requireSignatureConfirmation  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bağlama imza onayı gerektirip.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
