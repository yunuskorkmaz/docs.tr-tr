---
title: 'Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c7d197ea7178abf991247e5ecca02c2b8e94713
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634368"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="07b0d-102">Nasıl yapılır: Genel derleme önbelleğinin içeriğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="07b0d-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="07b0d-103">Kullanım [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) Genel Derleme Önbelleği (GAC) içeriğini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="07b0d-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="07b0d-104">Derlemeleri GAC'ye görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="07b0d-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="07b0d-105">Genel derleme önbelleğinde derlemelerin bir listesini görmek için [Visual Studio için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md)ve ardından aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="07b0d-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="07b0d-106">-veya-</span><span class="sxs-lookup"><span data-stu-id="07b0d-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="07b0d-107">.NET Framework'ün önceki sürümlerindeki [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows kabuk uzantısı, genel derleme önbelleğini dosya Gezgini'nde görüntülemek etkin.</span><span class="sxs-lookup"><span data-stu-id="07b0d-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="07b0d-108">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="07b0d-108">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="07b0d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07b0d-109">See also</span></span>

- [<span data-ttu-id="07b0d-110">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="07b0d-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="07b0d-111">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="07b0d-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
