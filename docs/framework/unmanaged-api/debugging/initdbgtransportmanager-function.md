---
title: InitDbgTransportManager İşlevi
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421052"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="5a3f7-102">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="5a3f7-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="5a3f7-103">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="5a3f7-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3f7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5a3f7-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5a3f7-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a3f7-105">Return Value</span></span>  
 <span data-ttu-id="5a3f7-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a3f7-106">S_OK</span></span>  
 <span data-ttu-id="5a3f7-107">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="5a3f7-107">Success.</span></span>  
  
 <span data-ttu-id="5a3f7-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5a3f7-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5a3f7-109">İşlev, bir taşıma yöneticisi için bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="5a3f7-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="5a3f7-110">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="5a3f7-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5a3f7-111">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="5a3f7-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3f7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a3f7-112">Requirements</span></span>  
 <span data-ttu-id="5a3f7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3f7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3f7-114">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="5a3f7-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5a3f7-115">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="5a3f7-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5a3f7-116">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5a3f7-116">**.NET Framework Versions:** 3.5 SP1</span></span>
