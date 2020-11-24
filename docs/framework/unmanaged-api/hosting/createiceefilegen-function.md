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
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673338"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="ff364-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="ff364-102">CreateICeeFileGen Function</span></span>

<span data-ttu-id="ff364-103">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff364-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="ff364-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ff364-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff364-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ff364-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff364-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff364-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="ff364-107">dışı Yeni bir nesnenin adresine yönelik bir işaretçi `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="ff364-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff364-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ff364-108">Return Value</span></span>  

 <span data-ttu-id="ff364-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff364-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff364-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff364-110">Remarks</span></span>  

 <span data-ttu-id="ff364-111">`ICeeFileGen`Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyaları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff364-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="ff364-112">Sona erdiğinde nesneyi yok etmek için [Destroııceefilegen](destroyiceefilegen-function.md) işlevini çağırın `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="ff364-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff364-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff364-113">Requirements</span></span>  

 <span data-ttu-id="ff364-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff364-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff364-115">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="ff364-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="ff364-116">**Kitaplık:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="ff364-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="ff364-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff364-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff364-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff364-118">See also</span></span>

- [<span data-ttu-id="ff364-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ff364-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
