---
title: Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104119"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="08174-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="08174-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="08174-103">[Tür kitaplığı verme programı aracı](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe), TlbRef. dll adlı bir dinamik bağlantı kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="08174-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="08174-104">Bu DLL iki yardımcı işlev ve derleme-tür kitaplığı dönüştürme işlemi sırasında dışarı aktarma aracının kullandığı bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="08174-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08174-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="08174-105">In This Section</span></span>  
 [<span data-ttu-id="08174-106">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="08174-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="08174-107">Bir tür kitaplığı için yerelleştirme ve işletim sistemi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="08174-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="08174-108">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="08174-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="08174-109">Başvurulan tür kitaplıklarını çözümlemek için [ıtypeelibresolver arabiriminin](itypelibresolver-interface.md) bir uygulamasını kullanarak bir tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="08174-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="08174-110">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08174-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="08174-111">Bir tür kitaplığının tam yolunu döndüren [Resolvettypeınfo lib yöntemini](resolvetypelib-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="08174-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
