---
description: ': IMetaDataImport2:: GetMethodSpecProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 77f3f78905d1f7f44af0e9c7a75746b4e5b6e684
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688656"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="e410b-103">IMetaDataImport2::GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e410b-103">IMetaDataImport2::GetMethodSpecProps Method</span></span>

<span data-ttu-id="e410b-104">Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="e410b-104">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e410b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e410b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e410b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e410b-106">Parameters</span></span>  

 `mi`  
 <span data-ttu-id="e410b-107">'ndaki Metodun örneklenmesini temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="e410b-107">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="e410b-108">dışı Yöntem tanımını temsil eden MethodDef veya MethodRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e410b-108">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="e410b-109">dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e410b-109">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="e410b-110">dışı Bayt cinsinden boyutu `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="e410b-110">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e410b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e410b-111">Requirements</span></span>  

 <span data-ttu-id="e410b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e410b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e410b-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e410b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e410b-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e410b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e410b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e410b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e410b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e410b-116">See also</span></span>

- [<span data-ttu-id="e410b-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e410b-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="e410b-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e410b-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
