---
title: Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma
description: Windows işletim sisteminin birçok sürümünde artık desteklenmeyen .NET Framework 1.1 gerektiren uygulamaların nasıl barındırılabildiğini açıklar.
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 28bf3669c24fdd8a6bf45f57059c2953c5ab27dd
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506976"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma

.NET Framework 1.1, Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 veya Windows 10 işletim sistemlerinde desteklenmez. Bazı durumlarda, .NET Framework 1.1, bir uygulamanın çalışması için özel olarak tanımlanır. Bu gibi durumlarda, uygulamanın .NET Framework 3.5 SP1 veya sonraki sürümde çalışacak şekilde yükseltilmesi için bağımsız yazılım satıcınıza (ISV) başvurmalısınız. Daha fazla bilgi için [bkz.](../migration-guide/migrating-from-the-net-framework-1-1.md)

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>.NET Framework 1.1'i CD veya Download Center'dan yükleme

.NET Framework 1.1'i Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 veya Windows 10'a el ile yüklemek mümkün değildir. Artık desteklenmiş. Paketi yüklemeye çalışırsanız, aşağıdaki hata iletisi görüntülenir: ".NET Framework'ün bu sürümü önceden yüklenmiş bir sürümle uyumsuz olduğundan kurulum devam edemez." Bu sorunu çözmek için [.NET Framework 3.5 SP1'i](https://www.microsoft.com/download/details.aspx?id=22)yükleyin. Bu sürüm, Windows 8, Windows 8.1 ve Windows 10'da desteklenen .NET Framework 2.0 (.NET Framework 1.1'i izleyen sürüm) içerir. Otomatik olarak .NET Framework'ün sonraki bir sürümüne güncelleştirilip güncelleştirilmeyeceğini belirlemek için uygulamayı her zaman önce yüklemeyi denemelisiniz. Yoksa, bir uygulama güncellemesi için ISV'nize başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](dotnet-35-windows-10.md)
