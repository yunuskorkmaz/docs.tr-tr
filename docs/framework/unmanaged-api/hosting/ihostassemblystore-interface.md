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
ms.openlocfilehash: 5620df2ab2b2530332df02cf3f11a00d6b6c8fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441620"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="9d51c-102">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51c-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="9d51c-103">Derlemeler ve modüller ortak dil çalışma zamanı (CLR) bağımsız olarak yüklemek bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d51c-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d51c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d51c-104">Methods</span></span>  
  
|<span data-ttu-id="9d51c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d51c-105">Method</span></span>|<span data-ttu-id="9d51c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d51c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d51c-107">ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51c-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="9d51c-108">Tarafından başvurulmuyor bir derlemesine başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) çağrısından döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d51c-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="9d51c-109">ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51c-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="9d51c-110">Bir derlemeyi ya da bağlantılı (katıştırılmış değil) kaynak dosyası içinde bir modüle giderir.</span><span class="sxs-lookup"><span data-stu-id="9d51c-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d51c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d51c-111">Remarks</span></span>  
 <span data-ttu-id="9d51c-112">`IHostAssemblyStore` derleme kimliğine verimli bir şekilde bağlı derlemeler yüklemek bir konak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d51c-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="9d51c-113">Konak döndürerek derlemelerini yükleyen `IStream` baytları doğrudan noktası örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9d51c-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="9d51c-114">CLR bir ana bilgisayar uyguladı olup olmadığını belirler `IHostAssemblyStore` çağırarak `IHostAssemblyManager::GetNonHostAssemblyStores` başlatma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d51c-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="9d51c-115">Bu konak, örneğin, kullanıcı derlemeleri bağlama denetlemek için ancak çalışma zamanı için .NET Framework derlemeleri bağlamak için kullanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d51c-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d51c-116">Uygulaması sağlama içinde `IHostAssemblyStore`, ana bilgisayarı tarafından başvurulan değil tüm derlemelerde çözmek yapma belirtir `ICLRAssemblyReferenceList` döndürülen `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="9d51c-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d51c-117">.NET Framework sürüm 2.0 tarafından sağlanan gibi bir derleme yerel görüntü yüklemek ana bilgisayar için bir yol sağlamaz [yerel Görüntü Oluşturucu (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="9d51c-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d51c-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d51c-118">Requirements</span></span>  
 <span data-ttu-id="9d51c-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d51c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d51c-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d51c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d51c-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d51c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d51c-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d51c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d51c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d51c-123">See Also</span></span>  
 [<span data-ttu-id="9d51c-124">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51c-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="9d51c-125">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51c-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="9d51c-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d51c-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
