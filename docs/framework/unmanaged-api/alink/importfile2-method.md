---
description: 'Daha fazla bilgi edinin: ImportFile2 yöntemi'
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
ms.openlocfilehash: 98da8ecf4bfc19e52c5a92e6509f6af49afbdd5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718063"
---
# <a name="importfile2-method"></a><span data-ttu-id="a6929-103">ImportFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6929-103">ImportFile2 Method</span></span>

<span data-ttu-id="a6929-104">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="a6929-104">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="a6929-105">Bu yöntem [ImportFile yöntemine](importfile-method.md)benzer, ancak içeri aktarılan dosya diskte mevcut olmasa bile çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a6929-105">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6929-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6929-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a6929-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6929-107">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="a6929-108">İçeri aktarılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a6929-108">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="a6929-109">Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="a6929-109">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="a6929-110">İsteğe bağlı [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a6929-110">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="a6929-111">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a6929-111">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="a6929-112">Dosya veya derleme için KIMLIĞI alır.</span><span class="sxs-lookup"><span data-stu-id="a6929-112">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="a6929-113">[IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="a6929-113">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="a6929-114">Dosya derleme değilse NULL.</span><span class="sxs-lookup"><span data-stu-id="a6929-114">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="a6929-115">İçeri aktarılan dosya ve/veya kapsamların bulunduğu yer sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a6929-115">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6929-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6929-116">Return Value</span></span>  

 <span data-ttu-id="a6929-117">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6929-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6929-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6929-118">Requirements</span></span>  

 <span data-ttu-id="a6929-119">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a6929-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6929-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6929-120">See also</span></span>

- [<span data-ttu-id="a6929-121">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6929-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a6929-122">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6929-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a6929-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="a6929-123">ALink API</span></span>](index.md)
