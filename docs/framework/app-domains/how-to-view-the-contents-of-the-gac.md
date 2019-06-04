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
ms.openlocfilehash: c319c5f7c9bb808b2ce7ee10178722287e456339
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486434"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Nasıl yapılır: Genel derleme önbelleğinin içeriğini görüntüleme

Kullanım [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) Genel Derleme Önbelleği (GAC) içeriğini görüntülemek için.

## <a name="view-the-assemblies-in-the-gac"></a>Derlemeleri GAC'ye görüntüleyin

Genel derleme önbelleğinde derlemelerin bir listesini görmek için [Visual Studio için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md)ve ardından aşağıdaki komutu girin:

```shell
gacutil -l
```

-veya-

```shell
gacutil /l
```

> [!NOTE]
> .NET Framework'ün önceki sürümlerindeki [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows kabuk uzantısı, genel derleme önbelleğini dosya Gezgini'nde görüntülemek etkin. .NET Framework 4 ile başlayarak, Shfusion.dll kullanımdan kalkmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
