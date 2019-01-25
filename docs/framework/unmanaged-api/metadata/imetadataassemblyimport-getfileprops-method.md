---
title: IMetaDataAssemblyImport::GetFileProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59dad67db9f9f9184a139f848020cf866a3a6771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716836"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="881b5-102">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="881b5-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="881b5-103">Belirtilen meta veri imzası dosyasının özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="881b5-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="881b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="881b5-104">Syntax</span></span>  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="881b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="881b5-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="881b5-106">[in] `mdFile` Özelliklerini almak istediğiniz dosyayı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="881b5-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="881b5-107">[out] Basit dosya adı.</span><span class="sxs-lookup"><span data-stu-id="881b5-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="881b5-108">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="881b5-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="881b5-109">[out] Gerçekte döndürülen geniş karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="881b5-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="881b5-110">[out] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="881b5-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="881b5-111">Dosyanın SHA-1 algoritmasını kullanarak karma budur.</span><span class="sxs-lookup"><span data-stu-id="881b5-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="881b5-112">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="881b5-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="881b5-113">[out] Bir dosya için geçerli bir meta veri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="881b5-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="881b5-114">Bir veya daha fazla flags değeri birleşimidir [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="881b5-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="881b5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="881b5-115">Requirements</span></span>  
 <span data-ttu-id="881b5-116">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="881b5-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="881b5-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="881b5-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="881b5-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="881b5-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="881b5-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="881b5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881b5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="881b5-120">See also</span></span>
- [<span data-ttu-id="881b5-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="881b5-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
