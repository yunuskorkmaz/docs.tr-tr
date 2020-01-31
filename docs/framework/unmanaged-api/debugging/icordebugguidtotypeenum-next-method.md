---
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
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777639"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="0a015-102">ICorDebugGuidToTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a015-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="0a015-103">GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0a015-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a015-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a015-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a015-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a015-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0a015-106">'ndaki Alınacak GUID-tür eşleme nesnelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0a015-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0a015-107">dışı Her biri bir Windows Çalışma Zamanı GUID 'sini karşılık gelen ICorDebugType nesnesine eşleyen bir [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0a015-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0a015-108">dışı Aslında `values`' de döndürülen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnelerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0a015-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a015-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a015-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a015-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a015-110">Requirements</span></span>  
 <span data-ttu-id="0a015-111">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0a015-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="0a015-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0a015-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a015-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0a015-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a015-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a015-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a015-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a015-115">See also</span></span>

- [<span data-ttu-id="0a015-116">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a015-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="0a015-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a015-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
