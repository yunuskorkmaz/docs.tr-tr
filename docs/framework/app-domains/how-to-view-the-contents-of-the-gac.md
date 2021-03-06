---
title: 'Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme'
description: Genel bütünleştirilmiş kod önbelleği (GAC) aracını (gacutil.exe) kullanarak .NET 'teki genel derleme önbelleğinin içeriğini görüntülemeyi öğrenin.
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
ms.openlocfilehash: a40c371e6f95f6c90ecbfbf28183226632a58e5b
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258318"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="a603c-103">Nasıl yapılır: genel derleme önbelleğinin içeriğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a603c-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="a603c-104">Genel bütünleştirilmiş kod önbelleğinin (GAC) içeriğini görüntülemek için [genel derleme önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a603c-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="a603c-105">GAC 'de derlemeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a603c-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="a603c-106">Genel derleme önbelleğindeki derlemelerin listesini görüntülemek için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)açın ve aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="a603c-106">To view a list of the assemblies in the global assembly cache, open a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="a603c-107">-veya-</span><span class="sxs-lookup"><span data-stu-id="a603c-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="a603c-108">.NET Framework önceki sürümlerinde, [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows kabuğu uzantısı, dosya Gezgini 'nde genel derleme önbelleğini görüntülemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a603c-108">In earlier versions of .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="a603c-109">.NET Framework 4 ' ten başlayarak Shfusion.dll artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a603c-109">Beginning with .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="a603c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a603c-110">See also</span></span>

- [<span data-ttu-id="a603c-111">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="a603c-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="a603c-112">Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="a603c-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
