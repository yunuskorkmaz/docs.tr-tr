---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 618899c80d1b22aaabc3c13fe1079137eaf10a93
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182508"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
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
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
