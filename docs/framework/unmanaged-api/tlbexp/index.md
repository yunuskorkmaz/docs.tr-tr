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
ms.openlocfilehash: a95ff535a4d0847fbd4b8af28f873b67a1829a4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798830"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="dba43-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dba43-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="dba43-103">[Tür kitaplığı verme programı aracı](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe), TlbRef. dll adlı bir dinamik bağlantı kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="dba43-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="dba43-104">Bu DLL iki yardımcı işlev ve derleme-tür kitaplığı dönüştürme işlemi sırasında dışarı aktarma aracının kullandığı bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="dba43-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dba43-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dba43-105">In This Section</span></span>  
 [<span data-ttu-id="dba43-106">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="dba43-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="dba43-107">Bir tür kitaplığı için yerelleştirme ve işletim sistemi bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba43-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="dba43-108">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="dba43-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="dba43-109">Başvurulan tür kitaplıklarını çözümlemek için [ıtypeelibresolver arabiriminin](itypelibresolver-interface.md) bir uygulamasını kullanarak bir tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="dba43-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="dba43-110">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dba43-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="dba43-111">Bir tür kitaplığının tam yolunu döndüren [Resolvettypeınfo lib yöntemini](resolvetypelib-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba43-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
