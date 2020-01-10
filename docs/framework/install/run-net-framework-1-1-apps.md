---
title: Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 507de3ca635986d1f4e0e3ba7c607a4af774cdcf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716273"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma

.NET Framework 1,1, Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 veya Windows 10 işletim sistemlerinde desteklenmez. Bazı durumlarda .NET Framework 1,1, bir uygulamanın çalışması için özellikle gereken şekilde tanımlanır. Bu gibi durumlarda, uygulamanın .NET Framework 3,5 SP1 veya sonraki bir sürümünde çalışacak şekilde yükseltilmesi için bağımsız yazılım satıcınıza (ISV) başvurmanız gerekir. Daha fazla bilgi için, bkz. [.NET Framework 1,1 ' den geçiş](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>CD 'den veya Indirme merkezinden 1,1 .NET Framework yükleyin

.NET Framework 1,1 ' i Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 veya Windows 10 ' a el ile yüklemek mümkün değildir. Artık desteklenmiyor. Paketi yüklemeye çalışırsanız şu hata iletisi görüntülenir: ".NET Framework sürümü daha önce yüklenmiş bir sürümle uyumsuz olduğundan kurulum devam edemiyor." Bu sorunu çözmek için [.NET Framework 3,5 SP1](https://www.microsoft.com/download/details.aspx?id=22)'i yüklemelisiniz. Bu sürüm, Windows 8, Windows 8.1 ve Windows 10 ' da desteklenen .NET Framework 2,0 (.NET Framework 1,1 ' den sonraki sürüm) içerir. İlk olarak, .NET Framework sonraki bir sürümüne otomatik olarak güncelleştirilip güncelleştirilmediğini anlamak için her zaman uygulamayı yüklemeyi denemelisiniz. Değilse, bir uygulama güncelleştirmesi için ISV 'nize başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](dotnet-35-windows-10.md)
