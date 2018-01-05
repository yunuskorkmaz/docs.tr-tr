---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a>Daralma
Daralma  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 Sözleşme sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Sözleşme sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="appdomainid"></a>AppDomainId  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Sözleşme barındıran appdomain kimliği.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranış dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu sözleşme ile ilişkilendirilen davranışlar.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL içindeki sözleşme adı.  
  
### <a name="namespace"></a>Ad Alanı  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Ad alanı `portType` WSDL öğesinde.  
  
### <a name="operations"></a>İşlemler  
 Veri türü: işlem dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu sözleşme işlemleri.  
  
### <a name="processid"></a>İşlem kimliği  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İşlemin işlem kimliği Sözleşmeyi barındıran.  
  
### <a name="ref"></a>ref  
 Veri türü: Sözleşme  
  
 Erişim türüne: salt okunur  
  
 Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.  
  
### <a name="sessionmode"></a>SessionMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sözleşme kanal oturumları kullanmak için bu sözleşmeyle ilişkili bağlama gerekli olup olmadığını gösterir.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sözleşme türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ContractDescription>
