---
description: 'Şu konuda daha fazla bilgi edinin: DestroyICeeFileGen Işlevi'
title: DestroyICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 14ae990999247b90f16b10115dea3408b965a04a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785659"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="41096-103">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="41096-103">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="41096-104">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="41096-104">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="41096-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="41096-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41096-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41096-106">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41096-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41096-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="41096-108">'ndaki `ICeeFileGen` Yok edilecek nesne.</span><span class="sxs-lookup"><span data-stu-id="41096-108">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41096-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41096-109">Return Value</span></span>  

 <span data-ttu-id="41096-110">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="41096-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41096-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41096-111">Remarks</span></span>  

 <span data-ttu-id="41096-112">`DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md) işlevi tarafından oluşturulan nesneyi yok eder.</span><span class="sxs-lookup"><span data-stu-id="41096-112">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41096-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41096-113">Requirements</span></span>  

 <span data-ttu-id="41096-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41096-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41096-115">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="41096-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="41096-116">**Kitaplık:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="41096-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="41096-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41096-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41096-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41096-118">See also</span></span>

- [<span data-ttu-id="41096-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="41096-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
