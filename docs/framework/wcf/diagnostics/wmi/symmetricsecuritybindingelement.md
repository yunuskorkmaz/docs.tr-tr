---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274107"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement

SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama için ileti şifreleme ve imzalama sırası.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bağlamanın imza onayını gerektirip gerektirmediğini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
