---
description: 'Şu konuda daha fazla bilgi edinin: IHostAssemblyStore arabirimi'
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
ms.openlocfilehash: a05fee7916911687143d5953e26187162a2fa544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709041"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="8b5ba-103">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-103">IHostAssemblyStore Interface</span></span>

<span data-ttu-id="8b5ba-104">Bir konağın ortak dil çalışma zamanından (CLR) bağımsız olarak derlemeleri ve modülleri yüklemesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-104">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b5ba-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8b5ba-105">Methods</span></span>  
  
|<span data-ttu-id="8b5ba-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8b5ba-106">Method</span></span>|<span data-ttu-id="8b5ba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b5ba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b5ba-108">ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-108">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="8b5ba-109">[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)çağrısından döndürülen [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-109">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="8b5ba-110">ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-110">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="8b5ba-111">Derleme içindeki bir modülü veya bağlı (gömülü değil) kaynak dosyasını çözer.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-111">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b5ba-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b5ba-112">Remarks</span></span>  

 <span data-ttu-id="8b5ba-113">`IHostAssemblyStore` bir konağın derleme kimliği temelinde derlemeleri etkin bir şekilde yüklemesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-113">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="8b5ba-114">Ana bilgisayar, `IStream` doğrudan baytlara işaret eden örnekleri döndürerek derlemeleri yükler.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-114">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="8b5ba-115">CLR, `IHostAssemblyStore` başlatma sonrasında çağırarak bir konağın uygulanıp uygulanmadığı belirler `IHostAssemblyManager::GetNonHostAssemblyStores` .</span><span class="sxs-lookup"><span data-stu-id="8b5ba-115">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="8b5ba-116">Bu, örneğin, ana bilgisayarın kullanıcı Derlemeleriyle bağlamayı denetlemesini, ancak .NET Framework derlemelerine bağlamak için çalışma zamanına güvenmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-116">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b5ba-117">Uygulamasının bir uygulamasını sağlamak `IHostAssemblyStore` için konak, öğesinden döndürülen tarafından başvurulmayan tüm derlemeleri çözümleme amacını belirtir `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="8b5ba-117">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b5ba-118">.NET Framework sürüm 2,0, ana bilgisayarın [Yerel Görüntü Oluşturucu (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) yardımcı programı tarafından sağlandığı şekilde bir derlemenin yerel görüntüsünü yüklemesi için bir yol sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-118">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5ba-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b5ba-119">Requirements</span></span>  

 <span data-ttu-id="8b5ba-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5ba-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5ba-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b5ba-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b5ba-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b5ba-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5ba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5ba-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-124">See also</span></span>

- [<span data-ttu-id="8b5ba-125">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8b5ba-126">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b5ba-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="8b5ba-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b5ba-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
