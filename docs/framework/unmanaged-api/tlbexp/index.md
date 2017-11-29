---
title: "Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5d0a0b08be725a50442a3db9f9942bceea7cf8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="7c53f-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7c53f-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="7c53f-103">[Tür kitaplığı dışarı Aktarıcı aracı](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) TlbRef.dll adlı bir dinamik bağlantı kitaplığı (Tlbexp.exe) yükler.</span><span class="sxs-lookup"><span data-stu-id="7c53f-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="7c53f-104">Bu DLL iki yardımcı işlev ve dışarı aktarma aracı derleme için tür kitaplığı dönüştürme işlemi sırasında kullanan bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="7c53f-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c53f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7c53f-105">In This Section</span></span>  
 [<span data-ttu-id="7c53f-106">Gettypelibınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="7c53f-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="7c53f-107">Tür kitaplığı için yerelleştirme ve işletim sistemi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c53f-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="7c53f-108">LoadTypeLibWithResolver işlevi</span><span class="sxs-lookup"><span data-stu-id="7c53f-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="7c53f-109">Tür kitaplığı uygulaması kullanarak yükler [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) herhangi çözümlemek için başvurulan tür kitaplıklarının.</span><span class="sxs-lookup"><span data-stu-id="7c53f-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="7c53f-110">Itypelibresolver arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c53f-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="7c53f-111">Sağlar [ResolveTypeLib yöntemi](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), bir tür kitaplığı tam nitelenmiş yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c53f-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
