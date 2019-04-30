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
ms.openlocfilehash: 69e48c6c3179ced167fdc39ae4df859f161727ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753523"
---
# <a name="importfile-method"></a><span data-ttu-id="87b47-102">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="87b47-102">ImportFile Method</span></span>
<span data-ttu-id="87b47-103">Derlemeler ve bağlantısız modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="87b47-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87b47-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="87b47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87b47-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="87b47-106">İçeri aktarılacak dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="87b47-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="87b47-107">Bütünleştirilmiş kod içine bağlı olarak dosyayı yeniden adlandırmak için kullanılabilecek isteğe bağlı bir çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="87b47-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="87b47-108">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b47-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="87b47-109">Benzersiz dosya kimliği depolanacağı belirteç için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87b47-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="87b47-110">Dosyanın bir derleme veya bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="87b47-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="87b47-111">İşaretçi alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="87b47-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="87b47-112">Dosyanın bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="87b47-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="87b47-113">Dosyaları ve/veya alınmış kapsamlar sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87b47-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87b47-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87b47-114">Return Value</span></span>  
 <span data-ttu-id="87b47-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="87b47-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87b47-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87b47-116">Requirements</span></span>  
 <span data-ttu-id="87b47-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="87b47-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b47-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87b47-118">See also</span></span>

- [<span data-ttu-id="87b47-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87b47-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="87b47-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87b47-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="87b47-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="87b47-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
