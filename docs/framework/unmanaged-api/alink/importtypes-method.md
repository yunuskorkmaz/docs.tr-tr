---
description: 'Daha fazla bilgi edinin: ImportTypes Yöntemi'
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
ms.openlocfilehash: 9a30c735ca2c9ad0f945628c3de1eb1bb56efe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662630"
---
# <a name="importtypes-method"></a><span data-ttu-id="a156e-103">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a156e-103">ImportTypes Method</span></span>

<span data-ttu-id="a156e-104">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türlerin içeri aktarılmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="a156e-104">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a156e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a156e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a156e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a156e-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="a156e-107">İçeri aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a156e-107">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a156e-108">İçeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a156e-108">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="a156e-109">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="a156e-109">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="a156e-110">Bu kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a156e-110">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="a156e-111">İsteğe bağlı olarak [IMetaDataImport arabirim](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="a156e-111">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="a156e-112">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a156e-112">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a156e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a156e-113">Return Value</span></span>  

 <span data-ttu-id="a156e-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a156e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a156e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a156e-115">Requirements</span></span>  

 <span data-ttu-id="a156e-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a156e-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a156e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a156e-117">See also</span></span>

- [<span data-ttu-id="a156e-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a156e-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a156e-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a156e-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a156e-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="a156e-120">ALink API</span></span>](index.md)
