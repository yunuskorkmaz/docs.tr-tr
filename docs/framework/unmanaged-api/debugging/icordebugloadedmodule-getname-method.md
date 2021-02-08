---
description: ': ICorDebugLoadedModule:: GetName metodu hakkında daha fazla bilgi edinin'
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 40a0715b513115177cabac01727ce9166a40d50b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801260"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="98ead-103">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98ead-103">ICorDebugLoadedModule::GetName Method</span></span>

<span data-ttu-id="98ead-104">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="98ead-104">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ead-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98ead-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98ead-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98ead-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="98ead-107">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="98ead-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="98ead-108">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="98ead-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="98ead-109">dışı Yüklenen modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="98ead-109">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98ead-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98ead-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98ead-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98ead-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ead-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98ead-112">Requirements</span></span>  

 <span data-ttu-id="98ead-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98ead-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ead-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98ead-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98ead-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98ead-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98ead-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98ead-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ead-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98ead-117">See also</span></span>

- [<span data-ttu-id="98ead-118">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98ead-118">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="98ead-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98ead-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
