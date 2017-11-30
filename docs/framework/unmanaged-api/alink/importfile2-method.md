---
title: "ImportFile2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a><span data-ttu-id="02694-102">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02694-102">ImportFile2 Method</span></span>
<span data-ttu-id="02694-103">Derlemeler ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="02694-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="02694-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosya diskte yok olsa bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="02694-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02694-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02694-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02694-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02694-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="02694-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="02694-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="02694-108">Derlemeye bağlı olarak dosyayı yeniden adlandırmak için kullanılan isteğe bağlı çıktı dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="02694-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="02694-109">İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02694-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="02694-110">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02694-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="02694-111">Dosya veya derleme Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="02694-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="02694-112">Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02694-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="02694-113">Dosya bir derleme değilse null değerini DÖNDÜRÜR.</span><span class="sxs-lookup"><span data-stu-id="02694-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="02694-114">Bulunan dosyaları ve/veya içeri kapsamları alır.</span><span class="sxs-lookup"><span data-stu-id="02694-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02694-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="02694-115">Return Value</span></span>  
 <span data-ttu-id="02694-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="02694-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02694-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02694-117">Requirements</span></span>  
 <span data-ttu-id="02694-118">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02694-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02694-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02694-119">See Also</span></span>  
 [<span data-ttu-id="02694-120">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="02694-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="02694-121">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="02694-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="02694-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="02694-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
