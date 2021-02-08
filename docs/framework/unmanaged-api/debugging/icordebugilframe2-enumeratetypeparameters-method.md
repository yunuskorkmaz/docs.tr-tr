---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILFrame2:: EnumerateTypeParameters yöntemi'
title: ICorDebugILFrame2::EnumerateTypeParameters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 34f305b7793e4909318ae2301d72e2af7c12f2c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791300"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters Yöntemi

Bu çerçevedeki parametreleri içeren bir ICorDebugTypeEnum nesnesi alır <xref:System.Type> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppTyParEnum`  
 Tür parametrelerinin numaralandırılmasına izin veren bir ICorDebugTypeEnum Arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
 Tür parametrelerinin listesi, sınıf türü parametreleri (varsa) ve ardından Yöntem türü parametreleri (varsa) içerir.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu listenin kaç sınıf türü parametre ve yöntem türü parametrelerinin içerdiğini öğrenmek için [IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) metodunu kullanın.  
  
 Tür parametreleri her zaman kullanılabilir değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
