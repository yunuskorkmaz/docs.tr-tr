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
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787585"
---
# <a name="emitassembly-method"></a><span data-ttu-id="679fe-102">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="679fe-102">EmitAssembly Method</span></span>
<span data-ttu-id="679fe-103">Derlemeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="679fe-103">Creates the assembly.</span></span> <span data-ttu-id="679fe-104">Derleme dosyası hariç diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="679fe-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="679fe-105">İlişkisiz modüller üretilirken bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="679fe-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="679fe-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="679fe-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="679fe-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="679fe-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="679fe-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="679fe-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="679fe-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="679fe-109">Return Value</span></span>  
 <span data-ttu-id="679fe-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="679fe-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="679fe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="679fe-111">Requirements</span></span>  
 <span data-ttu-id="679fe-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="679fe-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679fe-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="679fe-113">See also</span></span>

- [<span data-ttu-id="679fe-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="679fe-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="679fe-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="679fe-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="679fe-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="679fe-116">ALink API</span></span>](index.md)
