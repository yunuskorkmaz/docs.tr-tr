---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetSectionDataLen yöntemi'
title: ICeeGen::GetSectionDataLen Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 9475112a6f25e9a4c57c4ded6cd11dab9bf352b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721063"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="202e0-103">ICeeGen::GetSectionDataLen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="202e0-103">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="202e0-104">Belirtilen bölümün uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="202e0-104">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="202e0-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="202e0-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="202e0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="202e0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="202e0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="202e0-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="202e0-108">'ndaki Uzunluğu alınacak olan veri bölümü.</span><span class="sxs-lookup"><span data-stu-id="202e0-108">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="202e0-109">dışı Belirtilen bölümün döndürdüğü uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="202e0-109">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="202e0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="202e0-110">Remarks</span></span>  

 <span data-ttu-id="202e0-111">`GetSectionDataLen`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="202e0-111">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="202e0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="202e0-112">Requirements</span></span>  

 <span data-ttu-id="202e0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="202e0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="202e0-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="202e0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="202e0-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="202e0-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="202e0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="202e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202e0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="202e0-117">See also</span></span>

- [<span data-ttu-id="202e0-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="202e0-118">ICeeGen Interface</span></span>](iceegen-interface.md)
