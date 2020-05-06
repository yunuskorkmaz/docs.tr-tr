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
ms.openlocfilehash: 9d86b23b91702929a86334f557a8d647e19861a4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860596"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="75612-102">ICLRDataTarget::GetMachineType Metodu</span><span class="sxs-lookup"><span data-stu-id="75612-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="75612-103">Hedef işlemin kullandığı yönerge kümesi türünün tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="75612-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75612-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75612-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75612-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75612-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="75612-106">dışı Hedef işlemin kullandığı yönerge kümesini gösteren bir değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75612-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="75612-107">Döndürülen `machineType` , Winnt. h üstbilgi dosyasında tanımlanan IMAGE_FILE_MACHINE sabitlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="75612-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75612-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75612-108">Requirements</span></span>  
 <span data-ttu-id="75612-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75612-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75612-110">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="75612-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="75612-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75612-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75612-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75612-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75612-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75612-113">See also</span></span>

- [<span data-ttu-id="75612-114">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75612-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
