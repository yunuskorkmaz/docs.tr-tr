---
description: 'Daha fazla bilgi edinin: ImportTypes2 yöntemi'
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
ms.openlocfilehash: ca0d174061608f9b4abf524c43023e867e9a9646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662617"
---
# <a name="importtypes2-method"></a><span data-ttu-id="d637e-103">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d637e-103">ImportTypes2 Method</span></span>

<span data-ttu-id="d637e-104">Türlerin içeri aktarımını başlatır.</span><span class="sxs-lookup"><span data-stu-id="d637e-104">Initiates the import of types.</span></span> <span data-ttu-id="d637e-105">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türleri içeri aktarmaya başlamak için bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d637e-105">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d637e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d637e-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d637e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d637e-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d637e-108">İçeri aktarılacak derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d637e-108">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d637e-109">İçinden içeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d637e-109">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d637e-110">İçinden içeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="d637e-110">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="d637e-111">Verilen kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="d637e-111">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d637e-112">İsteğe bağlı olarak [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="d637e-112">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="d637e-113">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d637e-113">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d637e-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d637e-114">Return Value</span></span>  

 <span data-ttu-id="d637e-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d637e-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d637e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d637e-116">Requirements</span></span>  

 <span data-ttu-id="d637e-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="d637e-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d637e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d637e-118">See also</span></span>

- [<span data-ttu-id="d637e-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d637e-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d637e-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d637e-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d637e-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="d637e-121">ALink API</span></span>](index.md)
