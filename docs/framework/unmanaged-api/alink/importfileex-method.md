---
description: 'Daha fazla bilgi edinin: ImportFileEx yöntemi'
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
ms.openlocfilehash: a8a7e5a142091bf7cc93f50a4ae20c59d800f3ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718024"
---
# <a name="importfileex-method"></a><span data-ttu-id="5f4c8-103">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f4c8-103">ImportFileEx Method</span></span>

<span data-ttu-id="5f4c8-104">Belirtilen derleme veya ilişkisiz modül içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-104">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4c8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f4c8-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5f4c8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f4c8-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="5f4c8-107">İçinden içeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-107">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5f4c8-108">Hedef dosyanın isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-108">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5f4c8-109">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5f4c8-110">[OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-110">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5f4c8-111">İçeri aktarılmakta olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-111">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5f4c8-112">Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-112">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5f4c8-113">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-113">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5f4c8-114">İçeri aktarılan dosya ve/veya kapsamların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-114">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f4c8-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5f4c8-115">Return Value</span></span>  

 <span data-ttu-id="5f4c8-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4c8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f4c8-117">Requirements</span></span>  

 <span data-ttu-id="5f4c8-118">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4c8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f4c8-119">See also</span></span>

- [<span data-ttu-id="5f4c8-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f4c8-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5f4c8-121">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f4c8-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5f4c8-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="5f4c8-122">ALink API</span></span>](index.md)
