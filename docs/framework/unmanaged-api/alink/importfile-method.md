---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7fee7a91de99e2db69609cbc7c73e22d85d045f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777064"
---
# <a name="importfile-method"></a><span data-ttu-id="cfd72-102">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="cfd72-102">ImportFile Method</span></span>
<span data-ttu-id="cfd72-103">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="cfd72-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd72-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfd72-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cfd72-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfd72-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="cfd72-106">İçeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="cfd72-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="cfd72-107">Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="cfd72-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="cfd72-108">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cfd72-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="cfd72-109">Benzersiz bir dosya KIMLIĞININ depolanacağı belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cfd72-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="cfd72-110">Dosya bir derleme veya bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfd72-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="cfd72-111">[IMetaDataAssemblyImport arabirimine](../metadata/imetadataassemblyimport-interface.md)yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="cfd72-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="cfd72-112">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfd72-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="cfd72-113">İçeri aktarılan dosya ve/veya kapsamların sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfd72-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfd72-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cfd72-114">Return Value</span></span>  
 <span data-ttu-id="cfd72-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="cfd72-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd72-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfd72-116">Requirements</span></span>  
 <span data-ttu-id="cfd72-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="cfd72-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd72-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfd72-118">See also</span></span>

- [<span data-ttu-id="cfd72-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfd72-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cfd72-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfd72-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cfd72-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="cfd72-121">ALink API</span></span>](index.md)
