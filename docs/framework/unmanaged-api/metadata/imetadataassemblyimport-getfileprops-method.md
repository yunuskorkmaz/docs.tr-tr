---
description: ': IMetaDataAssemblyImport:: GetFileProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6814fee7edf5478a1ce2cf2b81d8f16fa62cd3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784112"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="2422b-103">IMetaDataAssemblyImport::GetFileProps Metodu</span><span class="sxs-lookup"><span data-stu-id="2422b-103">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="2422b-104">Belirtilen meta veri imzasıyla dosyanın özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="2422b-104">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2422b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2422b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2422b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2422b-106">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="2422b-107">'ndaki `mdFile` Özelliklerinin alınacağı dosyayı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2422b-107">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="2422b-108">dışı Dosyanın basit adı.</span><span class="sxs-lookup"><span data-stu-id="2422b-108">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2422b-109">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="2422b-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2422b-110">dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="2422b-110">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="2422b-111">dışı Karma değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2422b-111">[out] A pointer to the hash value.</span></span> <span data-ttu-id="2422b-112">Bu, dosyanın SHA-1 algoritmasını kullanan karmadır.</span><span class="sxs-lookup"><span data-stu-id="2422b-112">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="2422b-113">dışı Döndürülen karma değerindeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="2422b-113">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="2422b-114">dışı Bir dosyaya uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2422b-114">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="2422b-115">Flags değeri bir veya daha fazla [CorFileFlags](corfileflags-enumeration.md) değerinin birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="2422b-115">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2422b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2422b-116">Requirements</span></span>  

 <span data-ttu-id="2422b-117">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2422b-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2422b-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2422b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2422b-119">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2422b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2422b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2422b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2422b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2422b-121">See also</span></span>

- [<span data-ttu-id="2422b-122">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2422b-122">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
