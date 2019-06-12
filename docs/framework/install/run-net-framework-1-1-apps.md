---
title: Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ad78c9a277af23eebe357ef986ea59d16bb444e
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833731"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Windows 8, Windows 8.1 veya Windows 10’da .NET Framework 1.1 uygulamalarını çalıştırma

.NET Framework 1.1 desteklenmiyor [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10 işletim sistemleri. Bazı durumlarda, .NET Framework 1.1 özellikle çalıştırılacak bir uygulama için gerekli. Bu gibi durumlarda, bağımsız yazılım satıcısı (ISV) .NET Framework 3.5 SP1 veya sonraki bir sürümü üzerinde çalıştırmak için yükseltilmiş uygulamanız için başvurmanız gerekir. Ek bilgi için bkz: [.NET Framework 1. 1 ' geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>.NET Framework 1.1 bir CD veya Yükleme Merkezi'nden yükleme

.NET Framework 1.1 el ile yüklemek mümkün değildir [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10. Artık desteklenmiyor. Paketi yüklemeye çalışırsanız aşağıdaki hata iletisi görüntülenir: "Bu .NET Framework sürümü önceden yüklenmiş olanla uyumlu olmadığı için kurulum devam edemiyor." Bu sorunu çözmek için yükleme [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Bu sürümü .NET Framework üzerinde desteklenen 2.0 (.NET Framework 1.1 takip eden sürüm) içerir [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]ve Windows 10. Her zaman öncelikle bunu otomatik olarak .NET Framework'ün sonraki bir sürüme güncelleştirilmesi, belirlemek için uygulamayı yüklemek denemelisiniz. Kullanmıyorsa, bir uygulama güncelleştirmesi için ISV'nize başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](../../../docs/framework/install/dotnet-35-windows-10.md)
