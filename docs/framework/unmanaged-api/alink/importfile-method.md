---
description: 'Daha fazla bilgi edinin: ImportFile yöntemi'
title: ImportFile Metodu
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: 82c9c7de7cd739ee205dc3695ea651643d01ea3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718167"
---
# <a name="importfile-method"></a><span data-ttu-id="35e92-103">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="35e92-103">ImportFile Method</span></span>

<span data-ttu-id="35e92-104">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="35e92-104">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35e92-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="35e92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35e92-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="35e92-107">İçeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="35e92-107">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="35e92-108">Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="35e92-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="35e92-109">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="35e92-109">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="35e92-110">Benzersiz bir dosya KIMLIĞININ depolanacağı belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="35e92-110">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="35e92-111">Dosya bir derleme veya bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="35e92-111">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="35e92-112">[IMetaDataAssemblyImport arabirimine](../metadata/imetadataassemblyimport-interface.md)yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="35e92-112">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="35e92-113">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="35e92-113">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="35e92-114">İçeri aktarılan dosya ve/veya kapsamların sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35e92-114">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35e92-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35e92-115">Return Value</span></span>  

 <span data-ttu-id="35e92-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="35e92-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e92-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35e92-117">Requirements</span></span>  

 <span data-ttu-id="35e92-118">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="35e92-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e92-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35e92-119">See also</span></span>

- [<span data-ttu-id="35e92-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35e92-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="35e92-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35e92-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="35e92-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="35e92-122">ALink API</span></span>](index.md)
