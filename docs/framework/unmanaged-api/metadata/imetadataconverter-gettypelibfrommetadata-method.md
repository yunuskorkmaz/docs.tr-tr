---
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
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177627"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="29b0f-102">IMetaDataConverter::GetTypeLibFromMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29b0f-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="29b0f-103">Belirtilen kitaplık `ITypeLib` ve modül adlarına sahip tür kitaplığını temsil eden bir örneğin işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="29b0f-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29b0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29b0f-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="29b0f-106">[içinde] Tür kitaplığı modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="29b0f-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="29b0f-107">[içinde] Tür kitaplığın adı.</span><span class="sxs-lookup"><span data-stu-id="29b0f-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="29b0f-108">[çıkış] Tür kitaplığını temsil eden `ITypeLib` örneğin adresini alan bir konuma işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29b0f-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b0f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29b0f-109">Requirements</span></span>  
 <span data-ttu-id="29b0f-110">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b0f-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b0f-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29b0f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29b0f-112">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="29b0f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29b0f-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b0f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b0f-114">See also</span></span>

- [<span data-ttu-id="29b0f-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29b0f-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
