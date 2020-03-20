---
title: ICorDebugProcess5::EnumerateGCReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178617"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="cdcfe-102">ICorDebugProcess5::EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdcfe-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="cdcfe-103">Bir işlemde çöp olarak toplanacak olan tüm nesneler için bir sayısallaştırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcfe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdcfe-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdcfe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdcfe-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="cdcfe-106">[içinde] Zayıf başvuruların da numaralandırılıp numaralandırılmayacağını gösteren bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="cdcfe-107">`enumerateWeakReferences` Ise, `true` `ppEnum` sayısallaştırıcı hem güçlü başvurular hem de zayıf referanslar içerir.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="cdcfe-108">`enumerateWeakReferences` Ise, `false`sayısallaştırıcı yalnızca güçlü başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="cdcfe-109">[çıkış] Nesnelerin çöp olarak toplanması için bir sayıyalı olan [bir ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdcfe-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdcfe-110">Remarks</span></span>  
 <span data-ttu-id="cdcfe-111">Bu yöntem, bir işlemde yönetilen herhangi bir nesne için tam köklenme zincirini belirlemek için bir yol sağlar ve bir nesnenin neden hala hayatta olduğunu belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdcfe-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdcfe-112">Requirements</span></span>  
 <span data-ttu-id="cdcfe-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdcfe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdcfe-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdcfe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdcfe-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdcfe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdcfe-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdcfe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcfe-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdcfe-117">See also</span></span>

- [<span data-ttu-id="cdcfe-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdcfe-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="cdcfe-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cdcfe-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
