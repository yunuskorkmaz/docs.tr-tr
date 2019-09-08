---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08c4a97b8cbc61a735bb9c1e6a31a698e7eefc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787354"
---
# <a name="getscope2-method"></a><span data-ttu-id="97e87-102">GetScope2 Metodu</span><span class="sxs-lookup"><span data-stu-id="97e87-102">GetScope2 Method</span></span>
<span data-ttu-id="97e87-103">İçeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="97e87-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97e87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="97e87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97e87-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="97e87-106">Hedef derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="97e87-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="97e87-107">İçinden içeri aktarılacak dosyanın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="97e87-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="97e87-108">İçeri aktarılacak sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="97e87-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="97e87-109">Belirtilen kapsam için [IMetaDataImport2 arabirimi](../metadata/imetadataimport2-interface.md) arabirimine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="97e87-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97e87-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97e87-110">Return Value</span></span>  
 <span data-ttu-id="97e87-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="97e87-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e87-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97e87-112">Requirements</span></span>  
 <span data-ttu-id="97e87-113">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97e87-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e87-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97e87-114">See also</span></span>

- [<span data-ttu-id="97e87-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97e87-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="97e87-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97e87-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="97e87-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="97e87-117">ALink API</span></span>](index.md)
