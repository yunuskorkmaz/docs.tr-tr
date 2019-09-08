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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f19dd114925ed1fd12bcc0056411c3e3d4181215
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777088"
---
# <a name="importtypes-method"></a><span data-ttu-id="17099-102">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17099-102">ImportTypes Method</span></span>
<span data-ttu-id="17099-103">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türlerin içeri aktarılmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="17099-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17099-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17099-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="17099-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17099-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="17099-106">İçeri aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="17099-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="17099-107">İçeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="17099-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="17099-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="17099-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="17099-109">Bu kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="17099-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="17099-110">İsteğe bağlı olarak [IMetaDataImport arabirim](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="17099-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="17099-111">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="17099-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17099-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17099-112">Return Value</span></span>  
 <span data-ttu-id="17099-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="17099-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17099-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17099-114">Requirements</span></span>  
 <span data-ttu-id="17099-115">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="17099-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17099-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17099-116">See also</span></span>

- [<span data-ttu-id="17099-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17099-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="17099-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17099-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="17099-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="17099-119">ALink API</span></span>](index.md)
