---
title: Windows 7 SP1 'e .NET Framework yüklemesi
description: Windows 7 SP1 'e .NET Framework yüklemeyi öğrenin.
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899093"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a>Windows 7 SP1 ve Windows Server 2008 R2’de .NET Framework Yükleme

.NET Framework Windows üzerinde birçok uygulama çalıştırmak için gereklidir. Yüklemek için aşağıdaki yönergeleri kullanabilirsiniz. Bir uygulamayı çalıştırmayı ve makinenizde aşağıdaki iletişim kutusunu görmenizi tamamladıktan sonra bu sayfada ulaşmış olabilirsiniz.

![Bu uygulama başlatılamadı](./media/this-application-could-not-be-started.png)

Bu yönergeler, ihtiyacınız olan .NET Framework sürümlerini yüklemenize yardımcı olur. [.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) en son sürümdür. Windows 7 SP1 ve Windows Server 2008 R2 'de desteklenir ve [Windows 10 mayıs 2019 güncelleştirmesine](https://support.microsoft.com/help/4028685/windows-10-get-the-update)dahildir.

## <a name="net-framework-48"></a> .NET Framework 4.8

> [!div class="button"]
> [.NET Framework 4.8'i İndirin](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) , .NET Framework 4,0 veya üzeri için oluşturulmuş uygulamaları çalıştırmak için kullanılabilir.

### <a name="offline-installer"></a>Çevrimdışı yükleyici

Windows 7 ' de .NET Framework için çevrimdışı yükleme yaparken öncelikle hedef makineye en son [Microsoft kök sertifika yetkilisi 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) ' nin yüklü olduğundan emin olmanız gerekir.

_certmgr.exe_ aracı bir sertifikayı yüklemeyi otomatikleştirebilir ve Visual Studio 'dan veya Windows SDK elde edilebilir. Aşağıdaki komut, .NET Framework yükleyicisini çalıştırmadan önce sertifikayı yüklemek için kullanılır:

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a>.NET Framework 3.5

[3,5 .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) , Windows 7 ' ye dahildir.

.NET Framework 3,5 ile 3,5 .NET Framework 1,0 için oluşturulmuş uygulamaları destekler.

## <a name="help"></a>Yardım

.NET Framework yüklü olan doğru sürümü alamazsanız, [Yardım Için Microsoft 'a başvurabilirsiniz](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework indirin](https://dotnet.microsoft.com/download)
- [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md)
- [Geliştiriciler için .NET Framework yüklemesi](guide-for-developers.md)
