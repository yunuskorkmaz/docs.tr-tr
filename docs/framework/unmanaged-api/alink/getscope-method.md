---
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
ms.openlocfilehash: 078168ae8860f18ff6f811dcc972e3eb3c857e1d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447198"
---
# <a name="getscope-method"></a><span data-ttu-id="0a087-102">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="0a087-102">GetScope Method</span></span>
<span data-ttu-id="0a087-103">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="0a087-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a087-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a087-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a087-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a087-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0a087-106">İçeri aktarılacak derlemenin benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0a087-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0a087-107">İçeri aktarılacak dosyanın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0a087-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="0a087-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="0a087-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="0a087-109">Kapsam için [IMetaDataImport arabirimi](../metadata/imetadataimport-interface.md) arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="0a087-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a087-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a087-110">Return Value</span></span>  
 <span data-ttu-id="0a087-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a087-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a087-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a087-112">Requirements</span></span>  
 <span data-ttu-id="0a087-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="0a087-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a087-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a087-114">See also</span></span>

- [<span data-ttu-id="0a087-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a087-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0a087-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a087-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0a087-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="0a087-117">ALink API</span></span>](index.md)
