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
ms.openlocfilehash: b0e6250987997b8d1c833b7b33a985900510fb03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742144"
---
# <a name="emitassembly-method"></a><span data-ttu-id="aba30-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aba30-102">EmitAssembly Method</span></span>
<span data-ttu-id="aba30-103">Bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aba30-103">Creates the assembly.</span></span> <span data-ttu-id="aba30-104">Bütünleştirilmiş kod dosyası dışında diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="aba30-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="aba30-105">Bu yöntem, ilişkisiz modülleri üretirken çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="aba30-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba30-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aba30-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aba30-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aba30-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aba30-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="aba30-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aba30-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aba30-109">Return Value</span></span>  
 <span data-ttu-id="aba30-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="aba30-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aba30-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aba30-111">Requirements</span></span>  
 <span data-ttu-id="aba30-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="aba30-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba30-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aba30-113">See also</span></span>

- [<span data-ttu-id="aba30-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aba30-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="aba30-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aba30-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="aba30-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="aba30-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
