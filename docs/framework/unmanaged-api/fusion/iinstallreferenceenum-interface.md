---
title: IInstallReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aed89008dd2fa86b38f243c8e7cca1bdda901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497780"
---
# <a name="iinstallreferenceenum-interface"></a>IInstallReferenceEnum Arabirimi
Genel derleme önbelleğinde yüklü başvurulan derlemeler için bir numaralandırıcı temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetNextInstallReferenceItem Yöntemi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|Sonraki bir işaretçi alır `IInstallReferenceItem` bu konuda yer alan `IInstallReferenceEnum`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IInstallReferenceItem Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
