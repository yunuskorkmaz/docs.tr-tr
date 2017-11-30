---
title: "Çalıştırma .NET Framework 1.1 uygulamalarını Windows 8, Windows 8.1 veya Windows 10"
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c7b53a842dc4f9b6bfc04e058411e4a6d11a7bd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="19a1d-102">Çalıştırma .NET Framework 1.1 uygulamalarını Windows 8, Windows 8.1 veya Windows 10</span><span class="sxs-lookup"><span data-stu-id="19a1d-102">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="19a1d-103">.NET Framework 1.1 desteklenmiyor [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10 işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="19a1d-103">The .NET Framework 1.1 is not supported on the [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or the Windows 10 operating systems.</span></span> <span data-ttu-id="19a1d-104">Bazı durumlarda, .NET Framework 1.1 özellikle tanımlanır çalıştırmak bir uygulama için gerekli.</span><span class="sxs-lookup"><span data-stu-id="19a1d-104">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="19a1d-105">Bu durumlarda, bağımsız yazılım satıcısı (ISV) çalıştırmak için yükseltilmiş uygulamanız için başvurmalıdır [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="19a1d-105">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] or later version.</span></span> <span data-ttu-id="19a1d-106">Ek bilgi için bkz: [.NET Framework 1. 1 ' geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span><span class="sxs-lookup"><span data-stu-id="19a1d-106">For additional information, see [Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="19a1d-107">.NET Framework 1.1 bir CD veya Yükleme Merkezi'nden yükleyin</span><span class="sxs-lookup"><span data-stu-id="19a1d-107">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="19a1d-108">.NET Framework 1.1 el ile yüklemek kurulamadığı [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10.</span><span class="sxs-lookup"><span data-stu-id="19a1d-108">It isn't possible to manually install the .NET Framework 1.1 on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or Windows 10.</span></span> <span data-ttu-id="19a1d-109">Artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="19a1d-109">It is no longer supported.</span></span> <span data-ttu-id="19a1d-110">Paket yüklemeye çalışırsanız, aşağıdaki hata iletisi görüntülenir: "İçin kurulum devam edemiyor .NET Framework'ün bu sürümü ile önceden yüklenmiş bir tane uyumlu değil."</span><span class="sxs-lookup"><span data-stu-id="19a1d-110">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="19a1d-111">Bu sorunu çözmek için yükleme [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span><span class="sxs-lookup"><span data-stu-id="19a1d-111">To solve this problem, install the [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="19a1d-112">Bu sürüm, .NET Framework üzerinde desteklenen 2.0 (.NET Framework 1.1 izleyen sürüm) içerir [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]ve Windows 10.</span><span class="sxs-lookup"><span data-stu-id="19a1d-112">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], and Windows 10.</span></span> <span data-ttu-id="19a1d-113">Her zaman otomatik olarak .NET Framework'ün sonraki bir sürüme güncelleştirilir, ilk belirlemek için uygulamayı yüklemek denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="19a1d-113">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="19a1d-114">Mevcut değilse, ISV bir uygulama güncelleştirmesi başvurun.</span><span class="sxs-lookup"><span data-stu-id="19a1d-114">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="19a1d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19a1d-115">See also</span></span>

<span data-ttu-id="19a1d-116">[.NET Framework 1.1 geçirme](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme](../../../docs/framework/install/dotnet-35-windows-10.md)</span><span class="sxs-lookup"><span data-stu-id="19a1d-116">[Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span></span>
