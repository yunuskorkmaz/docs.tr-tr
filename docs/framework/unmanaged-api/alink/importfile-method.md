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
ms.openlocfilehash: d76e9b4e18b46d0b546d6c66fa572c35cb9fcefe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741774"
---
# <a name="importfile-method"></a><span data-ttu-id="8ca01-102">ImportFile Metodu</span><span class="sxs-lookup"><span data-stu-id="8ca01-102">ImportFile Method</span></span>
<span data-ttu-id="8ca01-103">Derlemeler ve bağlantısız modülleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="8ca01-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ca01-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8ca01-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ca01-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8ca01-106">İçeri aktarılacak dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="8ca01-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="8ca01-107">Bütünleştirilmiş kod içine bağlı olarak dosyayı yeniden adlandırmak için kullanılabilecek isteğe bağlı bir çıkış dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="8ca01-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="8ca01-108">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ca01-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="8ca01-109">Benzersiz dosya kimliği depolanacağı belirteç için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ca01-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="8ca01-110">Dosyanın bir derleme veya bir dosya olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca01-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="8ca01-111">İşaretçi alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8ca01-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="8ca01-112">Dosyanın bir derleme değilse NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca01-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="8ca01-113">Dosyaları ve/veya alınmış kapsamlar sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ca01-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ca01-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ca01-114">Return Value</span></span>  
 <span data-ttu-id="8ca01-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ca01-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca01-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ca01-116">Requirements</span></span>  
 <span data-ttu-id="8ca01-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8ca01-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca01-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca01-118">See also</span></span>

- [<span data-ttu-id="8ca01-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca01-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8ca01-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ca01-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8ca01-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="8ca01-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
