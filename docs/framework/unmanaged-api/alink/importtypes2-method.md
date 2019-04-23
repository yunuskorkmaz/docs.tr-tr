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
ms.openlocfilehash: f14822a58f3982d6f9fee1328c10b960657c056f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098474"
---
# <a name="importtypes2-method"></a><span data-ttu-id="c4178-102">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4178-102">ImportTypes2 Method</span></span>
<span data-ttu-id="c4178-103">İçeri aktarma türü başlatır.</span><span class="sxs-lookup"><span data-stu-id="c4178-103">Initiates the import of types.</span></span> <span data-ttu-id="c4178-104">Türleri aracılığıyla alınan her bir kapsamdan almaya başlamak için bu yöntemi çağırın [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c4178-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4178-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4178-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4178-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4178-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c4178-107">Bütünleştirilmiş kod içine alınacağı kimliği.</span><span class="sxs-lookup"><span data-stu-id="c4178-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c4178-108">Dosyaya alınacağı kimliği.</span><span class="sxs-lookup"><span data-stu-id="c4178-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c4178-109">Alınacağı sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="c4178-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="c4178-110">Numaralandırıcı tanıtıcı türleri için verilen kapsam içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="c4178-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c4178-111">İsteğe bağlı olarak alan [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c4178-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="c4178-112">İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c4178-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4178-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4178-113">Return Value</span></span>  
 <span data-ttu-id="c4178-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4178-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4178-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4178-115">Requirements</span></span>  
 <span data-ttu-id="c4178-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c4178-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4178-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4178-117">See also</span></span>

- [<span data-ttu-id="c4178-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4178-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c4178-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4178-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c4178-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c4178-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
