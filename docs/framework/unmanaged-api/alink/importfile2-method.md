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
ms.openlocfilehash: 61bc7783823408164ae2b073e097a0e85e193be6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401248"
---
# <a name="importfile2-method"></a><span data-ttu-id="ff1bb-102">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff1bb-102">ImportFile2 Method</span></span>
<span data-ttu-id="ff1bb-103">Derlemeler ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="ff1bb-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosya diskte yok olsa bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff1bb-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ff1bb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff1bb-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="ff1bb-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="ff1bb-108">Derlemeye bağlı olarak dosyayı yeniden adlandırmak için kullanılan isteğe bağlı çıktı dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="ff1bb-109">İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="ff1bb-110">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="ff1bb-111">Dosya veya derleme Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="ff1bb-112">Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="ff1bb-113">Dosya bir derleme değilse null değerini DÖNDÜRÜR.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="ff1bb-114">Bulunan dosyaları ve/veya içeri kapsamları alır.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff1bb-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ff1bb-115">Return Value</span></span>  
 <span data-ttu-id="ff1bb-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1bb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff1bb-117">Requirements</span></span>  
 <span data-ttu-id="ff1bb-118">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1bb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff1bb-119">See Also</span></span>  
 [<span data-ttu-id="ff1bb-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1bb-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ff1bb-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1bb-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ff1bb-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="ff1bb-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
