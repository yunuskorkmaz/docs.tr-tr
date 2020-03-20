---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178550"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="6e53b-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="6e53b-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="6e53b-103">Belirli bir kod adresindeyönetilen kod hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="6e53b-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e53b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e53b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e53b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e53b-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="6e53b-106">[içinde] Yönetilen kod kesiminin başlangıç adresini belirten [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="6e53b-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="6e53b-107">[çıkış] Yönetilen kodun bir kesimini temsil eden "ICorDebugCode" nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e53b-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e53b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e53b-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e53b-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e53b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e53b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e53b-110">Requirements</span></span>  
 <span data-ttu-id="6e53b-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e53b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e53b-112">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e53b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e53b-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e53b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e53b-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e53b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e53b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e53b-115">See also</span></span>

- [<span data-ttu-id="6e53b-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e53b-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="6e53b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e53b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
