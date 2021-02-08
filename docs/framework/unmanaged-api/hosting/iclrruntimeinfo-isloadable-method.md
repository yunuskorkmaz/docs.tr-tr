---
description: ': ICLRRuntimeInfo:: ısyüklenebilir yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeInfo::IsLoadable Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: cf63212350bfbd18e2a312add72818b163c32d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789794"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable Yöntemi

Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbLoadable`  
 [out] `true` Bu çalışma zamanı geçerli işleme yüklenebiliyorsanız, Aksi takdirde, `false` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pbLoadable` null.|  
  
## <a name="remarks"></a>Açıklamalar  

 Başka bir çalışma zamanı işleme zaten yüklenmişse ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebiliyorsanız, `pbLoadable` döndürür `true` . İki çalışma zamanı işlem içi yan yana `pbLoadable` çalıştıramsam, döndürür `false` . Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4, CLR sürüm 2,0 veya CLR sürüm 1,1 ile aynı işlemde yan yana çalışabilir. Ancak, CLR sürüm 1,1 ve CLR sürüm 2,0, yan yana işlem içinde çalıştırılamaz.  
  
 İşleme hiçbir çalışma zamanı yüklü değilse, bu yöntem her zaman döndürülür `true` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
