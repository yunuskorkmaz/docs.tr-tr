---
title: ImportTypes2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787260"
---
# <a name="importtypes2-method"></a><span data-ttu-id="80911-102">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80911-102">ImportTypes2 Method</span></span>
<span data-ttu-id="80911-103">Türlerin içeri aktarımını başlatır.</span><span class="sxs-lookup"><span data-stu-id="80911-103">Initiates the import of types.</span></span> <span data-ttu-id="80911-104">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türleri içeri aktarmaya başlamak için bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="80911-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80911-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80911-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="80911-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80911-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="80911-107">İçeri aktarılacak derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="80911-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="80911-108">İçinden içeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="80911-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="80911-109">İçinden içeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="80911-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="80911-110">Verilen kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="80911-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="80911-111">İsteğe bağlı olarak [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="80911-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="80911-112">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="80911-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80911-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80911-113">Return Value</span></span>  
 <span data-ttu-id="80911-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="80911-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80911-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80911-115">Requirements</span></span>  
 <span data-ttu-id="80911-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="80911-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80911-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80911-117">See also</span></span>

- [<span data-ttu-id="80911-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80911-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="80911-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80911-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="80911-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="80911-120">ALink API</span></span>](index.md)
