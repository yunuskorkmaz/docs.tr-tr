---
ms.openlocfilehash: 3275865cf7f4669ba7deaacea320136d02f64dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804249"
---

**{DotNet-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden** benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

Aşağıdaki komut kümesinde iki yer tutucu vardır.

- `{dotnet-package}`\
Bu, yüklemekte olduğunuz .NET paketini (gibi) temsil eder `aspnetcore-runtime-3.1` . Bu, aşağıdaki `sudo apt-get install` komutta kullanılır.

- `{os-version}`\
Bu, kullandığınız dağıtım sürümünü temsil eder. Bu, `wget` aşağıdaki komutta kullanılır. Dağıtım sürümü, `20.04` Ubuntu veya Dete gibi sayısal bir değerdir `10` .

Önce paket listesini temizlemeyi deneyin:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Ardından, .NET 'i yeniden yüklemeyi deneyin. Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:
