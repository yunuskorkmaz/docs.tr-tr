---
title: ImportTypes2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7fddfffed499537f5746998a94a3ef32d035685
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741608"
---
# <a name="importtypes2-method"></a><span data-ttu-id="edaee-102">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="edaee-102">ImportTypes2 Method</span></span>
<span data-ttu-id="edaee-103">İçeri aktarma türü başlatır.</span><span class="sxs-lookup"><span data-stu-id="edaee-103">Initiates the import of types.</span></span> <span data-ttu-id="edaee-104">Türleri aracılığıyla alınan her bir kapsamdan almaya başlamak için bu yöntemi çağırın [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="edaee-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edaee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edaee-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="edaee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edaee-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="edaee-107">Bütünleştirilmiş kod içine alınacağı kimliği.</span><span class="sxs-lookup"><span data-stu-id="edaee-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="edaee-108">Dosyaya alınacağı kimliği.</span><span class="sxs-lookup"><span data-stu-id="edaee-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="edaee-109">Alınacağı sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="edaee-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="edaee-110">Numaralandırıcı tanıtıcı türleri için verilen kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="edaee-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="edaee-111">İsteğe bağlı olarak alan [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="edaee-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="edaee-112">İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="edaee-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edaee-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="edaee-113">Return Value</span></span>  
 <span data-ttu-id="edaee-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="edaee-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edaee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edaee-115">Requirements</span></span>  
 <span data-ttu-id="edaee-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="edaee-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edaee-117">See also</span></span>

- [<span data-ttu-id="edaee-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edaee-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="edaee-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edaee-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="edaee-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="edaee-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
