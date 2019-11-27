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
ms.openlocfilehash: 8dae903ab76ab83ac0818c4bc4a76e81094bdf65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445670"
---
# <a name="importtypes2-method"></a><span data-ttu-id="3836d-102">ImportTypes2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3836d-102">ImportTypes2 Method</span></span>
<span data-ttu-id="3836d-103">Türlerin içeri aktarımını başlatır.</span><span class="sxs-lookup"><span data-stu-id="3836d-103">Initiates the import of types.</span></span> <span data-ttu-id="3836d-104">[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türleri içeri aktarmaya başlamak için bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3836d-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3836d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3836d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3836d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3836d-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3836d-107">İçeri aktarılacak derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3836d-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3836d-108">İçinden içeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3836d-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="3836d-109">İçinden içeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="3836d-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="3836d-110">Verilen kapsamdaki türler için numaralandırıcı tanıtıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3836d-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="3836d-111">İsteğe bağlı olarak [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="3836d-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="3836d-112">İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3836d-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3836d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3836d-113">Return Value</span></span>  
 <span data-ttu-id="3836d-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3836d-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3836d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3836d-115">Requirements</span></span>  
 <span data-ttu-id="3836d-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="3836d-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3836d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3836d-117">See also</span></span>

- [<span data-ttu-id="3836d-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3836d-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3836d-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3836d-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3836d-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="3836d-120">ALink API</span></span>](index.md)
