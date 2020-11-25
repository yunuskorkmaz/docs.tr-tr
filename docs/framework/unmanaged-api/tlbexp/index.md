---
title: Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 9386918f3574720d90bda7e8da592fa0c91160e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708250"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="e3a52-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e3a52-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="e3a52-103">[Tür kitaplığı verme programı aracı](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) TlbRef.dll adlı bir dinamik bağlantı kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="e3a52-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="e3a52-104">Bu DLL iki yardımcı işlev ve derleme-tür kitaplığı dönüştürme işlemi sırasında dışarı aktarma aracının kullandığı bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="e3a52-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3a52-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e3a52-105">In This Section</span></span>  

 [<span data-ttu-id="e3a52-106">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="e3a52-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="e3a52-107">Bir tür kitaplığı için yerelleştirme ve işletim sistemi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3a52-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="e3a52-108">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="e3a52-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="e3a52-109">Başvurulan tür kitaplıklarını çözümlemek için [ıtypeelibresolver arabiriminin](itypelibresolver-interface.md) bir uygulamasını kullanarak bir tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="e3a52-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="e3a52-110">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3a52-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="e3a52-111">Bir tür kitaplığının tam yolunu döndüren [Resolvettypeınfo lib yöntemini](resolvetypelib-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3a52-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
