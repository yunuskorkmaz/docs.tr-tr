---
description: ': ICLRDataTarget:: GetMachineType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5624f734a77f51b4ea6cd9dd0c9df393c72e7d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801351"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="14561-103">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="14561-103">ICLRDataTarget::GetMachineType Method</span></span>

<span data-ttu-id="14561-104">Hedef işlemin kullandığı yönerge kümesi türünün tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="14561-104">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14561-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14561-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14561-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14561-106">Parameters</span></span>  

 `machineType`  
 <span data-ttu-id="14561-107">dışı Hedef işlemin kullandığı yönerge kümesini gösteren bir değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14561-107">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="14561-108">Döndürülen, `machineType` Winnt. h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="14561-108">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14561-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14561-109">Requirements</span></span>  

 <span data-ttu-id="14561-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14561-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14561-111">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="14561-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="14561-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14561-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14561-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14561-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14561-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14561-114">See also</span></span>

- [<span data-ttu-id="14561-115">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14561-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
