---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: EmitString yöntemi'
title: ICeeGen::EmitString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: fca388d044603f932bf90a176cada6e830284702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707117"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="64d70-103">ICeeGen::EmitString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64d70-103">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="64d70-104">Belirtilen dizeyi kod tabanına yayar.</span><span class="sxs-lookup"><span data-stu-id="64d70-104">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="64d70-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="64d70-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d70-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d70-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d70-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64d70-107">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="64d70-108">'ndaki Yayyapılacak dize.</span><span class="sxs-lookup"><span data-stu-id="64d70-108">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="64d70-109">dışı Yayılan dizenin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="64d70-109">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d70-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64d70-110">Requirements</span></span>  

 <span data-ttu-id="64d70-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d70-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d70-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64d70-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d70-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="64d70-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64d70-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d70-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d70-115">See also</span></span>

- [<span data-ttu-id="64d70-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64d70-116">ICeeGen Interface</span></span>](iceegen-interface.md)
