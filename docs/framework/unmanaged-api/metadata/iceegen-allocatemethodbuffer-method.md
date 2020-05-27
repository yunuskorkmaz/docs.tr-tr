---
title: ICeeGen::AllocateMethodBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 8dc7f439cac56c2d55916ff8631ec3095c67680d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008891"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="be8c0-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be8c0-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="be8c0-103">Bir yöntem için belirtilen boyutun bir arabelleğini oluşturur ve yöntemin göreli sanal adresini alır.</span><span class="sxs-lookup"><span data-stu-id="be8c0-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="be8c0-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="be8c0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8c0-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="be8c0-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be8c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be8c0-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="be8c0-107">'ndaki Oluşturulacak arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="be8c0-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="be8c0-108">dışı Döndürülen arabellek.</span><span class="sxs-lookup"><span data-stu-id="be8c0-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="be8c0-109">dışı Metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="be8c0-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be8c0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be8c0-110">Requirements</span></span>  
 <span data-ttu-id="be8c0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be8c0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be8c0-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be8c0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be8c0-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="be8c0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be8c0-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be8c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8c0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be8c0-115">See also</span></span>

- [<span data-ttu-id="be8c0-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be8c0-116">ICeeGen Interface</span></span>](iceegen-interface.md)
