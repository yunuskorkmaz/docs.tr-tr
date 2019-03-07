---
title: ImportFileEx2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d09877d9ca8dde601d2b515bce63bfdca53b6ab0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498139"
---
# <a name="importfileex2-method"></a><span data-ttu-id="13b87-102">ImportFileEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13b87-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="13b87-103">Derlemeler ve bağlantısız modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="13b87-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="13b87-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosyanın diskte mevcut değilse bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="13b87-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b87-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13b87-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="13b87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13b87-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="13b87-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="13b87-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="13b87-108">Hedef dosya isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="13b87-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="13b87-109">İsteğe bağlı içeri aktarma kapsamı [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="13b87-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="13b87-110">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="13b87-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="13b87-111">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="13b87-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="13b87-112">Derleme veya dosya için benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="13b87-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="13b87-113">Derleme içeri aktarma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="13b87-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="13b87-114">Dosyanın bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="13b87-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="13b87-115">Dosyaları ve/veya içe kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="13b87-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13b87-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13b87-116">Return Value</span></span>  
 <span data-ttu-id="13b87-117">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="13b87-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13b87-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13b87-118">Requirements</span></span>  
 <span data-ttu-id="13b87-119">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="13b87-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b87-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13b87-120">See also</span></span>
- [<span data-ttu-id="13b87-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13b87-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="13b87-122">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13b87-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="13b87-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="13b87-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
