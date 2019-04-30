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
ms.openlocfilehash: 0375c835dea8984db34d3d1e24b2876fb9af8337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705603"
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
> .NET Framework'ün önceki sürümlerindeki [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows kabuk uzantısı, genel derleme önbelleğini dosya Gezgini'nde görüntülemek etkin. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll kullanımdan kalkmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)