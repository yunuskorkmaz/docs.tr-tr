---
description: ': ICorDebugSymbolProvider2:: GetFrameProps yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider2:: GetFrameProps yöntemi'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659562"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="26f7b-103">ICorDebugSymbolProvider2:: GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="26f7b-103">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="26f7b-104">Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="26f7b-104">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26f7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26f7b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26f7b-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="26f7b-107">'ndaki Kod göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="26f7b-107">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="26f7b-108">dışı Metodun başlangıç göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26f7b-108">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="26f7b-109">dışı Çerçevenin başlangıç göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26f7b-109">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f7b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26f7b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26f7b-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26f7b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f7b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26f7b-112">Requirements</span></span>  

 <span data-ttu-id="26f7b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f7b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f7b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26f7b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26f7b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26f7b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26f7b-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f7b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f7b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26f7b-117">See also</span></span>

- [<span data-ttu-id="26f7b-118">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26f7b-118">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="26f7b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26f7b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
