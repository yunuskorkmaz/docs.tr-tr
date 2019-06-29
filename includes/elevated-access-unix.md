---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424704"
---
### <a name="install-the-global-tool"></a>Genel aracı yükleme

Bir korumalı konumu kullanarak paket varlıklar yüklenmelidir `--tool-path` seçeneği. Bu ayrım, kısıtlı kullanıcı ortamını ile yükseltilmiş bir ortam paylaşımı önler.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools` izinle oluşturulacak `drwxr-xr-x`. Dizin zaten varsa, kullanmak `ls -l` kısıtlı kullanıcı dizini düzenleme izni yoksa doğrulamak için komutu. Bu durumda, kullanın `sudo chmod o-w -R /usr/share/dotnet-tools` erişimi kaldırmak için komutu.

### <a name="run-the-global-tool"></a>Genel aracı çalıştırın

**1. seçenek** sudo ile tam yolu kullanın:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**2. seçenek** aracının her aracı için bir kez sembol bağlantı ekleyin:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

Ve çalıştırın:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Genel Aracı kaldırma

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Sembol bağlantı yaptıysanız de kaldırmanız gerekir:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```