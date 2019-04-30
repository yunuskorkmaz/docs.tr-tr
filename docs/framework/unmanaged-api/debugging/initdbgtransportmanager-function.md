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
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761656"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="ce2e8-102">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="ce2e8-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="ce2e8-103">İşlem ve çalışma zamanı numaralandırması için bir uzak hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="ce2e8-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce2e8-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ce2e8-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ce2e8-105">Return Value</span></span>  
 <span data-ttu-id="ce2e8-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce2e8-106">S_OK</span></span>  
 <span data-ttu-id="ce2e8-107">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="ce2e8-107">Success.</span></span>  
  
 <span data-ttu-id="ce2e8-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ce2e8-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ce2e8-109">İşlev için bir aktarım Yöneticisi bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="ce2e8-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="ce2e8-110">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="ce2e8-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ce2e8-111">Diğer hatalar.</span><span class="sxs-lookup"><span data-stu-id="ce2e8-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2e8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce2e8-112">Requirements</span></span>  
 <span data-ttu-id="ce2e8-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce2e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2e8-114">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="ce2e8-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ce2e8-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ce2e8-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ce2e8-116">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ce2e8-116">**.NET Framework Versions:** 3.5 SP1</span></span>
