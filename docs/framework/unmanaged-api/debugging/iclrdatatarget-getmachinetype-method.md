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
ms.openlocfilehash: c515a8184e8c01b0e292057f3f66ffef28f2c5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402887"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="d7493-102">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="d7493-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="d7493-103">Tanımlayıcı için hedef işlem kullanarak yönerge kümesi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d7493-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7493-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7493-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7493-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7493-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="d7493-106">[out] Hedef işlem kümesi talimat belirten bir değer için bir işaretçi kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="d7493-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="d7493-107">Döndürülen `machineType` WinNT.h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitleri biridir.</span><span class="sxs-lookup"><span data-stu-id="d7493-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7493-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7493-108">Requirements</span></span>  
 <span data-ttu-id="d7493-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7493-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7493-110">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d7493-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d7493-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7493-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7493-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7493-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7493-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7493-113">See Also</span></span>  
 [<span data-ttu-id="d7493-114">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7493-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
