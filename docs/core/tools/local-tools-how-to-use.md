---
title: 'Öğretici: .NET Core yerel araçlarını yükleyin ve kullanın'
description: Yerel bir araç olarak bir .NET aracını nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156705"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

Bu öğretici, yerel bir aracı nasıl yükleyip kullanacağınızı öğretir. [Bu serinin ilk öğretici](global-tools-how-to-create.md)oluşturduğunuz bir araç kullanın.

## <a name="prerequisites"></a>Önkoşullar

* Bu [serinin ilk öğretici](global-tools-how-to-create.md)tamamlayın.
* .NET Core 2.1 çalışma süresini yükleyin.

  Bu öğretici için .NET Core 2.1'i hedefleyen bir araç yükler ve kullanırsınız, bu nedenle makinenizde çalışma zamanının yüklü olması gerekir. 2.1 çalışma süresini yüklemek için [.NET Core 2.1 indirme sayfasına](https://dotnet.microsoft.com/download/dotnet-core/2.1) gidin ve **Run uygulamaları - Runtime** sütununda çalışma zamanı yükleme bağlantısını bulun.

## <a name="create-a-manifest-file"></a>Bir bildirim dosyası oluşturma

Yalnızca yerel erişim için bir araç yüklemek için (geçerli dizin ve alt dizinler için), bir bildirim dosyasına eklenmesi gerekir.

*microsoft.botsay* klasöründen, bir düzeyyukarı depo *klasörüne* gidin:

```console
cd ..
```

[dotnet yeni](dotnet-new.md) komutunu çalıştırarak bir bildirim dosyası oluşturun:

```dotnetcli
dotnet new tool-manifest
```

Çıktı, dosyanın başarılı bir şekilde oluşturuldurunan kısmı gösterir.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

*.config/dotnet-tools.json* dosyasında henüz hiçbir araç bulunmamaktadır:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Bir bildirim dosyasında listelenen araçlar geçerli dizin ve alt dizinler tarafından kullanılabilir. Geçerli dizin, *.config* dizinini içeren dizindir.

Yerel bir araca atıfta bulunan bir CLI komutu kullandığınızda, SDK geçerli dizinde ve üst dizinde bir bildirim dosyası arar. Bir bildirim dosyası bulursa, ancak dosya başvurulan aracı içermiyorsa, ana dizinler aracılığıyla aramaya devam eder. Başvurulan aracı bulduğunda veya `isRoot` `true`'' için ayarlanmış bir manifesto dosyası bulduğunda arama sona erer.

## <a name="install-botsay-as-a-local-tool"></a>Botsay'ı yerel bir araç olarak yükleyin

Aracı ilk öğreticide oluşturduğunuz paketten yükleyin:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Bu komut, aracı önceki adımda oluşturduğunuz bildirim dosyasına ekler. Komut çıktısı, yeni yüklenen aracın hangi bildirim dosyasında olduğunu gösterir:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

*.config/dotnet-tools.json* dosyasının artık bir aracı vardır:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>Aracı kullanma

`dotnet tool run` *Depo* klasöründen komutu çalıştırarak aracı çağırın:

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Başkaları tarafından yüklenen yerel bir aracı geri yükleme

Genellikle deponun kök dizinine yerel bir araç yüklersiniz. Manifesto dosyasını depoya iade ettikten sonra, diğer geliştiriciler en son bildirim dosyasını alabilir. Bildirim dosyasında listelenen tüm araçları yüklemek için tek `dotnet tool restore` bir komut çalıştırabilirsiniz.

1. *.config/dotnet-tools.json* dosyasını açın ve içindekileri aşağıdaki JSON ile değiştirin:

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. Projeyi oluşturmak için kullandığınız adla değiştirin. `<name>`

1. Yaptığınız değişiklikleri kaydedin.

   Bu değişikliği yapmak, başka biri proje dizininin paketini `dotnetsay` yükledikten sonra depodan en son sürümü almakla aynıdır.

1. `dotnet tool restore` komutunu çalıştırın.

   ```dotnetcli
   dotnet tool restore
   ```

   Komut aşağıdaki örnek gibi çıktı üretir:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Araçların kullanılabilir olduğundan doğrulayın:

   ```dotnetcli
   dotnet tool list
   ```

   Çıktı, aşağıdaki örneğe benzer şekilde paketlerin ve komutların bir listesidir:

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Araçları test edin:

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Yerel bir aracı güncelleştirme

Yerel aracın `dotnetsay` yüklü sürümü 2.1.3'tür.  En son sürümü 2.1.4 olduğunu. Aracı en son sürüme güncellemek için [dotnet araç güncelleştirme](dotnet-tool-update.md) komutunu kullanın.

```dotnetcli
dotnet tool update dotnetsay
```

Çıktı yeni sürüm numarasını gösterir:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Güncelleştirme komutu, paket kimliğini içeren ilk bildirim dosyasını bulur ve güncelleştirir. Arama kapsamında ki herhangi bir bildirim dosyasında böyle bir paket kimliği yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler. Arama kapsamı, bir `isRoot = true` bildirim dosyası bulunana kadar üst dizinler aracılığıyla tamamlanır.

## <a name="remove-local-tools"></a>Yerel araçları kaldırma

Yüklü araçları [dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak kaldırın:

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

Daha fazla bilgi için [bkz.](global-tools.md)
