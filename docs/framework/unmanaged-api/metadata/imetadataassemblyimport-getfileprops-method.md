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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175986"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="8c79a-102">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="8c79a-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="8c79a-103">Belirtilen meta veri imzasıyla dosyanın özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="8c79a-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c79a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c79a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="8c79a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c79a-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="8c79a-106">[içinde] Özellikleri `mdFile` almak için dosyayı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8c79a-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c79a-107">[çıkış] Dosyanın basit adı.</span><span class="sxs-lookup"><span data-stu-id="8c79a-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8c79a-108">[içinde] Boyutu, geniş chars, `szName`ve .</span><span class="sxs-lookup"><span data-stu-id="8c79a-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8c79a-109">[çıkış] Geniş karakter sayısı aslında döndü `szName`.</span><span class="sxs-lookup"><span data-stu-id="8c79a-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="8c79a-110">[çıkış] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c79a-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="8c79a-111">Bu, SHA-1 algoritmasını kullanarak dosyanın karma.</span><span class="sxs-lookup"><span data-stu-id="8c79a-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="8c79a-112">[çıkış] Döndürülen karma değerdeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="8c79a-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="8c79a-113">[çıkış] Bir dosyaya uygulanan meta verileri açıklayan bayraklar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c79a-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="8c79a-114">Bayrak değeri, bir veya daha fazla [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerinin bir leşimidir.</span><span class="sxs-lookup"><span data-stu-id="8c79a-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c79a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c79a-115">Requirements</span></span>  
 <span data-ttu-id="8c79a-116">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c79a-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c79a-117">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c79a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c79a-118">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8c79a-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c79a-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c79a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c79a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c79a-120">See also</span></span>

- [<span data-ttu-id="8c79a-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c79a-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
