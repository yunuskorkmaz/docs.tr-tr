---
title: Çalıştırma .NET Framework 1.1 uygulamalarını Windows 8, Windows 8.1 veya Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b234d4e2fe7d5efe0a6c33f61b9ba422b55803d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Çalıştırma .NET Framework 1.1 uygulamalarını Windows 8, Windows 8.1 veya Windows 10

.NET Framework 1.1 desteklenmiyor [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10 işletim sistemleri. Bazı durumlarda, .NET Framework 1.1 özellikle tanımlanır çalıştırmak bir uygulama için gerekli. Bu durumlarda, bağımsız yazılım satıcısı (ISV) çalıştırmak için yükseltilmiş uygulamanız için başvurmalıdır [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü. Ek bilgi için bkz: [.NET Framework 1. 1 ' geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>.NET Framework 1.1 bir CD veya Yükleme Merkezi'nden yükleyin

.NET Framework 1.1 el ile yüklemek kurulamadığı [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], veya Windows 10. Artık desteklenmiyor. Paket yüklemeye çalışırsanız, aşağıdaki hata iletisi görüntülenir: "İçin kurulum devam edemiyor .NET Framework'ün bu sürümü ile önceden yüklenmiş bir tane uyumlu değil." Bu sorunu çözmek için yükleme [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22). Bu sürüm, .NET Framework üzerinde desteklenen 2.0 (.NET Framework 1.1 izleyen sürüm) içerir [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]ve Windows 10. Her zaman otomatik olarak .NET Framework'ün sonraki bir sürüme güncelleştirilir, ilk belirlemek için uygulamayı yüklemek denemelisiniz. Mevcut değilse, ISV bir uygulama güncelleştirmesi başvurun.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework 1.1 geçirme](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[.NET Framework 3.5 Windows 10, Windows 8.1 ve Windows 8 yükleme](../../../docs/framework/install/dotnet-35-windows-10.md)
