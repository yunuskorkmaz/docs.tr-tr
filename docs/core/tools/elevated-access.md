---
title: Dotnet komutları için yükseltilmiş erişim
description: Yükseltilmiş erişim gerektiren dotnet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410646"
---
# <a name="elevated-access-for-dotnet-commands"></a>Dotnet komutları için yükseltilmiş erişim

Yazılım geliştirme en iyi uygulamalar, az ayrıcalık gerektiren yazılım yazma için Geliştirici Kılavuzu. Ancak, performans araçları, izleme gibi bazı yazılım nedeniyle işletim sistemi kuralları yönetici izni gerektirir. Aşağıdaki yönergeler, yazılımla .NET Core ile yazmak için desteklenen senaryolar açıklanmaktadır. 

Aşağıdaki komutları yükseltilmiş çalıştırılabilir:

- `dotnet tool` gibi komutlar [dotnet aracı yükleme](dotnet-tool-install.md).
- `dotnet run --no-build`

Diğer komutlar yükseltilmiş çalıştıran önerilmemektedir. Özellikle, yükseltme ile MSBuild gibi kullandığınız komutlar önermemekteyiz [dotnet restore](dotnet-restore.md), [dotnet derleme](dotnet-build.md), ve [çalıştırma dotnet](dotnet-run.md). Kullanıcı geri ve İleri kök ve sınırlı bir hesap arasında dotnet komutları kestikten sonra geçiş yaptığında birincil izin yönetimi sorunlarını sorunudur. Kök kullanıcı tarafından oluşturulmuş dosyaya erişime sahip olmadığından, sınırlı bir kullanıcı bulabilirsiniz. Bu sorunu çözmek için vardır, ancak bunların başlangıçta içine alın gerekmez.

Kök ve sınırlı bir hesap arasında sürekli geçiş yoksa sürece komutları kök olarak çalıştırın. Örneğin, bu özellik sahip oldukları için Docker kapsayıcılarını varsayılan olarak, kök olarak çalıştırın.

## <a name="global-tool-installation"></a>Genel aracı yükleme

Aşağıdaki yönergeler, yükleme, çalıştırma ve yürütmek için yükseltilmiş izinler gerektirir ve .NET Core Araçları'nı kaldırmak için önerilen yol gösterir.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Genel aracı yükleme

Varsa klasörü `%ProgramFiles%\dotnet-tools` zaten var "Kullanıcılar" grubunu yazın veya bu dizine değiştirmek için izni olup olmadığını denetlemek için aşağıdakileri yapın:

* Sağ `%ProgramFiles%\dotnet-tools` klasörü ve select **özellikleri**. **Ortak özellikler** iletişim kutusu açılır. 
* Seçin **güvenlik** sekmesi. Altında **grup veya kullanıcı adları**, "Kullanıcılar" grubunu yazma veya dizin değiştirme iznine sahip olup olmadığını denetleyin. 
* "Kullanıcılar" grubunu yazma veya dizinini değiştirin, Araçlar yüklenirken farklı dizin adı kullanmak yerine *dotnet-tools*.

Araçları yüklemek için yükseltilmiş isteminde aşağıdaki komutu çalıştırın. Oluşturacağı *dotnet-tools* yüklenmesi sırasında klasör.

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Genel aracı çalıştırın

**1. seçenek** yükseltilmiş istemiyle tam yolu kullanın:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**2. seçenek** eklemek için yeni oluşturulan klasör `%Path%`. Yalnızca bir kez bu işlemi yapmanız gerekir.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

Ve çalıştırın:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Genel Aracı kaldırma

Yükseltilmiş isteminde, aşağıdaki komutu yazın:

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Yerel Araçlar

Yerel Araçlar, kullanıcı başına alt ağacı başına belirlenir. Yükseltilmiş çalıştırdığınızda, yerel Araçlar yükseltilmiş ortamı için kısıtlı kullanıcı ortamını paylaşın. Linux ve macOS, kök yalnızca kullanıcı erişimi ile ayarlanan dosyaları sonuçlanır. Kullanıcı, kısıtlı bir hesapta geçerse, kullanıcı artık erişmek veya dosyalara yazmak. Bu nedenle yerel araçlar olarak yetki yükseltmesi gerektiren araçlarını yükleme önerilmez. Bunun yerine, `--tool-path` seçeneği ve genel araçları için önceki yönergeleri.

## <a name="elevation-during-development"></a>Geliştirme sırasında yükseltme

Geliştirme sırasında uygulamanızı test etmek için yükseltilmiş erişim gerekebilir. Bu örneğin IOT uygulamaları için yaygın senaryodur. Yükseltme olmadan uygulamayı derleyin ve ardından yükseltme ile çalıştırın öneririz. Aşağıdaki gibi birkaç desen vardır:

- Oluşturulan yürütülebilir dosya (en iyi başlangıç performansı sağlar) kullanarak:

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Kullanarak [çalıştırma dotnet](dotnet-run.md) komutunu `—no-build` yeni ikili dosyaları oluşturmamak üzere bayrağı:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core Araçları Genel genel bakış](global-tools.md)
