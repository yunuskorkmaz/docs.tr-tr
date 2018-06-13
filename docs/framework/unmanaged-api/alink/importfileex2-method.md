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
ms.openlocfilehash: be6332c76b3dae9c02e1a939286b70438ee14cfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400685"
---
# <a name="importfileex2-method"></a><span data-ttu-id="02cd4-102">ImportFileEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02cd4-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="02cd4-103">Derlemeler ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="02cd4-104">Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosya diskte yok olsa bile çalışır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02cd4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02cd4-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="02cd4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02cd4-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="02cd4-107">İçeri aktarılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="02cd4-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="02cd4-108">Hedef dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="02cd4-109">İsteğe bağlı alma kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02cd4-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="02cd4-110">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="02cd4-111">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="02cd4-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="02cd4-112">Derleme veya dosya için benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="02cd4-113">Derleme alma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02cd4-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="02cd4-114">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="02cd4-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="02cd4-115">Dosyaları ve/veya içeri kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="02cd4-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02cd4-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="02cd4-116">Return Value</span></span>  
 <span data-ttu-id="02cd4-117">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="02cd4-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02cd4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02cd4-118">Requirements</span></span>  
 <span data-ttu-id="02cd4-119">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02cd4-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02cd4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02cd4-120">See Also</span></span>  
 [<span data-ttu-id="02cd4-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02cd4-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="02cd4-122">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02cd4-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="02cd4-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="02cd4-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
