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
ms.openlocfilehash: da38c04f5d67dc0220b1828ba0e5cdeb84346bb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137949"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="7b2d0-102">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="7b2d0-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="7b2d0-103">Belirtilen meta veri imzası dosyasının özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b2d0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7b2d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b2d0-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="7b2d0-106">[in] `mdFile` Özelliklerini almak istediğiniz dosyayı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="7b2d0-107">[out] Basit dosya adı.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7b2d0-108">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="7b2d0-109">[out] Gerçekte döndürülen geniş karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="7b2d0-110">[out] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="7b2d0-111">Dosyanın SHA-1 algoritmasını kullanarak karma budur.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="7b2d0-112">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="7b2d0-113">[out] Bir dosya için geçerli bir meta veri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="7b2d0-114">Bir veya daha fazla flags değeri birleşimidir [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b2d0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b2d0-115">Requirements</span></span>  
 <span data-ttu-id="7b2d0-116">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b2d0-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b2d0-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7b2d0-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b2d0-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7b2d0-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7b2d0-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7b2d0-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7b2d0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b2d0-120">See also</span></span>

- [<span data-ttu-id="7b2d0-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b2d0-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
