---
description: 'Daha fazla bilgi edinin: IGCHost2 Interface'
title: IGCHost2 Arabirimi
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: e32a4894fcff3600c9385f0f559443e23b2bc307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709327"
---
# <a name="igchost2-interface"></a>IGCHost2 Arabirimi

Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.  
  
> [!NOTE]
> Yeni geliştirme için, bunun yerine [ICLRGCManager2](iclrgcmanager2-interface.md) arabirimini kullanmanızı öneririz.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetGCStartupLimitsEx Yöntemi](igchost2-setgcstartuplimitsex-method.md)|Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar. 1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
- [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)
- [CorRuntimeHost Ortak Sınıfı](corruntimehost-coclass.md)
