---
title: Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967706"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="a2381-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a2381-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="a2381-103">[Tür kitaplığı dışarı Aktarıcı aracı](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) TlbRef.dll adlı bir dinamik bağlantı kitaplığı (Tlbexp.exe) yükler.</span><span class="sxs-lookup"><span data-stu-id="a2381-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="a2381-104">Bu DLL, iki yardımcı işlev ve dışarı aktarma aracı derleme için tür kitaplığını dönüştürme işlemi sırasında kullanan bir arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2381-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2381-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2381-105">In This Section</span></span>  
 [<span data-ttu-id="a2381-106">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="a2381-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="a2381-107">Bir tür kitaplığı için yerelleştirme ve işletim sistemi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2381-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="a2381-108">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="a2381-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="a2381-109">Bir tür kitaplığı uygulaması kullanarak yükler [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) herhangi çözmek için başvurulan tür kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="a2381-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="a2381-110">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2381-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="a2381-111">Sağlar [ResolveTypeLib yöntemi](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), bir tür kitaplığının tam yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2381-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
