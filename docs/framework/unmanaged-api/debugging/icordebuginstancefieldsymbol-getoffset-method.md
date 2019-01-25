---
title: ICorDebugInstanceFieldSymbol::GetOffset yöntemi
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e78a7358f62ab83c7ecba63eac9f021fc4932d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636384"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="6ed5c-102">ICorDebugInstanceFieldSymbol::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ed5c-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="6ed5c-103">Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="6ed5c-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ed5c-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ed5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ed5c-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="6ed5c-106">Bu örnek alanı, üst sınıfında uzaklığını bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ed5c-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ed5c-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ed5c-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ed5c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed5c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ed5c-109">Requirements</span></span>  
 <span data-ttu-id="6ed5c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed5c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed5c-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ed5c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ed5c-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ed5c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ed5c-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed5c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed5c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ed5c-114">See also</span></span>
- [<span data-ttu-id="6ed5c-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ed5c-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="6ed5c-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ed5c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
