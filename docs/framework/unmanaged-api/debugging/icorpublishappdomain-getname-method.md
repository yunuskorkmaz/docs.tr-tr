---
description: ': ICorPublishAppDomain:: GetName metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 05b1b14f7e0db371b29059ec3d44333ac40428e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721807"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName Yöntemi

Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.  
  
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
 'ndaki `szName` Dizinin boyutu.  
  
 `pcchName`  
 dışı Dizide döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi `szName` .  
  
 `szName`  
 dışı Adın kaydedileceği bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  

 `szName`Null değilse, `GetName` yöntemi `cchName` içine (null Sonlandırıcı dahil) kadar karakter kopyalar `szName` . İçinde null olmayan bir değer döndürülürse `pcchName` , ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizide depolanır.  
  
 `GetName`Yöntemi, kaç karakterin kopyalandığına BAKıLMAKSıZıN HRESULT s_ok döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishAppDomain Arabirimi](icorpublishappdomain-interface.md)
