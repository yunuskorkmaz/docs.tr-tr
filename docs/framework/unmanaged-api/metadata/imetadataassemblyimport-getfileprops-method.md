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
ms.openlocfilehash: 0b9ff2716cc0bc32c81fe6fcdd4e6c367d4d835f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718185"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="1957e-102">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1957e-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="1957e-103">Belirtilen meta veri imzasıyla dosyanın özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="1957e-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1957e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1957e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1957e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1957e-105">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="1957e-106">'ndaki `mdFile` Özelliklerinin alınacağı dosyayı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1957e-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="1957e-107">dışı Dosyanın basit adı.</span><span class="sxs-lookup"><span data-stu-id="1957e-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1957e-108">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="1957e-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1957e-109">dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="1957e-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="1957e-110">dışı Karma değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1957e-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="1957e-111">Bu, dosyanın SHA-1 algoritmasını kullanan karmadır.</span><span class="sxs-lookup"><span data-stu-id="1957e-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="1957e-112">dışı Döndürülen karma değerindeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="1957e-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="1957e-113">dışı Bir dosyaya uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1957e-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="1957e-114">Flags değeri bir veya daha fazla [CorFileFlags](corfileflags-enumeration.md) değerinin birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="1957e-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1957e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1957e-115">Requirements</span></span>  

 <span data-ttu-id="1957e-116">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1957e-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1957e-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1957e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1957e-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1957e-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1957e-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1957e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1957e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1957e-120">See also</span></span>

- [<span data-ttu-id="1957e-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1957e-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
