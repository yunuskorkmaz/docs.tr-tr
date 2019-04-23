---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c6b9e1239dc1baed9428d4fe967eb8274a9304
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206037"
---
# <a name="getscope2-method"></a><span data-ttu-id="2a7a8-102">GetScope2 Metodu</span><span class="sxs-lookup"><span data-stu-id="2a7a8-102">GetScope2 Method</span></span>
<span data-ttu-id="2a7a8-103">Bir içeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a7a8-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="2a7a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a7a8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2a7a8-106">Hedef derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2a7a8-107">Alınacağı dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="2a7a8-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="2a7a8-109">İşaretçi alır [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) Belirtilen kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a7a8-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a7a8-110">Return Value</span></span>  
 <span data-ttu-id="2a7a8-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a7a8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a7a8-112">Requirements</span></span>  
 <span data-ttu-id="2a7a8-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7a8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a7a8-114">See also</span></span>

- [<span data-ttu-id="2a7a8-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a7a8-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2a7a8-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a7a8-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2a7a8-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="2a7a8-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
