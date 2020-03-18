---
title: dotnet komutları için yüksek erişim
description: Yüksek erişim gerektiren dotnet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156770"
---
# <a name="elevated-access-for-dotnet-commands"></a>dotnet komutları için yüksek erişim

Yazılım geliştirme en iyi uygulamaları ayrıcalık en az miktarda gerektiren yazılım yazma geliştiricileri rehberlik eder. Ancak, performans izleme araçları gibi bazı yazılımlar, işletim sistemi kuralları nedeniyle yönetici izni gerektirir. Aşağıdaki kılavuzda, bu tür yazılımları .NET Core ile yazmak için desteklenen senaryolar açıklanmaktadır.

Aşağıdaki komutlar yükseltilebilir:

- `dotnet tool`[komutları, dotnet aracı yükleme](dotnet-tool-install.md)gibi .
- `dotnet run --no-build`

Diğer komutları yükseltmenizi önermiyoruz. Özellikle, [biz dotnet geri yükleme, dotnet](dotnet-restore.md) [yapı](dotnet-build.md)ve [dotnet çalıştırmak](dotnet-run.md)gibi MSBuild kullanan komutları ile yükseklik önermiyoruz. Birincil sorun, bir kullanıcı dotnet komutları verdikten sonra kök ve kısıtlı bir hesap arasında ileri ve geri geçiş yaptığında izin yönetimi sorunlarıdır. Kısıtlanmış bir kullanıcı olarak, bir kök kullanıcı tarafından oluşturulmuş dosyaya erişiminiz olmadığını görebilirsiniz. Bu durumu çözmenin yolları var, ama en başta içine girmek için gereksiz.

Kök ve kısıtlı bir hesap arasında geçiş yapmadığınız sürece komutları kök olarak çalıştırabilirsiniz. Örneğin, Docker kapsayıcıları varsayılan olarak kök olarak çalıştırın, bu nedenle bu özelliğe sahiptirler.

## <a name="global-tool-installation"></a>Genel takım kurulumu

Aşağıdaki yönergeler, yürütmek için yüksek izinler gerektiren .NET Core araçlarını yükleme, çalıştırma ve kaldırmanın önerilen yolunu gösterir.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Aracı yükleme

Klasör `%ProgramFiles%\dotnet-tools` zaten varsa, "Kullanıcılar" grubunun bu dizini yazma veya değiştirme izni olup olmadığını denetlemek için aşağıdakileri yapın:

- Klasöre `%ProgramFiles%\dotnet-tools` sağ tıklayın ve **Özellikler'i**seçin. **Ortak Özellikler** iletişim kutusu açılır.
- **Güvenlik** sekmesini seçin. **Grup veya kullanıcı adları**altında, "Kullanıcılar" grubunun dizini yazma veya değiştirme izni olup olmadığını kontrol edin.
- "Kullanıcılar" grubu dizini yazabilir veya değiştirebiliyorsa, *araçları dotnet araçları*yerine yüklerken farklı bir dizin adı kullanın.

Araçları yüklemek için aşağıdaki komutu yükseltilmiş komut isteminde çalıştırın. Yükleme sırasında *dotnet-tools* klasörünü oluşturur.

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Genel aracı çalıştırma

**Seçenek 1** Yükseltilmiş komut istemi ile tam yolu kullanın:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Seçenek 2** Yeni oluşturulan klasörü `%Path%`. Bu işlemi sadece bir kez yapmanız gerekir.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

Ve ile çalıştırın:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Genel aracı kaldırma

Yükseltilmiş bir istemi olarak, aşağıdaki komutu yazın:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[Macos](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Yerel araçlar

Yerel araçlar, kullanıcı başına alt dizin ağacı başına kapsamlıdır. Yüksek çalıştırıldığında, yerel araçlar kısıtlı bir kullanıcı ortamını yükseltilmiş ortamla paylaşır. Linux ve macOS'ta bu, yalnızca root kullanıcı erişimine sahip dosyaların ayarlandığına neden olur. Kullanıcı kısıtlı bir hesaba geri dönerse, kullanıcı artık dosyalara erişemez veya dosyalara yazamaz. Bu nedenle, yerel araçlar olarak yükseklik gerektiren araçların yüklenmesi önerilmez. Bunun yerine, `--tool-path` genel araçlar için seçeneği ve önceki yönergeleri kullanın.

## <a name="elevation-during-development"></a>Geliştirme sırasında yükseklik

Geliştirme sırasında, uygulamanızı test etmek için yüksek erişim gerekebilir. Bu senaryo, örneğin IoT uygulamaları için yaygındır. Uygulamayı yükseklik olmadan oluşturmanızı ve yükseklik ile çalıştırmanızı öneririz. Aşağıdaki gibi birkaç desen vardır:

- Oluşturulan çalıştırılabilir (en iyi başlangıç performansını sağlar) kullanarak:

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Yeni ikililer oluşturmamak için `—no-build` [bayrakla dotnet çalıştırma](dotnet-run.md) komutunu kullanma:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core Global Tools genel bakış](global-tools.md)
