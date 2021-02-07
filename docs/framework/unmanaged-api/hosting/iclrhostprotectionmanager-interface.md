---
description: ': ICLRHostProtectionManager Arabirimi hakkında daha fazla bilgi'
title: ICLRHostProtectionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689254"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager Arabirimi

Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Önemli ortak dil çalışma zamanı (CLR) hatalarına neden olabilecek nadir bazı yarış durumlarının hiçbir şekilde ortaya çıkması garantisi sağlar.|  
|[SetProtectedCategories Yöntemi](iclrhostprotectionmanager-setprotectedcategories-method.md)|Kısmen güvenilen kodda çalışması engellenecek olan yönetilen türlerin ve üyelerin kategorilerini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EApiCategories Numaralandırması](eapicategories-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
