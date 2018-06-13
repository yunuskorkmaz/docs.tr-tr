---
title: ICorPublishAppDomain::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 796f8ea42cc5cbe13729f7b92e15bc214d62734d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423864"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName Metodu
Bu tarafından temsil edilen uygulama etki alanı adını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Boyutunu `szName` dizi.  
  
 `pcchName`  
 [out] Null döndürdü karakteri de dahil olmak üzere geniş karakter sayısını gösteren bir işaretçi `szName` dizi.  
  
 `szName`  
 [out] Dizi adı depolanacağı.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `szName` boş olduğundan `GetName` yöntemi kopyalar kadar `cchName` (null Sonlandırıcı dahil) karakterlere `szName`. Null olmayan bir döndürülürse `pcchName`, gerçek (null Sonlandırıcı dahil) adı karakter sayısı depolanan `szName` dizi.  
  
 `GetName` Yöntemi kaç karakterin kopyalanan bakılmaksızın bir S_OK HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorPublishAppDomain Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
