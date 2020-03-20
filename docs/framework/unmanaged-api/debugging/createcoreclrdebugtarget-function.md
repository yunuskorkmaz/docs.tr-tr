---
title: CreateCoreClrDebugTarget İşlevi
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179214"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="b054a-102">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="b054a-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="b054a-103">Uzak bir makinede çalışan bir hata ayıklayıcı proxy'ye bağlantı oluşturur ve uzak makinede çalışan işlemleri ve yüklü çalışma sürelerini sorgulamak için kullanılabilecek bir [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b054a-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b054a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b054a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b054a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b054a-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="b054a-106">[içinde] Uzak bir hedef makinenin IPv4 adresi.</span><span class="sxs-lookup"><span data-stu-id="b054a-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="b054a-107">[çıkış] Oluşturulacak bir [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b054a-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b054a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b054a-108">Return Value</span></span>  
 <span data-ttu-id="b054a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="b054a-109">S_OK</span></span>  
 <span data-ttu-id="b054a-110">İşlemdeki CLR sayısı başarıyla belirlendi ve karşılık gelen tutamaç ve yol dizileri düzgün şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="b054a-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="b054a-111">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="b054a-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b054a-112">`ppTarget`'ye yeterli bellek ayrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b054a-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="b054a-113">E_FAIL (veya diğer E_ iade kodları)</span><span class="sxs-lookup"><span data-stu-id="b054a-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b054a-114">Diğer başarısızlıklar.</span><span class="sxs-lookup"><span data-stu-id="b054a-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b054a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b054a-115">Requirements</span></span>  
 <span data-ttu-id="b054a-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b054a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b054a-117">**Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b054a-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b054a-118">**Kütüphane:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b054a-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b054a-119">**.NET Çerçeve Sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b054a-119">**.NET Framework Versions:** 3.5 SP1</span></span>
