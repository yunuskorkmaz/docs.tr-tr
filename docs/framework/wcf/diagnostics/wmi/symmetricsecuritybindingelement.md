---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485062"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İleti şifreleme ve bu bağlama için imzalama sırası.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Olup bağlama imza onayı gerektirir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
