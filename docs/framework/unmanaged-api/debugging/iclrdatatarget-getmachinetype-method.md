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
ms.openlocfilehash: ff9c88d534e0bfe51075a76581af37aba791a3da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148479"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="f385e-102">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="f385e-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="f385e-103">Hedef işlemin kullandığı yönerge kümesi türü için tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="f385e-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f385e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f385e-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f385e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f385e-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="f385e-106">[out] İşaretçisi talimat hedef işlem kümesi gösteren bir değer kullanır.</span><span class="sxs-lookup"><span data-stu-id="f385e-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="f385e-107">Döndürülen `machineType` WinNT.h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitleri biridir.</span><span class="sxs-lookup"><span data-stu-id="f385e-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f385e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f385e-108">Requirements</span></span>  
 <span data-ttu-id="f385e-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f385e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f385e-110">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f385e-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f385e-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f385e-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f385e-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f385e-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f385e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f385e-113">See also</span></span>

- [<span data-ttu-id="f385e-114">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f385e-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
