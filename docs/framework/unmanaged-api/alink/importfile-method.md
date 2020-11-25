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
ms.openlocfilehash: f30307884a268008fd4d1a8de31ec5a49b6ab92d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705247"
---
# <a name="importfile-method"></a><span data-ttu-id="a7b9b-102">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="a7b9b-102">ImportFile Method</span></span>

<span data-ttu-id="a7b9b-103">Derlemeleri ve ilişkisiz modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b9b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7b9b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a7b9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b9b-105">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="a7b9b-106">İçeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="a7b9b-107">Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="a7b9b-108">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="a7b9b-109">Benzersiz bir dosya KIMLIĞININ depolanacağı belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="a7b9b-110">Dosya bir derleme veya bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="a7b9b-111">[IMetaDataAssemblyImport arabirimine](../metadata/imetadataassemblyimport-interface.md)yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="a7b9b-112">Dosya bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="a7b9b-113">İçeri aktarılan dosya ve/veya kapsamların sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7b9b-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7b9b-114">Return Value</span></span>  

 <span data-ttu-id="a7b9b-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b9b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b9b-116">Requirements</span></span>  

 <span data-ttu-id="a7b9b-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a7b9b-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b9b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b9b-118">See also</span></span>

- [<span data-ttu-id="a7b9b-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b9b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a7b9b-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b9b-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a7b9b-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="a7b9b-121">ALink API</span></span>](index.md)
