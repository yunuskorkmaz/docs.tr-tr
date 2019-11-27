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
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446956"
---
# <a name="importfileex-method"></a><span data-ttu-id="4414a-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4414a-102">ImportFileEx Method</span></span>
<span data-ttu-id="4414a-103">Belirtilen derleme veya ilişkisiz modül içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="4414a-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4414a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4414a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4414a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4414a-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="4414a-106">İçinden içeri aktarılacak dosyanın tam adı.</span><span class="sxs-lookup"><span data-stu-id="4414a-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="4414a-107">Hedef dosyanın isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="4414a-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="4414a-108">TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4414a-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4414a-109">[OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4414a-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="4414a-110">İçeri aktarılmakta olan dosyanın KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="4414a-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="4414a-111">Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="4414a-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="4414a-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4414a-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="4414a-113">İçeri aktarılan dosya ve/veya kapsamların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4414a-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4414a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4414a-114">Return Value</span></span>  
 <span data-ttu-id="4414a-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="4414a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4414a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4414a-116">Requirements</span></span>  
 <span data-ttu-id="4414a-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4414a-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4414a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4414a-118">See also</span></span>

- [<span data-ttu-id="4414a-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4414a-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4414a-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4414a-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4414a-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="4414a-121">ALink API</span></span>](index.md)
