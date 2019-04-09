---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2ab06419491093a2de41d2ef25d16c01c03ebaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158853"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="bd729-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd729-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="bd729-103">Geçerli derleme bildiriminde atıf yapılan dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="bd729-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd729-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd729-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd729-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd729-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bd729-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd729-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bd729-107">Bu, bu yöntemin ilk çağrı için null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd729-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="bd729-108">[out] Depolamak için kullanılan bir dizi `mdFile` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="bd729-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bd729-109">[in] En fazla `mdFile` yerleştirilebilir belirteçleri `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="bd729-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bd729-110">[out] Sayısını `mdFile` belirteçleri gerçekten yerleştirilen `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="bd729-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd729-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd729-111">Return Value</span></span>  
  
|<span data-ttu-id="bd729-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd729-112">HRESULT</span></span>|<span data-ttu-id="bd729-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd729-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumFiles` <span data-ttu-id="bd729-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bd729-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bd729-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bd729-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bd729-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bd729-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd729-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd729-117">Requirements</span></span>  
 <span data-ttu-id="bd729-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd729-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd729-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bd729-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd729-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bd729-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bd729-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bd729-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd729-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd729-122">See also</span></span>

- [<span data-ttu-id="bd729-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd729-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
