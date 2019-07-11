---
title: ICLRDataTarget::GetMachineType Metodu
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 958968fb1a84b598b0c3e92151fbad58fc5e79d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738747"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="a1ee7-102">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="a1ee7-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="a1ee7-103">Hedef işlemin kullandığı yönerge kümesi türü için tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a1ee7-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1ee7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ee7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1ee7-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="a1ee7-106">[out] İşaretçisi talimat hedef işlem kümesi gösteren bir değer kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ee7-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="a1ee7-107">Döndürülen `machineType` WinNT.h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitleri biridir.</span><span class="sxs-lookup"><span data-stu-id="a1ee7-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ee7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1ee7-108">Requirements</span></span>  
 <span data-ttu-id="a1ee7-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ee7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ee7-110">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a1ee7-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a1ee7-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ee7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ee7-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ee7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ee7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1ee7-113">See also</span></span>

- [<span data-ttu-id="a1ee7-114">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1ee7-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
