---
description: 'Daha fazla bilgi edinin: AsymmetricSecurityBindingElement'
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 25d0ac205491e9ce27c59d3a0670d1e4a3150e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757949"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement

AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 AsymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
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

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
