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
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98273307003485202d8c12d5c27fda04ff5a0ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629890"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="52dd9-102">IAssemblyCacheItem::CreateStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52dd9-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="52dd9-103">Belirtilen ada ve biçimi bir akış oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52dd9-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="52dd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52dd9-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="52dd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52dd9-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="52dd9-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="52dd9-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="52dd9-107">[in] Oluşturulacak Akış adı.</span><span class="sxs-lookup"><span data-stu-id="52dd9-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="52dd9-108">[in] Akışla için dosya biçimi.</span><span class="sxs-lookup"><span data-stu-id="52dd9-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="52dd9-109">[in] Fusion.idl içinde tanımlanan özel biçim bayrakları.</span><span class="sxs-lookup"><span data-stu-id="52dd9-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="52dd9-110">[out] Döndürülen adresini bir işaretçiye [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneği.</span><span class="sxs-lookup"><span data-stu-id="52dd9-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="52dd9-111">[, isteğe bağlı] En büyük boyutu tarafından başvuruda bulunulan akışın `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="52dd9-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="52dd9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52dd9-112">Requirements</span></span>

<span data-ttu-id="52dd9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52dd9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="52dd9-114">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="52dd9-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="52dd9-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52dd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="52dd9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52dd9-116">See also</span></span>

- [<span data-ttu-id="52dd9-117">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52dd9-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
