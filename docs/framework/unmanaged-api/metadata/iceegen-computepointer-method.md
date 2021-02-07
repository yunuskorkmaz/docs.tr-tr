---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: ComputePointer yöntemi'
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
ms.openlocfilehash: 9319343cc93eae3e4c7b060239d23ad8aeb7d3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721183"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="ed144-103">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed144-103">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="ed144-104">Belirtilen kod bölümünün arabelleğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ed144-104">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="ed144-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed144-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed144-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed144-106">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed144-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed144-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="ed144-108">'ndaki Arabellek döndürülecek kod bölümü.</span><span class="sxs-lookup"><span data-stu-id="ed144-108">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="ed144-109">'ndaki Bir işaretçinin alınacağı metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="ed144-109">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="ed144-110">dışı Döndürülen arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ed144-110">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed144-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed144-111">Requirements</span></span>  

 <span data-ttu-id="ed144-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed144-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed144-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed144-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed144-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ed144-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed144-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed144-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed144-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed144-116">See also</span></span>

- [<span data-ttu-id="ed144-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed144-117">ICeeGen Interface</span></span>](iceegen-interface.md)
