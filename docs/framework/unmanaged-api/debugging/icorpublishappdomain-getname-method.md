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
ms.openlocfilehash: 4325d61d12a66b17f88e5e368cbbc7806d0a3ec5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790717"
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
 'ndaki `szName` dizisinin boyutu.  
  
 `pcchName`  
 dışı `szName` dizisinde döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi.  
  
 `szName`  
 dışı Adın kaydedileceği bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `szName` null değilse `GetName` yöntemi, `szName``cchName` karaktere (null Sonlandırıcı dahil) kopyalar. `pcchName`null olmayan bir değer döndürülürse, ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizisinde depolanır.  
  
 `GetName` yöntemi, kaç karakter kopyalandığına bakılmaksızın HRESULT S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishAppDomain Arabirimi](icorpublishappdomain-interface.md)
