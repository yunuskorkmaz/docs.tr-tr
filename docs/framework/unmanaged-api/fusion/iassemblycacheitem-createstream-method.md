---
title: IAssemblyCacheItem::CreateStream Yöntemi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 726efe69f67627c48108b6b1ece9fe52f34a91c1
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="acb0d-102">IAssemblyCacheItem::CreateStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acb0d-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="acb0d-103">Belirtilen ada ve biçimi ile bir akış oluşturur.</span><span class="sxs-lookup"><span data-stu-id="acb0d-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acb0d-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acb0d-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="acb0d-106">[in] Fusion.idl içinde tanımlı bayrak.</span><span class="sxs-lookup"><span data-stu-id="acb0d-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="acb0d-107">[in] Oluşturulacak Akış adı.</span><span class="sxs-lookup"><span data-stu-id="acb0d-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="acb0d-108">[in] Akışını dosya biçimi.</span><span class="sxs-lookup"><span data-stu-id="acb0d-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="acb0d-109">[in] Fusion.idl içinde tanımlanan biçimi özgü bayraklar.</span><span class="sxs-lookup"><span data-stu-id="acb0d-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="acb0d-110">[out] Döndürülen adresini gösteren bir işaretçi [IStream](https://msdn.microsoft.com/library/aa380034.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="acb0d-110">[out] A pointer to the address of the returned [IStream](https://msdn.microsoft.com/library/aa380034.aspx) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="acb0d-111">[isteğe bağlı] En büyük boyutu tarafından başvuruda bulunulan akışın `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="acb0d-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb0d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acb0d-112">Requirements</span></span>  
 <span data-ttu-id="acb0d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acb0d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb0d-114">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="acb0d-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="acb0d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb0d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acb0d-116">See Also</span></span>  
 [<span data-ttu-id="acb0d-117">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acb0d-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
