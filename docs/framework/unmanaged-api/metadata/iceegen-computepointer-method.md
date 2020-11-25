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
ms.openlocfilehash: 41a3b9c77fc766b2fa39b406dedbb3203cc97ad9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715478"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="f9b83-102">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b83-102">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="f9b83-103">Belirtilen kod bölümünün arabelleğini belirler.</span><span class="sxs-lookup"><span data-stu-id="f9b83-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="f9b83-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9b83-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b83-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9b83-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9b83-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9b83-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="f9b83-107">'ndaki Arabellek döndürülecek kod bölümü.</span><span class="sxs-lookup"><span data-stu-id="f9b83-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="f9b83-108">'ndaki Bir işaretçinin alınacağı metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="f9b83-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f9b83-109">dışı Döndürülen arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f9b83-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b83-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9b83-110">Requirements</span></span>  

 <span data-ttu-id="f9b83-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b83-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b83-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9b83-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9b83-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f9b83-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9b83-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b83-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9b83-115">See also</span></span>

- [<span data-ttu-id="f9b83-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9b83-116">ICeeGen Interface</span></span>](iceegen-interface.md)
