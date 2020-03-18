---
title: Yerelleştirilmiş IntelliSense dosyalarını yükleme
description: Visual Studio'daki .NET Core projeleri için yerelleştirilmiş IntelliSense dosyalarını kullanmak üzere geliştirme makinenizi nasıl ayarlayabilirsiniz öğrenin.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157719"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>.NET Core için yerelleştirilmiş IntelliSense dosyaları nasıl yüklenir?

[IntelliSense,](/visualstudio/ide/using-intellisense) Visual Studio gibi farklı tümleşik geliştirme ortamlarında (IME' ler) kullanılabilen bir kod tamamlama yardımıdır. Varsayılan olarak, .NET Core projeleri geliştirirken, SDK yalnızca IntelliSense dosyalarının İngilizce sürümünü içerir. Bu makalede açıklanmaktadır:

- Bu dosyaların yerelleştirilmiş sürümünü yükleme.
- Farklı bir dil kullanmak için Visual Studio yüklemesi nasıl değiştirilir.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya daha sonraki bir sürüm.
- [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha sonraki bir sürüm.

## <a name="download-and-install-the-localized-intellisense-files"></a>Yerelleştirilmiş IntelliSense dosyalarını indirin ve kurun

> [!IMPORTANT]
> Bu yordam, IntelliSense dosyalarını .NET Core yükleme klasörüne kopyalamak için yönetici iznine sahip olmayı gerektirir.

1. [IntelliSense dosyalarını indir](https://dotnet.microsoft.com/download/dotnet-core/intellisense) sayfasına gidin.

1. Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.

1. Zip dosyasının içeriğini ayıklayın.

1. .NET Core Intellisense klasörüne gidin.

   1. .NET Core yükleme klasörüne gidin. Varsayılan olarak, *%ProgramFiles%\dotnet\packs*altındadır.
   1. IntelliSense'i yüklemek istediğiniz SDK'yı seçin ve ilişkili yola gidin. Aşağıdaki seçenekleriniz vardır:

      | SDK türü        | Yol                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft.NETCore.App.Ref*        |
      | Windows Masaüstü | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard   | *NETStandard.Library.Ref*          |

   1. Yerelleştirilmiş IntelliSense'i yüklemek istediğiniz sürüme gidin. Örneğin, *3.1.0*.
   1. *Ref* klasörünü açın.
   1. Takma addklasörü açın. Örneğin, *netcoreapp3.1*.

   Yani, gitmek istiyorum tam yol C benzer *görünecektir:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.

1. Az önce açtığınız takma addklasörün içinde bir alt klasör oluşturun. Klasörün adı hangi dili kullanmak istediğinizi gösterir. Aşağıdaki tabloda farklı seçenekler belirtin:

   | Dil              | Klasör adı |
   | --------------------- | ----------- |
   | Brezilya Portekizcesi  | *pt-br*     |
   | Çince (basitleştirilmiş)  | *zh-hans*   |
   | Çince (geleneksel) | *zh-hant*   |
   | Fransızca                | *Fr*        |
   | Almanca                | *de*        |
   | İtalyanca               | *bu*        |
   | Japonca              | *Ja*        |
   | Korece                | *ko*        |
   | Rusça               | *Ru*        |
   | İspanyolca               | *Es*        |

1. Adım 3'te ayıkladığınız *.xml* dosyalarını bu yeni klasöre kopyalayın. *.xml* dosyaları SDK klasörlerine göre ayrılmıştır, bu nedenle bunları adım 4'te seçtiğiniz eşleşen SDK'ya kopyalayın.

## <a name="modify-visual-studio-language"></a>Visual Studio dilini değiştirin

Visual Studio'nun IntelliSense için farklı bir dil kullanması için uygun dil paketini yükleyin. Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesini değiştirerek yapılabilir. Visual Studio'yu seçtiğiniz dile göre yapılandırmışsanız, IntelliSense yüklemeniz hazırdır.

### <a name="install-the-language-pack"></a>Dil paketini yükleme

Kurulum sırasında istediğiniz dil paketini yüklemediyseniz, dil paketini yüklemek için Visual Studio'yu aşağıdaki gibi güncelleştirin:

> [!IMPORTANT]
> Visual Studio'yı yüklemek, güncellemek veya değiştirmek için yönetici izni olan bir hesapla oturum açmanız gerekir. Daha fazla bilgi için [Kullanıcı izinlerine ve Visual Studio'ya](/visualstudio/ide/user-permissions-and-visual-studio)bakın.

1. Bilgisayarınızda Visual Studio Yükleyicisini bulun.

   Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından Visual **Studio Installer**olarak listelenen **V**harfine gidin.

   ![Windows'tan Visual Studio Yükleyicisini Açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Visual Studio Yükleyicisini aşağıdaki konumda da bulabilirsiniz:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Öyleyse, istemleri izleyin.

1. Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü arayın ve ardından **Değiştir'i**seçin.

   ![Visual Studio'yı güncelleştirin veya değiştirin](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > **Değiştir** düğmesi görmüyorsanız ancak bunun yerine bir **Güncelleme** düğmesi görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio'nuzu güncellemeniz gerekir.
   > Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.

1. Dil **paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçin.

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. **Değiştir'i**seçin. Güncelleştirme başlar.

### <a name="modify-language-settings-in-visual-studio"></a>Visual Studio'da dil ayarlarını değiştirme

İstediğiniz dil paketlerini yükledikten sonra Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kodsuz Devam**et'i seçin.

1. Menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin. Seçenekler iletişim kutusu açılır.

1. **Çevre** düğümü altında, **Uluslararası Ayarlar'ı**seçin.

1. **Dil** açılır tarihinde istediğiniz dili seçin. **Tamam'ı**seçin.

1. Bir iletişim kutusu, değişikliklerin etkili olması için Visual Studio'yu yeniden başlatmanız gerektiğini bildirir. **Tamam'ı**seçin.

1. Visual Studio'yu yeniden başlatın.

Bundan sonra, IntelliSense'iniz, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET Core projesini açtığınızda beklendiği gibi çalışmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense in Visual Studio](/visualstudio/ide/using-intellisense)
