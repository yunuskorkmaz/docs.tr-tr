---
description: 'Daha fazla bilgi edinin: ImportFileEx2 yöntemi'
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
ms.openlocfilehash: 0968318ab7e416e56b71f2f30f2745d538d0ff8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718011"
---
# <a name="importfileex2-method"></a><span data-ttu-id="001b4-103">ImportFileEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="001b4-103">ImportFileEx2 Method</span></span>

<span data-ttu-id="001b4-104">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="001b4-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="001b4-105">Bu yöntem [ImportFile yöntemine](importfile-method.md)benzer, ancak içeri aktarılan dosya diskte mevcut olmasa bile çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="001b4-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001b4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="001b4-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="001b4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="001b4-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="001b4-108">İçeri aktarılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="001b4-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="001b4-109">Hedef dosyanın isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="001b4-109">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="001b4-110">İsteğe bağlı içeri aktarma kapsamı [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="001b4-110">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="001b4-111">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="001b4-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="001b4-112">[OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="001b4-112">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="001b4-113">Derleme veya dosya için benzersiz KIMLIĞI alır.</span><span class="sxs-lookup"><span data-stu-id="001b4-113">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="001b4-114">Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="001b4-114">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="001b4-115">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="001b4-115">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="001b4-116">İçeri aktarılan dosya ve/veya kapsamların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="001b4-116">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="001b4-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="001b4-117">Return Value</span></span>  

 <span data-ttu-id="001b4-118">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="001b4-118">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="001b4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="001b4-119">Requirements</span></span>  

 <span data-ttu-id="001b4-120">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="001b4-120">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001b4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="001b4-121">See also</span></span>

- [<span data-ttu-id="001b4-122">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="001b4-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="001b4-123">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="001b4-123">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="001b4-124">ALink API</span><span class="sxs-lookup"><span data-stu-id="001b4-124">ALink API</span></span>](index.md)
