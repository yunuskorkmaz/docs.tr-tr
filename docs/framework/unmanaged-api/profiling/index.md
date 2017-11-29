---
title: "Profil Oluşturma (Yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 26fa9471b46a7a963d66ebf0d5b3c6a0286ae640
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="9e93e-102">Profil Oluşturma (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9e93e-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="9e93e-103">Profil oluşturma API'si bir programın yürütme ortak dil çalışma zamanı tarafından (CLR) izlemek bir profil oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e93e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9e93e-104">In This Section</span></span>  
 [<span data-ttu-id="9e93e-105">Profil oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="9e93e-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="9e93e-106">Profil oluşturma .NET Framework ortamında desteklemek için CLR sağlar arabirimleri ve Hizmetleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="9e93e-107">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e93e-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="9e93e-108">Profil oluşturma API'si kullanan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e93e-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="9e93e-109">Profil oluşturma ortamını ayarlama</span><span class="sxs-lookup"><span data-stu-id="9e93e-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="9e93e-110">.NET Framework uygulama profili için uygulamanız gereken adımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9e93e-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="9e93e-111">CLR Profil oluşturucular ve Windows mağazası uygulamaları</span><span class="sxs-lookup"><span data-stu-id="9e93e-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="9e93e-112">Windows mağazası uygulamaları ile başarılı olarak çalışması için CLR Profil oluşturma API tüketen tanılama araçları bağlantı noktası açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e93e-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="9e93e-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e93e-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="9e93e-114">Yöntem çağrısı altında döndüğü koşullar belgeleri `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9e93e-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="9e93e-115">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="9e93e-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="9e93e-116">Profil oluşturma API'si kullanan yönetilmeyen genel statik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e93e-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="9e93e-117">Profil oluşturma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9e93e-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="9e93e-118">Profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="9e93e-119">Profil oluşturma yapıları</span><span class="sxs-lookup"><span data-stu-id="9e93e-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="9e93e-120">Profil oluşturma API'si kullanan yönetilmeyen yapılar açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e93e-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e93e-121">Related Sections</span></span>  
 [<span data-ttu-id="9e93e-122">İzlenecek yol: Performans sorunları tanımlama</span><span class="sxs-lookup"><span data-stu-id="9e93e-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="9e93e-123">Microsoft Visual Studio 2005 Team System'da yerleşik profil oluşturma araçlarını kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="9e93e-124">Profil oluşturma API'si kullanılarak için alternatif bir yaklaşım Bu araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e93e-124">These tools provide an alternative approach to using the profiling API.</span></span>
