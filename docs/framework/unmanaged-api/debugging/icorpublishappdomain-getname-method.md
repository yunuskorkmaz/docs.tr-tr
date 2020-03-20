---
title: ICorPublishAppDomain::GetName Yöntemi
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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178414"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName Yöntemi
Bu [iCorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchName`  
 [içinde] `szName` Dizinin boyutu.  
  
 `pcchName`  
 [çıkış] Null karakteri de dahil olmak üzere geniş karakter sayısına `szName` işaretçi, dizide döndürülür.  
  
 `szName`  
 [çıkış] Adın depolandığı bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Null `szName` olmayan ise, `GetName` yöntem karakterlere `cchName` kadar kopyalar (null terminator `szName`dahil) içine . Null olmayan bir döndürülürse, `pcchName`addaki gerçek karakter sayısı (null sonlandırıcı dahil) `szName` dizide depolanır.  
  
 Yöntem, `GetName` kaç karakter kopyalandığından bağımsız olarak bir S_OK HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorPub.idl, CorPub.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishAppDomain Arabirimi](icorpublishappdomain-interface.md)
