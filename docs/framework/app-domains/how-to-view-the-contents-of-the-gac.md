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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Nasıl yapılır: genel derleme önbelleğinin içeriğini görüntüleme

Genel bütünleştirilmiş kod önbelleğinin (GAC) içeriğini görüntülemek için [genel derleme önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.

## <a name="view-the-assemblies-in-the-gac"></a>GAC 'de derlemeleri görüntüleme

Genel derleme önbelleğindeki derlemelerin listesini görüntülemek için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)açın ve aşağıdaki komutu girin:

```shell
gacutil -l
```

-veya-

```shell
gacutil /l
```

> [!NOTE]
> .NET Framework önceki sürümlerinde, [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows kabuğu uzantısı, dosya Gezgini 'nde genel derleme önbelleğini görüntülemenize olanak sağlar. .NET Framework 4 ' ten başlayarak Shfusion.dll artık kullanılmıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
