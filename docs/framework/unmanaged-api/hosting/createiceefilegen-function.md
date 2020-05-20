---
title: CreateICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 294b82efd66704014aab1b73171afe9165f17664
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616456"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="3d882-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d882-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="3d882-103">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d882-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="3d882-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3d882-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d882-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3d882-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d882-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d882-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="3d882-107">dışı Yeni bir nesnenin adresine yönelik bir işaretçi `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="3d882-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d882-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d882-108">Return Value</span></span>  
 <span data-ttu-id="3d882-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d882-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d882-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d882-110">Remarks</span></span>  
 <span data-ttu-id="3d882-111">`ICeeFileGen`Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyaları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d882-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="3d882-112">Sona erdiğinde nesneyi yok etmek için [Destroııceefilegen](destroyiceefilegen-function.md) işlevini çağırın `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="3d882-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d882-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d882-113">Requirements</span></span>  
 <span data-ttu-id="3d882-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d882-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d882-115">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="3d882-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="3d882-116">**Kitaplık:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="3d882-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="3d882-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d882-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d882-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d882-118">See also</span></span>

- [<span data-ttu-id="3d882-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3d882-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
