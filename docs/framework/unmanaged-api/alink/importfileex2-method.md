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
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776974"
---
# <a name="importfileex2-method"></a><span data-ttu-id="5716f-102">ImportFileEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5716f-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="5716f-103">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5716f-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="5716f-104">Bu yöntem [ImportFile yöntemine](importfile-method.md)benzer, ancak içeri aktarılan dosya diskte mevcut olmasa bile çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="5716f-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5716f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5716f-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5716f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5716f-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5716f-107">İçeri aktarılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5716f-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5716f-108">Hedef dosyanın isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="5716f-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="5716f-109">İsteğe bağlı içeri aktarma kapsamı [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5716f-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5716f-110">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5716f-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5716f-111">[OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5716f-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5716f-112">Derleme veya dosya için benzersiz KIMLIĞI alır.</span><span class="sxs-lookup"><span data-stu-id="5716f-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5716f-113">Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="5716f-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="5716f-114">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="5716f-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5716f-115">İçeri aktarılan dosya ve/veya kapsamların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5716f-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5716f-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5716f-116">Return Value</span></span>  
 <span data-ttu-id="5716f-117">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5716f-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5716f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5716f-118">Requirements</span></span>  
 <span data-ttu-id="5716f-119">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5716f-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5716f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5716f-120">See also</span></span>

- [<span data-ttu-id="5716f-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5716f-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5716f-122">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5716f-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5716f-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="5716f-123">ALink API</span></span>](index.md)
