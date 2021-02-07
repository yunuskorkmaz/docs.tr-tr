---
description: ': IMetaDataAssemblyImport:: EnumFiles yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataAssemblyImport::EnumFiles Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 25282edd081e937e4c84334f9f004e201b9db46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671028"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="888f1-103">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="888f1-103">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="888f1-104">Geçerli derleme bildiriminde başvurulan dosyaları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="888f1-104">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="888f1-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="888f1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="888f1-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="888f1-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="888f1-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="888f1-108">Bu yöntemin ilk çağrısı için bu bir null değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="888f1-108">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="888f1-109">dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdFile` .</span><span class="sxs-lookup"><span data-stu-id="888f1-109">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="888f1-110">'ndaki `mdFile` İçine yerleştirilebilecek en fazla belirteç sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="888f1-110">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="888f1-111">dışı `mdFile` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="888f1-111">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="888f1-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="888f1-112">Return Value</span></span>  
  
|<span data-ttu-id="888f1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="888f1-113">HRESULT</span></span>|<span data-ttu-id="888f1-114">Description</span><span class="sxs-lookup"><span data-stu-id="888f1-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="888f1-115">`EnumFiles` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="888f1-115">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="888f1-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="888f1-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="888f1-117">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="888f1-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="888f1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="888f1-118">Requirements</span></span>  

 <span data-ttu-id="888f1-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="888f1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="888f1-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="888f1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="888f1-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="888f1-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="888f1-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="888f1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888f1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="888f1-123">See also</span></span>

- [<span data-ttu-id="888f1-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="888f1-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
