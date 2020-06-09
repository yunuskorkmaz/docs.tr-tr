---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602987"
---

**{Netcore-Package} paketi bulunamıyor**hatasıyla benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

Aşağıdaki komut kümesinde iki yer tutucu vardır.

- `{dotnet-package}`\
Bu, yüklemekte olduğunuz .NET Core paketini (gibi) temsil eder `aspnetcore-runtime-3.1` . Bu, `sudo apt-get install` aşağıdaki komutta kullanılır.

- `{os-version}`\
Bu, açık olduğunuz Linux sürümünü temsil eder. Bu, `wget` aşağıdaki komutta kullanılır.

Paket listesini temizlemeyi deneyin:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:
