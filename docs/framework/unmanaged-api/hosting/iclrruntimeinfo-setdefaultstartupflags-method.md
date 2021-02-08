---
description: ': ICLRRuntimeInfo:: SetDefaultStartupFlags Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: eb839b2ff71836adc1b3858092f7caf5787275b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785048"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="d5631-103">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5631-103">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>

<span data-ttu-id="d5631-104">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d5631-104">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="d5631-105">Bu yöntem `startupFlags` , [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevlerinde parametresinin kullanımını yerini alır.</span><span class="sxs-lookup"><span data-stu-id="d5631-105">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5631-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5631-106">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5631-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5631-107">Parameters</span></span>  

 `dwStartupFlags`  
 <span data-ttu-id="d5631-108">'ndaki Ayarlanacak konak başlangıç bayrakları.</span><span class="sxs-lookup"><span data-stu-id="d5631-108">[in] The host startup flags to set.</span></span> <span data-ttu-id="d5631-109">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5631-109">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="d5631-110">'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="d5631-110">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5631-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5631-111">Return Value</span></span>  

 <span data-ttu-id="d5631-112">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5631-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d5631-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5631-113">HRESULT</span></span>|<span data-ttu-id="d5631-114">Description</span><span class="sxs-lookup"><span data-stu-id="d5631-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5631-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5631-115">S_OK</span></span>|<span data-ttu-id="d5631-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d5631-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5631-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5631-117">Remarks</span></span>  

 <span data-ttu-id="d5631-118">Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5631-118">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="d5631-119">Aksi takdirde, A iş parçacığı b iş parçacığını `SetStartupFlags` başlattıktan önce ve ' a çağrı tamamladıktan sonra yöntemini çağırabilir `SetStartupFlags` .</span><span class="sxs-lookup"><span data-stu-id="d5631-119">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5631-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5631-120">Requirements</span></span>  

 <span data-ttu-id="d5631-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5631-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5631-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d5631-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d5631-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d5631-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5631-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5631-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5631-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5631-125">See also</span></span>

- [<span data-ttu-id="d5631-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5631-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d5631-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5631-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d5631-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="d5631-128">Hosting</span></span>](index.md)
