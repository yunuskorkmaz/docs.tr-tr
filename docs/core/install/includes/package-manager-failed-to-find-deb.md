---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132956"
---

**{Netcore-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden**benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

Aşağıdaki komut kümesinde iki yer tutucu vardır.

- `{dotnet-package}`\
Bu, yüklemekte olduğunuz .NET Core paketini (gibi) temsil eder `aspnetcore-runtime-3.1` . Bu, `sudo apt-get install` aşağıdaki komutta kullanılır.

- `{os-version}`\
Bu, açık olduğunuz Linux sürümünü temsil eder. Bu, `wget` aşağıdaki komutta kullanılır.

Önce paket listesini temizlemeyi deneyin:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Ardından, .NET Core 'u yeniden yüklemeyi deneyin. Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:
