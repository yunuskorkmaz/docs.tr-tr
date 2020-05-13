---
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
ms.openlocfilehash: 9020fed83b1c57cae3cc492872a279afb0195983
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205169"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="23ed0-102">ICorDebugILFrame2::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23ed0-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="23ed0-103">Bu çerçevedeki parametreleri içeren bir ICorDebugTypeEnum nesnesi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="23ed0-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ed0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23ed0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23ed0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23ed0-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="23ed0-106">Tür parametrelerinin numaralandırılmasına izin veren bir ICorDebugTypeEnum Arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="23ed0-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="23ed0-107">Tür parametrelerinin listesi, sınıf türü parametreleri (varsa) ve ardından Yöntem türü parametreleri (varsa) içerir.</span><span class="sxs-lookup"><span data-stu-id="23ed0-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23ed0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23ed0-108">Remarks</span></span>  
 <span data-ttu-id="23ed0-109">Bu listenin kaç sınıf türü parametre ve yöntem türü parametrelerinin içerdiğini öğrenmek için [IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="23ed0-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="23ed0-110">Tür parametreleri her zaman kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="23ed0-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ed0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23ed0-111">Requirements</span></span>  
 <span data-ttu-id="23ed0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ed0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ed0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23ed0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23ed0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="23ed0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23ed0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ed0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
