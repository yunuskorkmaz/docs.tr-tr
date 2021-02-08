---
description: ': InitDbgTransportManager Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 19cdfcbe3a5b120c11fc781476410833997b8c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790444"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="2cd4a-103">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="2cd4a-103">InitDbgTransportManager Function</span></span>

<span data-ttu-id="2cd4a-104">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="2cd4a-104">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd4a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2cd4a-105">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2cd4a-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cd4a-106">Return Value</span></span>  

 <span data-ttu-id="2cd4a-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cd4a-107">S_OK</span></span>  
 <span data-ttu-id="2cd4a-108">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="2cd4a-108">Success.</span></span>  
  
 <span data-ttu-id="2cd4a-109">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2cd4a-109">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="2cd4a-110">İşlev, bir taşıma yöneticisi için bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="2cd4a-110">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="2cd4a-111">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="2cd4a-111">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2cd4a-112">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="2cd4a-112">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd4a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cd4a-113">Requirements</span></span>  

 <span data-ttu-id="2cd4a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd4a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd4a-115">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="2cd4a-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="2cd4a-116">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="2cd4a-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="2cd4a-117">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="2cd4a-117">**.NET Framework Versions:** 3.5 SP1</span></span>
