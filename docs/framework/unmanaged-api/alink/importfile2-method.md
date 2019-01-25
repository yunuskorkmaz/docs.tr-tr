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
ms.openlocfilehash: b3c145bae61922894f4893d532923319ccf16f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499018"
---
# <a name="importfile2-method"></a><span data-ttu-id="5bf42-102">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bf42-102">ImportFile2 Method</span></span>
<span data-ttu-id="5bf42-103">Derlemeler ve bağlantısız modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="5bf42-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosyanın diskte mevcut değilse bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf42-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bf42-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5bf42-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bf42-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5bf42-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="5bf42-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5bf42-108">Bütünleştirilmiş kod içine bağlı olarak dosyayı yeniden adlandırmak için kullanılabilecek isteğe bağlı bir çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="5bf42-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="5bf42-109">İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5bf42-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5bf42-110">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5bf42-111">Dosya veya derleme Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5bf42-112">Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5bf42-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5bf42-113">Dosyanın bir derleme değilse null değerini DÖNDÜRÜR.</span><span class="sxs-lookup"><span data-stu-id="5bf42-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5bf42-114">Bulunan dosyaları ve/veya içe kapsamları alır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bf42-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bf42-115">Return Value</span></span>  
 <span data-ttu-id="5bf42-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5bf42-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf42-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bf42-117">Requirements</span></span>  
 <span data-ttu-id="5bf42-118">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf42-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bf42-119">See also</span></span>
- [<span data-ttu-id="5bf42-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bf42-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5bf42-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bf42-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5bf42-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="5bf42-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
