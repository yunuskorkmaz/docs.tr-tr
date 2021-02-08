---
description: ': IMetaDataConverter:: GetTypeLibFromMetaData metodu hakkında daha fazla bilgi edinin'
title: IMetaDataConverter::GetTypeLibFromMetaData Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: 5eecc87f938740366b7938d6ec3d1460ebcfb7eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789274"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="53049-103">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53049-103">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>

<span data-ttu-id="53049-104">`ITypeLib`Belirtilen kitaplık ve modül adlarına sahip tür kitaplığını temsil eden bir örneğe yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="53049-104">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53049-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53049-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53049-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53049-106">Parameters</span></span>  

 `strModule`  
 <span data-ttu-id="53049-107">'ndaki Tür kitaplığının modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="53049-107">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="53049-108">'ndaki Tür kitaplığının adı.</span><span class="sxs-lookup"><span data-stu-id="53049-108">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="53049-109">dışı Tür kitaplığını temsil eden örneğin adresini alan konuma yönelik bir işaretçi `ITypeLib` .</span><span class="sxs-lookup"><span data-stu-id="53049-109">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53049-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53049-110">Requirements</span></span>  

 <span data-ttu-id="53049-111">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53049-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53049-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="53049-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53049-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="53049-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53049-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53049-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53049-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53049-115">See also</span></span>

- [<span data-ttu-id="53049-116">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53049-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
