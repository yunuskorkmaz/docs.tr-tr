---
title: ImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445683"
---
# <a name="importtypes-method"></a><span data-ttu-id="82d53-102">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82d53-102">ImportTypes Method</span></span>
<span data-ttu-id="82d53-103">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türlerin içeri aktarılmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="82d53-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82d53-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82d53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82d53-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="82d53-106">İçeri aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="82d53-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="82d53-107">İçeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="82d53-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="82d53-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="82d53-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="82d53-109">Bu kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="82d53-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="82d53-110">İsteğe bağlı olarak [IMetaDataImport arabirim](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="82d53-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="82d53-111">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="82d53-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82d53-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82d53-112">Return Value</span></span>  
 <span data-ttu-id="82d53-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="82d53-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d53-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82d53-114">Requirements</span></span>  
 <span data-ttu-id="82d53-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="82d53-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d53-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d53-116">See also</span></span>

- [<span data-ttu-id="82d53-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82d53-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="82d53-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82d53-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="82d53-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="82d53-119">ALink API</span></span>](index.md)
