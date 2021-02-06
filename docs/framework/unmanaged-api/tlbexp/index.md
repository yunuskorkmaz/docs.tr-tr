---
description: 'Daha fazla bilgi edinin: Tlbexp yardımcı Işlevleri (yönetilmeyen API Başvurusu)'
title: Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 8d5aacbe63d111b0b53f6bc76357a37ee4660d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646264"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="91c73-103">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="91c73-103">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="91c73-104">[Tür kitaplığı verme programı aracı](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) TlbRef.dll adlı bir dinamik bağlantı kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="91c73-104">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="91c73-105">Bu DLL iki yardımcı işlev ve derleme-tür kitaplığı dönüştürme işlemi sırasında dışarı aktarma aracının kullandığı bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="91c73-105">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91c73-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="91c73-106">In This Section</span></span>  

 [<span data-ttu-id="91c73-107">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="91c73-107">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="91c73-108">Bir tür kitaplığı için yerelleştirme ve işletim sistemi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91c73-108">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="91c73-109">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="91c73-109">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="91c73-110">Başvurulan tür kitaplıklarını çözümlemek için [ıtypeelibresolver arabiriminin](itypelibresolver-interface.md) bir uygulamasını kullanarak bir tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="91c73-110">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="91c73-111">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91c73-111">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="91c73-112">Bir tür kitaplığının tam yolunu döndüren [Resolvettypeınfo lib yöntemini](resolvetypelib-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="91c73-112">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
