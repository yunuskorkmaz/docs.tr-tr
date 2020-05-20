---
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
ms.openlocfilehash: ff7e7b299d185b8db263d2076c1e075b87b487fc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616404"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="7f751-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="7f751-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="7f751-103">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="7f751-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="7f751-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="7f751-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f751-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f751-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f751-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f751-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="7f751-107">'ndaki `ICeeFileGen`Yok edilecek nesne.</span><span class="sxs-lookup"><span data-stu-id="7f751-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f751-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f751-108">Return Value</span></span>  
 <span data-ttu-id="7f751-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f751-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f751-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f751-110">Remarks</span></span>  
 <span data-ttu-id="7f751-111">`DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md) işlevi tarafından oluşturulan nesneyi yok eder.</span><span class="sxs-lookup"><span data-stu-id="7f751-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f751-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f751-112">Requirements</span></span>  
 <span data-ttu-id="7f751-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f751-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f751-114">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="7f751-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="7f751-115">**Kitaplık:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="7f751-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="7f751-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f751-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f751-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f751-117">See also</span></span>

- [<span data-ttu-id="7f751-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7f751-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
