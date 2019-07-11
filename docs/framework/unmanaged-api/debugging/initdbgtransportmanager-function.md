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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764787"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="148f9-102">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="148f9-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="148f9-103">İşlem ve çalışma zamanı numaralandırması için bir uzak hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="148f9-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="148f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="148f9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="148f9-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="148f9-105">Return Value</span></span>  
 <span data-ttu-id="148f9-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="148f9-106">S_OK</span></span>  
 <span data-ttu-id="148f9-107">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="148f9-107">Success.</span></span>  
  
 <span data-ttu-id="148f9-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="148f9-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="148f9-109">İşlev için bir aktarım Yöneticisi bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="148f9-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="148f9-110">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="148f9-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="148f9-111">Diğer hatalar.</span><span class="sxs-lookup"><span data-stu-id="148f9-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="148f9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="148f9-112">Requirements</span></span>  
 <span data-ttu-id="148f9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148f9-114">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="148f9-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="148f9-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="148f9-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="148f9-116">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="148f9-116">**.NET Framework Versions:** 3.5 SP1</span></span>
