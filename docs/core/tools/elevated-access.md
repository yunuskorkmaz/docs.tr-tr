---
title: DotNet komutları için yükseltilmiş erişim
description: Yükseltilmiş erişim gerektiren DotNet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: b6de87f375a584da25e160d79f51f1bc48f3c302
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969858"
---
# <a name="elevated-access-for-dotnet-commands"></a>DotNet komutları için yükseltilmiş erişim

Yazılım geliştirme en iyi uygulamaları, geliştiricilerin en az ayrıcalık gerektiren yazılımları yazmasını sağlar. Ancak, performans izleme araçları gibi bazı yazılımlar, işletim sistemi kuralları nedeniyle yönetici izni gerektirir. Aşağıdaki kılavuzda .NET Core ile bu tür yazılımları yazmaya yönelik desteklenen senaryolar açıklanmaktadır. 

Aşağıdaki komutlar yükseltilmiş olarak çalıştırılabilir:

- `dotnet tool`[DotNet aracı yüklemesi](dotnet-tool-install.md)gibi komutlar.
- `dotnet run --no-build`

Diğer komutların yükseltilme çalıştırılmasını önermiyoruz. Özellikle, [DotNet restore](dotnet-restore.md), [DotNet Build](dotnet-build.md)ve [DotNet Run](dotnet-run.md)gibi MSBuild kullanan komutlarla yükseltmeyi önermiyoruz. Birincil sorun, bir Kullanıcı DotNet komutları verdikten sonra kök ve kısıtlanmış bir hesap arasında geri ve ileri geçiş yaptığında izin yönetimi sorunlardır. Bir kök kullanıcı tarafından oluşturulan dosyaya erişiminizin olmadığı kısıtlı bir kullanıcı olarak bulunabilir. Bu durumu çözmek için bazı yollar vardır, ancak ilk yerde içine aktarılmaları gereksizdir.

Kök ve sınırlı hesap arasında geri geçiş yapmıyorsanız ve komutları kök olarak çalıştırabilirsiniz. Örneğin, Docker Kapsayıcıları varsayılan olarak kök olarak çalışır, bu nedenle bu özelliğe sahiptirler.

## <a name="global-tool-installation"></a>Küresel araç yüklemesi

Aşağıdaki yönergelerde, yürütme için yükseltilmiş izinler gerektiren .NET Core araçlarını yüklemek, çalıştırmak ve kaldırmak için önerilen yol gösterilmektedir.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Genel aracı 'nı yükler

Klasör `%ProgramFiles%\dotnet-tools` zaten mevcutsa, "kullanıcılar" grubunun bu dizini yazma veya değiştirme izni olup olmadığını denetlemek için aşağıdakileri yapın:

- `%ProgramFiles%\dotnet-tools` Klasöre sağ tıklayın ve **Özellikler**' i seçin. **Ortak özellikler** iletişim kutusu açılır. 
- **Güvenlik** sekmesini seçin. **Grup veya Kullanıcı adları**altında "kullanıcılar" grubunun dizini yazma veya değiştirme izni olup olmadığını denetleyin. 
- "Kullanıcılar" grubu dizini yazabilir veya değiştirebiliyorsanız, *DotNet araçları*yerine araçları yüklerken farklı bir dizin adı kullanın.

Araçları yüklemek için, yükseltilmiş komut isteminde aşağıdaki komutu çalıştırın. Yükleme sırasında *DotNet araçları* klasörünü oluşturur.

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Genel aracı çalıştırma

**Seçenek 1** Tam yolu yükseltilmiş istemle kullanın:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Seçenek 2** Yeni oluşturulan klasörü öğesine `%Path%`ekleyin. Bu işlemi yalnızca bir kez yapmanız gerekir.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

Ve şunu çalıştırın:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Genel aracı kaldır

Yükseltilmiş bir komut isteminde aşağıdaki komutu yazın:

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Yerel Araçlar

Yerel araçlar, Kullanıcı başına alt dizin ağacı başına kapsamlandırılır. Yükseltilmiş olarak çalıştırıldığında yerel araçlar, kısıtlı bir Kullanıcı ortamını yükseltilmiş ortamda paylaşır. Linux ve macOS 'ta bu, dosyaların yalnızca kök kullanıcı erişimiyle ayarlanmasına neden olur. Kullanıcı kısıtlı bir hesaba geri geçtiğinde, Kullanıcı artık dosyalara erişemez veya dosyalara yazamaz. Bu nedenle, yerel araçlar olarak yükseltme gerektiren araçların yüklenmesi önerilmez. Bunun yerine, genel `--tool-path` araçlar için seçeneğini ve önceki yönergeleri kullanın.

## <a name="elevation-during-development"></a>Geliştirme sırasında yükseltme

Geliştirme sırasında uygulamanızı test etmek için yükseltilmiş erişime sahip olabilirsiniz. Bu senaryo, IoT uygulamaları için yaygın olarak kullanılan bir örnektir. Uygulamayı yükseltme olmadan oluşturmanızı ve ardından yükseltme ile çalıştırmayı öneririz. Aşağıda gösterildiği gibi birkaç desen vardır:

- Oluşturulan yürütülebiliri kullanma (en iyi başlangıç performansını sağlar):

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Yeni ikililer oluşturmaktan kaçınmak için, `—no-build` [DotNet Run](dotnet-run.md) komutunu bayrağıyla birlikte kullanma:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core genel araçlarına genel bakış](global-tools.md)
