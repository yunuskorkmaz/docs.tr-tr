---
title: EmitAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212918"
---
# <a name="emitassembly-method"></a><span data-ttu-id="82e17-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82e17-102">EmitAssembly Method</span></span>
<span data-ttu-id="82e17-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82e17-103">Creates the assembly.</span></span> <span data-ttu-id="82e17-104">Bütünleştirilmiş kod dosyası dışında diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="82e17-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="82e17-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="82e17-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e17-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82e17-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e17-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82e17-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="82e17-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="82e17-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e17-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82e17-109">Return Value</span></span>  
 <span data-ttu-id="82e17-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="82e17-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e17-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82e17-111">Requirements</span></span>  
 <span data-ttu-id="82e17-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="82e17-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e17-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e17-113">See also</span></span>

- [<span data-ttu-id="82e17-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82e17-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="82e17-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82e17-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="82e17-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="82e17-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
