---
title: IHostAssemblyStore Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="df8bf-102">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df8bf-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="df8bf-103">Derlemeler ve modüller ortak dil çalışma zamanı (CLR) bağımsız olarak yüklemek bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="df8bf-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df8bf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df8bf-104">Methods</span></span>  
  
|<span data-ttu-id="df8bf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df8bf-105">Method</span></span>|<span data-ttu-id="df8bf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df8bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df8bf-107">ProvideAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="df8bf-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="df8bf-108">Tarafından başvurulmuyor bir derlemesine başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) çağrısından döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="df8bf-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="df8bf-109">ProvideModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="df8bf-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="df8bf-110">Bir derlemeyi ya da bağlantılı (katıştırılmış değil) kaynak dosyası içinde bir modüle giderir.</span><span class="sxs-lookup"><span data-stu-id="df8bf-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df8bf-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df8bf-111">Remarks</span></span>  
 <span data-ttu-id="df8bf-112">`IHostAssemblyStore`derleme kimliğine verimli bir şekilde bağlı derlemeler yüklemek bir konak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="df8bf-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="df8bf-113">Konak döndürerek derlemelerini yükleyen `IStream` baytları doğrudan noktası örnekleri.</span><span class="sxs-lookup"><span data-stu-id="df8bf-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="df8bf-114">CLR bir ana bilgisayar uyguladı olup olmadığını belirler `IHostAssemblyStore` çağırarak `IHostAssemblyManager::GetNonHostAssemblyStores` başlatma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="df8bf-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="df8bf-115">Bu konak, örneğin, kullanıcı derlemeleri bağlama denetlemek için ancak çalışma zamanı için .NET Framework derlemeleri bağlamak için kullanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="df8bf-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8bf-116">Uygulaması sağlama içinde `IHostAssemblyStore`, ana bilgisayarı tarafından başvurulan değil tüm derlemelerde çözmek yapma belirtir `ICLRAssemblyReferenceList` döndürülen `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="df8bf-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df8bf-117">.NET Framework sürüm 2.0 tarafından sağlanan gibi bir derleme yerel görüntü yüklemek ana bilgisayar için bir yol sağlamaz [yerel Görüntü Oluşturucu (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="df8bf-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df8bf-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df8bf-118">Requirements</span></span>  
 <span data-ttu-id="df8bf-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df8bf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df8bf-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df8bf-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df8bf-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="df8bf-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df8bf-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df8bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8bf-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df8bf-123">See Also</span></span>  
 [<span data-ttu-id="df8bf-124">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="df8bf-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="df8bf-125">Ihostassemblymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="df8bf-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="df8bf-126">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df8bf-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
