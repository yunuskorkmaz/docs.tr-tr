---
description: 'Şu konuda daha fazla bilgi edinin: ICLRAssemblyIdentityManager arabirimi'
title: ICLRAssemblyIdentityManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: d6238ec51a8cc1bb61eaa96e5297656c447df785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790065"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager Arabirimi

Derlemeler hakkında, ana bilgisayar ve ortak dil çalışma zamanı (CLR) arasındaki iletişimi destekleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBindingIdentityFromFile Yöntemi](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Belirtilen dosya yolundaki derleme için derleme kimliği bağlama verilerini alır.|  
|[GetBindingIdentityFromStream Yöntemi](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Belirtilen akıştaki derleme için kurallı derleme kimliği verilerini alır.|  
|[GetCLRAssemblyReferenceList Yöntemi](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) örneği alır.|  
|[GetProbingAssembliesFromReference Yöntemi](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Belirtilen kimliğe sahip derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.|  
|[GetReferencedAssembliesFromFile Yöntemi](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) örneğini alır.|  
|[GetReferencedAssembliesFromStream Yöntemi](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|`ICLRReferenceAssemblyEnum`Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir nesneye yönelik bir işaretçi alır.|  
|[IsStronglyNamed Yöntemi](iclrassemblyidentitymanager-isstronglynamed-method.md)|Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICLRAssemblyIdentityManager` `ICLRAssemblyReferenceList` Derleme kimliklerini listelemek ve örnekleri almak için kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum Arabirimi](iclrprobingassemblyenum-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
