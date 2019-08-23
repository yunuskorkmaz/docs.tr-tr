---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85748106edb34b98f975a40bcc2617401536e271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910098"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="81521-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="81521-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="81521-103">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="81521-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81521-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81521-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81521-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81521-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="81521-106">dışı Yüklenen modülün temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81521-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81521-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81521-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81521-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81521-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81521-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81521-109">Requirements</span></span>  
 <span data-ttu-id="81521-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81521-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81521-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81521-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81521-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="81521-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81521-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81521-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81521-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81521-114">See also</span></span>

- [<span data-ttu-id="81521-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81521-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="81521-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="81521-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
