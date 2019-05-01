---
title: IHostAssemblyStore Arabirimi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930045"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="94390-102">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94390-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="94390-103">Derlemeler ve modüller ortak dil çalışma zamanı (CLR) bağımsız olarak yüklemek konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="94390-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94390-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="94390-104">Methods</span></span>  
  
|<span data-ttu-id="94390-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94390-105">Method</span></span>|<span data-ttu-id="94390-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94390-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94390-107">ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94390-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="94390-108">Tarafından başvurulmuyor bir derlemeye bir başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) çağrısından döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="94390-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="94390-109">ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94390-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="94390-110">Bir derleme veya bağlı (embedded değil) kaynak dosyası içinde bir modüle çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="94390-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94390-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94390-111">Remarks</span></span>  
 <span data-ttu-id="94390-112">`IHostAssemblyStore` verimli bir şekilde derleme kimliğine dayalı derlemeler yüklemek için bir konak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="94390-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="94390-113">Döndürerek ana bilgisayar bütünleştirilmiş kodları yükler `IStream` doğrudan baytları gösteren örnekler.</span><span class="sxs-lookup"><span data-stu-id="94390-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="94390-114">CLR bir konağa uygulanan olup olmadığını belirler. `IHostAssemblyStore` çağırarak `IHostAssemblyManager::GetNonHostAssemblyStores` başlatma temel alır.</span><span class="sxs-lookup"><span data-stu-id="94390-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="94390-115">Bu konak, örneğin, kullanıcı bütünleştirilmiş kodları bağlamayı denetlemek için ancak .NET Framework derlemeleri bağlamak için çalışma zamanı üzerinde yararlanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="94390-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94390-116">Sağlama uygulaması içinde `IHostAssemblyStore`, konak tarafından başvurulmuyor tüm derlemelerin çözümlenecek konuşmanın niyetini belirtir `ICLRAssemblyReferenceList` döndürüldüğü `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="94390-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94390-117">.NET Framework sürüm 2.0 tarafından sağlanan bir derlemenin yerel görüntü yüklemek ana bilgisayar için bir yol sunmaz [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="94390-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94390-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94390-118">Requirements</span></span>  
 <span data-ttu-id="94390-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94390-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94390-120">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94390-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94390-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="94390-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94390-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94390-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94390-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94390-123">See also</span></span>

- [<span data-ttu-id="94390-124">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94390-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="94390-125">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94390-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="94390-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94390-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
