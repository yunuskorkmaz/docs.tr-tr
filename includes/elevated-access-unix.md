---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540128"
---
### <a name="install-the-global-tool"></a>Genel aracı yükleme

Paket varlıkları `--tool-path` seçeneği kullanılarak korunan bir konuma yüklenmelidir. Bu ayırma, kısıtlı bir kullanıcı ortamını yükseltilmiş bir ortamla paylaşmayı önler.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools`izni `drwxr-xr-x`ile oluşturulacaktır. Dizin zaten varsa, kısıtlı `ls -l` kullanıcının dizini yönetme izni olmadığını doğrulamak için komutu kullanın. Bu öyleyse, `sudo chmod o-w -R /usr/share/dotnet-tools` erişimi kaldırmak için komutu kullanın.

### <a name="run-the-global-tool"></a>Genel aracı çalıştırma

**Seçenek 1** Sudo ile tam yolu kullanın:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Seçenek 2** Aracın sembol bağlantısını, araç başına bir kez ekleyin:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

Ve ile çalıştırın:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Genel aracı kaldırma

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Bir sembol bağlantısı yaptıysanız, bunu kaldırmanız da gerekir:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
