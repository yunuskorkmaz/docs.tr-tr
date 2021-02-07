---
description: 'Daha fazla bilgi edinin: anlaşma'
title: Anlaşma
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 3443a7d2eed1a34f07495bd3ceb98c1ba997fabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757559"
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
  
### <a name="name"></a>Name  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 WSDL 'deki sözleşmenin adı.  
  
### <a name="namespace"></a>Ad Alanı  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 `portType`WSDL içindeki öğenin ad alanı.  
  
### <a name="operations"></a>Operations  

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
