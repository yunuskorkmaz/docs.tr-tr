---
title: IMetaDataAssemblyImport::GetFileProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="8d0a4-102">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="8d0a4-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="8d0a4-103">Belirtilen meta veri imzayla dosyasının özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d0a4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8d0a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d0a4-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="8d0a4-106">[in] `mdFile` Özellikleri almak istediğiniz dosyayı temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d0a4-107">[out] Dosyanın basit adı.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8d0a4-108">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8d0a4-109">[out] Gerçekte döndürülen geniş karakter sayısı `szName`.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="8d0a4-110">[out] Karma değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="8d0a4-111">Dosyanın SHA-1 algoritmasını kullanarak karma budur.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="8d0a4-112">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="8d0a4-113">[out] Bir dosyaya uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="8d0a4-114">Bir veya birden çok bayrak değeri birleşimidir [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d0a4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d0a4-115">Requirements</span></span>  
 <span data-ttu-id="8d0a4-116">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d0a4-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0a4-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d0a4-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d0a4-118">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8d0a4-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d0a4-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d0a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0a4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d0a4-120">See Also</span></span>  
 [<span data-ttu-id="8d0a4-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d0a4-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
