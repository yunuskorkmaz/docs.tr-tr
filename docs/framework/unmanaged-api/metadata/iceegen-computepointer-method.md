---
title: ICeeGen::ComputePointer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008878"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="fd023-102">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd023-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="fd023-103">Belirtilen kod bölümünün arabelleğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fd023-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="fd023-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fd023-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd023-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd023-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd023-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd023-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="fd023-107">'ndaki Arabellek döndürülecek kod bölümü.</span><span class="sxs-lookup"><span data-stu-id="fd023-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="fd023-108">'ndaki Bir işaretçinin alınacağı metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="fd023-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="fd023-109">dışı Döndürülen arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fd023-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd023-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd023-110">Requirements</span></span>  
 <span data-ttu-id="fd023-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd023-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd023-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fd023-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd023-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fd023-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd023-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd023-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd023-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd023-115">See also</span></span>

- [<span data-ttu-id="fd023-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd023-116">ICeeGen Interface</span></span>](iceegen-interface.md)
