---
title: ImportFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88006703ba4a491ae458868a1431be618d37252a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471205"
---
# <a name="importfile2-method"></a><span data-ttu-id="d000e-102">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d000e-102">ImportFile2 Method</span></span>
<span data-ttu-id="d000e-103">Derlemeler ve bağlantısız modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="d000e-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="d000e-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosyanın diskte mevcut değilse bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="d000e-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d000e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d000e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d000e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d000e-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d000e-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="d000e-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="d000e-108">Bütünleştirilmiş kod içine bağlı olarak dosyayı yeniden adlandırmak için kullanılabilecek isteğe bağlı bir çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="d000e-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="d000e-109">İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d000e-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="d000e-110">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d000e-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="d000e-111">Dosya veya derleme Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="d000e-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="d000e-112">Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d000e-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="d000e-113">Dosyanın bir derleme değilse null değerini DÖNDÜRÜR.</span><span class="sxs-lookup"><span data-stu-id="d000e-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="d000e-114">Bulunan dosyaları ve/veya içe kapsamları alır.</span><span class="sxs-lookup"><span data-stu-id="d000e-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d000e-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d000e-115">Return Value</span></span>  
 <span data-ttu-id="d000e-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d000e-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d000e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d000e-117">Requirements</span></span>  
 <span data-ttu-id="d000e-118">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d000e-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d000e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d000e-119">See also</span></span>
- [<span data-ttu-id="d000e-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d000e-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d000e-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d000e-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d000e-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="d000e-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
