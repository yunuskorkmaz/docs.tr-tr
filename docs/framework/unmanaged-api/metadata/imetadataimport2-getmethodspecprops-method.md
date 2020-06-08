---
title: IMetaDataImport2::GetMethodSpecProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490451"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="bac56-102">IMetaDataImport2::GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bac56-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="bac56-103">Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="bac56-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac56-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bac56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="bac56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bac56-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="bac56-106">'ndaki Metodun örneklenmesini temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="bac56-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="bac56-107">dışı Yöntem tanımını temsil eden MethodDef veya MethodRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bac56-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="bac56-108">dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bac56-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="bac56-109">dışı Bayt cinsinden boyutu `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="bac56-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac56-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bac56-110">Requirements</span></span>  
 <span data-ttu-id="bac56-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac56-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac56-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bac56-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bac56-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bac56-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bac56-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac56-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bac56-115">See also</span></span>

- [<span data-ttu-id="bac56-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bac56-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="bac56-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bac56-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
