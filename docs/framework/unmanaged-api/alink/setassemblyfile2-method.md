---
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d96881ce35dca1ee7a196507ef8d81a565eed82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741505"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="25701-102">SetAssemblyFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25701-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="25701-103">Yeni bir derleme seçeneklerini ve adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="25701-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="25701-104">İlişkisiz modüller oluşturmak, bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="25701-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25701-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25701-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="25701-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25701-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="25701-107">Bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="25701-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="25701-108">[Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) bu dosya için arabirim.</span><span class="sxs-lookup"><span data-stu-id="25701-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="25701-109">Seçenekleri temsil ettiği [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="25701-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="25701-110">Yapılandırılan bir derleme için benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="25701-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25701-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25701-111">Return Value</span></span>  
 <span data-ttu-id="25701-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="25701-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25701-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25701-113">Requirements</span></span>  
 <span data-ttu-id="25701-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="25701-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25701-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25701-115">See also</span></span>

- [<span data-ttu-id="25701-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25701-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="25701-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25701-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="25701-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="25701-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
