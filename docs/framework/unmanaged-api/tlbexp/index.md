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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104119"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="22570-102">Tlbexp Yardımcı İşlevleri (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="22570-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="22570-103">[Tip Kitaplığı İhracatçısı aracı](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) TlbRef.dll adlı dinamik bir bağlantı kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="22570-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="22570-104">Bu DLL, iki yardımcı işlev ve ihracatçı aracının derleme-tip kitaplık dönüştürme işlemi sırasında kullandığı bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="22570-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22570-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="22570-105">In This Section</span></span>  
 [<span data-ttu-id="22570-106">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="22570-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="22570-107">Tür kitaplığı için yerelleştirme ve işletim sistemi bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="22570-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="22570-108">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="22570-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="22570-109">Başvurulan tür kitaplıklarını çözmek için [ITypeLibResolver arabiriminin](itypelibresolver-interface.md) bir uygulamasını kullanarak bir tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="22570-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="22570-110">ITypeLibResolver Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22570-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="22570-111">Bir tür kitaplığın tam nitelikli yolunu döndüren [ResolveTypeLib yöntemini](resolvetypelib-method.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="22570-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
