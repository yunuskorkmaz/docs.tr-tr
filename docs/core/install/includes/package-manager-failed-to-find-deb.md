---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506981"
---

**{DotNet-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden** benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

Aşağıdaki komut kümesinde iki yer tutucu vardır.

- `{dotnet-package}`\
Bu, yüklemekte olduğunuz .NET paketini (gibi) temsil eder `aspnetcore-runtime-3.1` . Bu, aşağıdaki `sudo apt-get install` komutta kullanılır.

- `{os-version}`\
Bu, açık olduğunuz Linux sürümünü temsil eder. Bu, `wget` aşağıdaki komutta kullanılır.

Önce paket listesini temizlemeyi deneyin:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Ardından, .NET 'i yeniden yüklemeyi deneyin. Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:
