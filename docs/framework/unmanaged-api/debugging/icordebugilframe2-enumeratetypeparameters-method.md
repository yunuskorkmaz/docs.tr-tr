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
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="9b0e4-103">ICorDebugILFrame2::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b0e4-103">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="9b0e4-104">Bu çerçevedeki parametreleri içeren bir ICorDebugTypeEnum nesnesi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="9b0e4-104">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b0e4-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b0e4-106">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="9b0e4-107">Tür parametrelerinin numaralandırılmasına izin veren bir ICorDebugTypeEnum Arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b0e4-107">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="9b0e4-108">Tür parametrelerinin listesi, sınıf türü parametreleri (varsa) ve ardından Yöntem türü parametreleri (varsa) içerir.</span><span class="sxs-lookup"><span data-stu-id="9b0e4-108">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0e4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b0e4-109">Remarks</span></span>  

 <span data-ttu-id="9b0e4-110">Bu listenin kaç sınıf türü parametre ve yöntem türü parametrelerinin içerdiğini öğrenmek için [IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b0e4-110">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="9b0e4-111">Tür parametreleri her zaman kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="9b0e4-111">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0e4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b0e4-112">Requirements</span></span>  

 <span data-ttu-id="9b0e4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0e4-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b0e4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b0e4-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b0e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b0e4-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
