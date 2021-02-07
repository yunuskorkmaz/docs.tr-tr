---
description: 'Daha fazla bilgi edinin: GetScope yöntemi'
title: GetScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: cdebda457573e70755b49798ae86eae8f076216b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718370"
---
# <a name="getscope-method"></a><span data-ttu-id="e5b6d-103">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="e5b6d-103">GetScope Method</span></span>

<span data-ttu-id="e5b6d-104">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b6d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5b6d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5b6d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5b6d-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="e5b6d-107">İçeri aktarılacak derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-107">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5b6d-108">İçeri aktarılacak dosyanın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-108">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="e5b6d-109">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="e5b6d-110">Kapsam için [IMetaDataImport arabirimi](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-110">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5b6d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e5b6d-111">Return Value</span></span>  

 <span data-ttu-id="e5b6d-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b6d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5b6d-113">Requirements</span></span>  

 <span data-ttu-id="e5b6d-114">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e5b6d-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b6d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b6d-115">See also</span></span>

- [<span data-ttu-id="e5b6d-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5b6d-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e5b6d-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5b6d-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e5b6d-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="e5b6d-118">ALink API</span></span>](index.md)
