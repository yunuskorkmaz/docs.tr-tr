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
ms.openlocfilehash: 50ea9caf08b2ffb689760da95af4e5c3fdd77301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793735"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="cd67d-102">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="cd67d-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="cd67d-103">Hedef işlemin kullandığı yönerge kümesi türünün tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="cd67d-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd67d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd67d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd67d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd67d-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="cd67d-106">dışı Hedef işlemin kullandığı yönerge kümesini gösteren bir değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cd67d-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="cd67d-107">Döndürülen `machineType`, WinNT. h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="cd67d-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd67d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd67d-108">Requirements</span></span>  
 <span data-ttu-id="cd67d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd67d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd67d-110">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cd67d-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cd67d-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cd67d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd67d-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd67d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd67d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd67d-113">See also</span></span>

- [<span data-ttu-id="cd67d-114">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd67d-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
