---
title: Anlaşma
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 0df39bbd0b273f1e898ccbe585be288cc245b7f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274146"
---
# <a name="contract"></a>Anlaşma

Anlaşma  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 Anlaşma sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Sözleşme sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainID  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Sözleşmeyi barındıran AppDomain 'in AppDomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  

 Veri türü: davranış dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu sözleşmeyle ilişkilendirilen davranışlar.  
  
### <a name="name"></a>Adı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 WSDL 'deki sözleşmenin adı.  
  
### <a name="namespace"></a>Ad Alanı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 `portType`WSDL içindeki öğenin ad alanı.  
  
### <a name="operations"></a>İşlemler  

 Veri türü: Işlem dizisi  
  
 Erişim türü: salt okunurdur  
  
 Bu sözleşmenin işlemleri.  
  
### <a name="processid"></a>Işlem  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Sözleşmeyi barındıran işlemin işlem kimliği.  
  
### <a name="ref"></a>ref  

 Veri türü: sözleşme  
  
 Erişim türü: salt okunurdur  
  
 Anlaşma bir çift yönlü sözleşme olduğunda geri çağırma türü.  
  
### <a name="sessionmode"></a>SessionMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Sözleşmenin Bu sözleşmeyle ilişkili bağlamanın kanal oturumlarını kullanmasını gerektirip gerektirmediğini belirtir.  
  
### <a name="type"></a>Tür  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Sözleşmenin türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ContractDescription>
