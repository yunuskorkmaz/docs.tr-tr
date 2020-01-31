---
title: 'ICorDebugSymbolProvider2:: GetFrameProps yöntemi'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: dc64152938c46945978715251286ecb6c6d8983c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791518"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="7a0eb-102">ICorDebugSymbolProvider2:: GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a0eb-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="7a0eb-103">Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a0eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a0eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a0eb-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="7a0eb-106">'ndaki Kod göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="7a0eb-107">dışı Metodun başlangıç göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="7a0eb-108">dışı Çerçevenin başlangıç göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a0eb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a0eb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a0eb-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0eb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a0eb-111">Requirements</span></span>  
 <span data-ttu-id="7a0eb-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a0eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0eb-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a0eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a0eb-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a0eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a0eb-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0eb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0eb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a0eb-116">See also</span></span>

- [<span data-ttu-id="7a0eb-117">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a0eb-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="7a0eb-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a0eb-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
