---
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
ms.openlocfilehash: 9e373f133830a5bc1f3cf7bdc8034cb67725d797
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705208"
---
# <a name="importfileex-method"></a><span data-ttu-id="f27c7-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f27c7-102">ImportFileEx Method</span></span>

<span data-ttu-id="f27c7-103">Belirtilen derleme veya ilişkisiz modül içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="f27c7-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27c7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f27c7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f27c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f27c7-105">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="f27c7-106">İçinden içeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="f27c7-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="f27c7-107">Hedef dosyanın isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="f27c7-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="f27c7-108">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f27c7-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="f27c7-109">[OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f27c7-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="f27c7-110">İçeri aktarılmakta olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="f27c7-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="f27c7-111">Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="f27c7-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="f27c7-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f27c7-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="f27c7-113">İçeri aktarılan dosya ve/veya kapsamların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f27c7-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f27c7-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f27c7-114">Return Value</span></span>  

 <span data-ttu-id="f27c7-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f27c7-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27c7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f27c7-116">Requirements</span></span>  

 <span data-ttu-id="f27c7-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f27c7-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27c7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f27c7-118">See also</span></span>

- [<span data-ttu-id="f27c7-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f27c7-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f27c7-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f27c7-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f27c7-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="f27c7-121">ALink API</span></span>](index.md)
