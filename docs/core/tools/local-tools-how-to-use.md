---
title: 'Öğretici: .NET Core yerel araçlarını yükleyip kullanın'
description: .NET aracını yerel bir araç olarak yüklemeyi ve kullanmayı öğrenin.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 555497a71d54713e62e54f8f293afdf74ead1743
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062684"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

Bu öğretici, yerel bir araç yüklemeyi ve kullanmayı öğretir. [Bu serinin ilk öğreticisinde](global-tools-how-to-create.md)oluşturduğunuz bir aracı kullanırsınız.

## <a name="prerequisites"></a>Önkoşullar

* [Bu serinin ilk öğreticisini](global-tools-how-to-create.md)doldurun.
* .NET Core 2,1 çalışma zamanını yükler.

  Bu öğreticide, .NET Core 2,1 ' i hedefleyen bir araç yükleyip kullanacaksınız, bu yüzden çalışma zamanının makinenizde yüklü olması gerekir. 2,1 çalışma zamanını yüklemek için [.NET Core 2,1 indirme sayfasına](https://dotnet.microsoft.com/download/dotnet-core/2.1) gidin ve **Çalıştır-çalışma zamanı** sütununda çalışma zamanı yükleme bağlantısını bulun.

## <a name="create-a-manifest-file"></a>Bildirim dosyası oluşturma

Yalnızca yerel erişim için bir araç yüklemek üzere (geçerli dizin ve alt dizinler için), bir bildirim dosyasına eklenmelidir.

*Microsoft. botsay* klasöründen, *Depo* klasörü için bir düzey yukarı gidin:

```console
cd ..
```

[DotNet yeni](dotnet-new.md) komutunu çalıştırarak bir bildirim dosyası oluşturun:

```dotnetcli
dotnet new tool-manifest
```

Çıktı, dosyanın başarıyla oluşturulmasını gösterir.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Dosya *üzerinde. config/dotnet-tools.js* henüz bir araç içermiyor:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Bir bildirim dosyasında listelenen araçlar geçerli dizin ve alt dizinler için kullanılabilir. Geçerli dizin, bildirim dosyası ile *. config* dizinini içeren bir dizindir.

Yerel bir araca başvuran bir CLı komutu kullandığınızda, SDK geçerli dizin ve üst dizinlerde bir bildirim dosyası arar. Bir bildirim dosyası bulursa, ancak dosya başvurulan aracı içermiyorsa, üst dizinlere göre aramaya devam eder. Arama, başvurulan aracı bulduğunda sona erer veya olarak ayarlanmış bir bildirim dosyası bulur `isRoot` `true` .

## <a name="install-botsay-as-a-local-tool"></a>Botsay 'ı yerel araç olarak yükler

Aracı ilk öğreticide oluşturduğunuz paketten yükleyebilirsiniz:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Bu komut, önceki adımda oluşturduğunuz bildirim dosyasına aracı ekler. Komut çıktısı, yeni yüklenen aracın hangi bildirim dosyasında olduğunu gösterir:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Dosyadaki *. config/dotnet-tools.js* artık bir araca sahiptir:

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

`dotnet tool run`Komutu *Depo* klasöründen çalıştırarak aracı çağırın:

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Başkaları tarafından yüklenen bir yerel aracı geri yükleme

Genellikle deponun kök dizinine yerel bir araç yüklersiniz. Bildirim dosyasını depoya iade ettikten sonra, diğer geliştiriciler en son bildirim dosyasını alabilir. Bildirim dosyasında listelenen tüm araçları yüklemek için, tek bir `dotnet tool restore` komut çalıştırabilir.

1. Dosya *üzerinde. config/dotnet-tools.js* açın ve IÇERIĞINI aşağıdaki JSON ile değiştirin:

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

1. `<name>`Projeyi oluşturmak için kullandığınız adla değiştirin.

1. Yaptığınız değişiklikleri kaydedin.

   Bu değişikliğin yapılması, proje dizini paketini başka birisi yükledikten sonra depodan en son sürümü alma ile aynıdır `dotnetsay` .

1. `dotnet tool restore` komutunu çalıştırın.

   ```dotnetcli
   dotnet tool restore
   ```

   Komut aşağıdaki örnekte olduğu gibi bir çıktı üretir:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Araçların kullanılabilir olduğunu doğrulayın:

   ```dotnetcli
   dotnet tool list
   ```

   Çıktı, aşağıdaki örneğe benzer şekilde paketlerin ve komutların listesidir:

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Araçları test etme:

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Yerel bir aracı güncelleştirme

Yerel aracın yüklü sürümü `dotnetsay` 2.1.3.  En son sürüm 2.1.4 ' dir. Aracı en son sürüme güncelleştirmek için [DotNet araç Güncelleştir](dotnet-tool-update.md) komutunu kullanın.

```dotnetcli
dotnet tool update dotnetsay
```

Çıkış, yeni sürüm numarasını gösterir:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Update komutu, paket KIMLIĞINI içeren ilk bildirim dosyasını bulur ve güncelleştirir. Arama kapsamındaki herhangi bir bildirim dosyasında böyle bir paket KIMLIĞI yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler. İle bir bildirim dosyası bulunana kadar arama kapsamı üst dizinler üzerinden çalışır `isRoot = true` .

## <a name="remove-local-tools"></a>Yerel araçları kaldır

[DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak yüklü araçları kaldırın:

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Ayrıca bkz.

Daha fazla bilgi için bkz. [.NET Core araçları](global-tools.md)
