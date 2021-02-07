---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugGuidToTypeEnum:: Next yöntemi'
title: ICorDebugGuidToTypeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 0ab05cc0689c76c0bb185205ea00c5ccebfcbe03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661005"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="b58dc-103">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b58dc-103">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="b58dc-104">GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b58dc-104">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b58dc-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b58dc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b58dc-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b58dc-107">'ndaki Alınacak GUID-tür eşleme nesnelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b58dc-107">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b58dc-108">dışı Her biri bir Windows Çalışma Zamanı GUID 'sini karşılık gelen ICorDebugType nesnesine eşleyen bir [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="b58dc-108">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b58dc-109">dışı Gerçekte içinde döndürülen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnelerinin sayısına yönelik bir işaretçi `values` .</span><span class="sxs-lookup"><span data-stu-id="b58dc-109">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b58dc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b58dc-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58dc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b58dc-111">Requirements</span></span>  

 <span data-ttu-id="b58dc-112">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b58dc-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="b58dc-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b58dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b58dc-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b58dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b58dc-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58dc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b58dc-116">See also</span></span>

- [<span data-ttu-id="b58dc-117">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b58dc-117">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="b58dc-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b58dc-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
