---
title: IAssemblyCacheItem::CreateStream Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079168"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="c3713-102">IAssemblyCacheItem::CreateStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3713-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="c3713-103">Belirtilen ada ve biçimi bir akış oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3713-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3713-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3713-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c3713-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3713-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="c3713-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c3713-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="c3713-107">[in] Oluşturulacak Akış adı.</span><span class="sxs-lookup"><span data-stu-id="c3713-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="c3713-108">[in] Akışla için dosya biçimi.</span><span class="sxs-lookup"><span data-stu-id="c3713-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="c3713-109">[in] Fusion.idl içinde tanımlanan özel biçim bayrakları.</span><span class="sxs-lookup"><span data-stu-id="c3713-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="c3713-110">[out] Döndürülen adresini bir işaretçiye [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneği.</span><span class="sxs-lookup"><span data-stu-id="c3713-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="c3713-111">[, isteğe bağlı] En büyük boyutu tarafından başvuruda bulunulan akışın `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="c3713-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3713-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3713-112">Requirements</span></span>  
 <span data-ttu-id="c3713-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3713-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3713-114">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c3713-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c3713-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3713-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3713-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3713-116">See Also</span></span>  
 [<span data-ttu-id="c3713-117">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3713-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
