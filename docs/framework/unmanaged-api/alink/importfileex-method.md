---
title: "ImportFileEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71a7bc1ba9f23f1c581ca3528752e04003d9857c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="47bc0-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47bc0-102">ImportFileEx Method</span></span>
<span data-ttu-id="47bc0-103">İçeri aktarmalar derleme veya ilişkisiz modülü gösterilir.</span><span class="sxs-lookup"><span data-stu-id="47bc0-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47bc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47bc0-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47bc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47bc0-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="47bc0-106">İçeri aktarılacak dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="47bc0-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="47bc0-107">Hedef dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="47bc0-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="47bc0-108">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47bc0-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="47bc0-109">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="47bc0-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="47bc0-110">İçeri aktarılan dosya Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="47bc0-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="47bc0-111">Derleme alma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="47bc0-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="47bc0-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="47bc0-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="47bc0-113">İçeri aktarılan dosyaları ve/veya kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="47bc0-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47bc0-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47bc0-114">Return Value</span></span>  
 <span data-ttu-id="47bc0-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="47bc0-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47bc0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47bc0-116">Requirements</span></span>  
 <span data-ttu-id="47bc0-117">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47bc0-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47bc0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47bc0-118">See Also</span></span>  
 [<span data-ttu-id="47bc0-119">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="47bc0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="47bc0-120">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="47bc0-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="47bc0-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="47bc0-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
