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
ms.openlocfilehash: 495d84470c559df13ea64b63dd00582f4335d4e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673202"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="71076-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="71076-102">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="71076-103">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="71076-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="71076-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="71076-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71076-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="71076-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71076-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71076-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="71076-107">'ndaki `ICeeFileGen` Yok edilecek nesne.</span><span class="sxs-lookup"><span data-stu-id="71076-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71076-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71076-108">Return Value</span></span>  

 <span data-ttu-id="71076-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="71076-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71076-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71076-110">Remarks</span></span>  

 <span data-ttu-id="71076-111">`DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md) işlevi tarafından oluşturulan nesneyi yok eder.</span><span class="sxs-lookup"><span data-stu-id="71076-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71076-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71076-112">Requirements</span></span>  

 <span data-ttu-id="71076-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71076-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71076-114">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="71076-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="71076-115">**Kitaplık:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="71076-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="71076-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71076-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71076-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71076-117">See also</span></span>

- [<span data-ttu-id="71076-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="71076-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
