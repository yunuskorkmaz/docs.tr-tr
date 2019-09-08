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
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776932"
---
# <a name="importfile2-method"></a><span data-ttu-id="3fb75-102">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb75-102">ImportFile2 Method</span></span>
<span data-ttu-id="3fb75-103">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="3fb75-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="3fb75-104">Bu yöntem [ImportFile yöntemine](importfile-method.md)benzer, ancak içeri aktarılan dosya diskte mevcut olmasa bile çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="3fb75-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb75-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fb75-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="3fb75-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fb75-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="3fb75-107">İçeri aktarılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3fb75-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="3fb75-108">Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="3fb75-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="3fb75-109">İsteğe bağlı [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3fb75-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="3fb75-110">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fb75-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="3fb75-111">Dosya veya derleme için KIMLIĞI alır.</span><span class="sxs-lookup"><span data-stu-id="3fb75-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="3fb75-112">[IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="3fb75-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="3fb75-113">Dosya derleme değilse NULL.</span><span class="sxs-lookup"><span data-stu-id="3fb75-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="3fb75-114">İçeri aktarılan dosya ve/veya kapsamların bulunduğu yer sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3fb75-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fb75-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3fb75-115">Return Value</span></span>  
 <span data-ttu-id="3fb75-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fb75-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb75-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fb75-117">Requirements</span></span>  
 <span data-ttu-id="3fb75-118">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3fb75-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb75-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb75-119">See also</span></span>

- [<span data-ttu-id="3fb75-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fb75-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3fb75-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fb75-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3fb75-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="3fb75-122">ALink API</span></span>](index.md)
