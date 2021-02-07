---
description: 'Şu konuda daha fazla bilgi edinin: CreateICeeFileGen Işlevi'
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
ms.openlocfilehash: 10aefaad4dd1173e4ef55f727371bab508e2d40c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716939"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="57d5f-103">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="57d5f-103">CreateICeeFileGen Function</span></span>

<span data-ttu-id="57d5f-104">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57d5f-104">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="57d5f-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="57d5f-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57d5f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57d5f-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57d5f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57d5f-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="57d5f-108">dışı Yeni bir nesnenin adresine yönelik bir işaretçi `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="57d5f-108">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57d5f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57d5f-109">Return Value</span></span>  

 <span data-ttu-id="57d5f-110">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="57d5f-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57d5f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57d5f-111">Remarks</span></span>  

 <span data-ttu-id="57d5f-112">`ICeeFileGen`Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyaları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57d5f-112">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="57d5f-113">Sona erdiğinde nesneyi yok etmek için [Destroııceefilegen](destroyiceefilegen-function.md) işlevini çağırın `ICeeFileGen` .</span><span class="sxs-lookup"><span data-stu-id="57d5f-113">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57d5f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57d5f-114">Requirements</span></span>  

 <span data-ttu-id="57d5f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57d5f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57d5f-116">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="57d5f-116">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="57d5f-117">**Kitaplık:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="57d5f-117">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="57d5f-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57d5f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d5f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57d5f-119">See also</span></span>

- [<span data-ttu-id="57d5f-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="57d5f-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
