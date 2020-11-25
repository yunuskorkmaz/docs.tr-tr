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
ms.openlocfilehash: e1849eb95401e3637a1fd1b00715332f9886071e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715530"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="df4b0-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df4b0-102">ICeeGen::AllocateMethodBuffer Method</span></span>

<span data-ttu-id="df4b0-103">Bir yöntem için belirtilen boyutun bir arabelleğini oluşturur ve yöntemin göreli sanal adresini alır.</span><span class="sxs-lookup"><span data-stu-id="df4b0-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="df4b0-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="df4b0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df4b0-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="df4b0-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df4b0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df4b0-106">Parameters</span></span>  

 `cchBuffer`  
 <span data-ttu-id="df4b0-107">'ndaki Oluşturulacak arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="df4b0-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="df4b0-108">dışı Döndürülen arabellek.</span><span class="sxs-lookup"><span data-stu-id="df4b0-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="df4b0-109">dışı Metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="df4b0-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df4b0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df4b0-110">Requirements</span></span>  

 <span data-ttu-id="df4b0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df4b0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df4b0-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="df4b0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df4b0-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="df4b0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df4b0-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df4b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4b0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df4b0-115">See also</span></span>

- [<span data-ttu-id="df4b0-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df4b0-116">ICeeGen Interface</span></span>](iceegen-interface.md)
