---
title: ImportFileEx Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fe73bef50a32c3ff03f2a2754f665cc95018a4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403000"
---
# <a name="importfileex-method"></a><span data-ttu-id="1aa27-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa27-102">ImportFileEx Method</span></span>
<span data-ttu-id="1aa27-103">İçeri aktarmalar derleme veya ilişkisiz modülü gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1aa27-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1aa27-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1aa27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1aa27-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="1aa27-106">İçeri aktarılacak dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="1aa27-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="1aa27-107">Hedef dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1aa27-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="1aa27-108">TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1aa27-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="1aa27-109">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="1aa27-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="1aa27-110">İçeri aktarılan dosya Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1aa27-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="1aa27-111">Derleme alma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1aa27-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="1aa27-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1aa27-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="1aa27-113">İçeri aktarılan dosyaları ve/veya kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1aa27-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aa27-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1aa27-114">Return Value</span></span>  
 <span data-ttu-id="1aa27-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="1aa27-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa27-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1aa27-116">Requirements</span></span>  
 <span data-ttu-id="1aa27-117">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1aa27-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa27-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1aa27-118">See Also</span></span>  
 [<span data-ttu-id="1aa27-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aa27-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1aa27-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aa27-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1aa27-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="1aa27-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
