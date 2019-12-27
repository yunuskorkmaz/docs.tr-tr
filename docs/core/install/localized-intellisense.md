---
title: Yerelleştirilmiş IntelliSense dosyalarını yükler
description: Geliştirme makinenizi, Visual Studio 'da .NET Core projeleri için yerelleştirilmiş IntelliSense dosyalarını kullanacak şekilde ayarlamayı öğrenin.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443479"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>.NET Core için yerelleştirilmiş IntelliSense dosyalarını nasıl yükleyeceğiniz

[IntelliSense](/visualstudio/ide/using-intellisense) , Visual Studio gibi farklı tümleşik geliştirme ortamlarında (ides) kullanılabilen bir kod tamamlama yardımıdır. Varsayılan olarak, .NET Core projelerini geliştirirken, SDK yalnızca IntelliSense dosyalarının Ingilizce sürümünü içerir. Bu makalede şunları açıklanmaktadır:

- Bu dosyaların yerelleştirilmiş sürümünü nasıl yükleyeceksiniz.
- Visual Studio yüklemesini farklı bir dil kullanacak şekilde değiştirme.

## <a name="prerequisites"></a>Prerequisites

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.
- [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonraki bir sürümü.

## <a name="download-and-install-the-localized-intellisense-files"></a>Yerelleştirilmiş IntelliSense dosyalarını indirme ve yükleme

> [!IMPORTANT]
> Bu yordam, IntelliSense dosyalarını .NET Core yükleme klasörüne kopyalamak için yönetici iznine sahip olmanızı gerektirir.

1. [IntelliSense dosyalarını indirme](https://dotnet.microsoft.com/download/dotnet-core/intellisense) sayfasına gidin.

1. Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.

1. ZIP dosyasının içeriğini ayıklayın.

1. .NET Core yükleme klasörüne gidin. Varsayılan olarak, *%ProgramFiles%\dotnet\packs*altındadır.

   - IntelliSense 'i yüklemek istediğiniz SDK 'yı seçin ve ilişkili yola gidin. Şu seçenekleriniz vardır:

      | SDK türü        | Yol                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft. NETCore. app. ref*        |
      | Windows Masaüstü | *Microsoft. WindowsDesktop. app. ref* |
      | .NET Standard   | *NETStandard. Library. ref*          |
   
   - Yerelleştirilmiş IntelliSense 'i yüklemek istediğiniz sürüme gidin. Örneğin, *3.1.0*.
   - *Ref* klasörünü açın.
   - Bilinen ad klasörünü açın. Örneğin, *netcoreapp 3.1*.

   Bu nedenle, gittiğiniz yolun tam yolu *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*şuna benzer.

1. Yeni açtığınız bilinen ad klasörünün içinde bir alt klasör oluşturun. Klasörün adı, hangi dili kullanmak istediğinizi belirtir. Aşağıdaki tabloda farklı seçenekler verilmiştir:

   | Dil              | Klasör adı |
   | --------------------- | ----------- |
   | Brezilya Portekizcesi  | *pt-br*     |
   | Çince (Basitleştirilmiş)  | *zh-Hans*   |
   | Çince (Geleneksel) | *zh-Hant*   |
   | Fransızca                | *kesir*        |
   | Almanca                | *seçimini*        |
   | İtalyanca               | *içerdiği*        |
   | Japonca              | *Sofya*        |
   | Korece                | *dili*        |
   | Rusça               | *ru*        |
   | İspanyolca               | *es*        |

1. Adım 3 ' te ayıkladığınız *. xml* dosyalarını bu yeni klasöre kopyalayın. *. Xml* dosyaları SDK klasörleri tarafından bölünür, bu nedenle bunları 4. adımda SEÇTIĞINIZ eşleşen SDK 'ya kopyalayın.

## <a name="modify-visual-studio-language"></a>Visual Studio dilini değiştir

Visual Studio 'nun IntelliSense için farklı bir dil kullanabilmesi için, uygun dil paketini de yüklemelisiniz. Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesi değiştirilerek yapılabilir. Seçtiğiniz dilde Visual Studio zaten yapılandırılmışsa, IntelliSense yüklemeniz hazırlayın.

### <a name="install-the-language-pack"></a>Dil paketini yükler

İstenen dil paketini kurulum sırasında yüklemediyseniz, dil paketini yüklemek için Visual Studio 'Yu aşağıdaki şekilde güncelleştirin:

> [!IMPORTANT]
> Yüklemek, güncelleştirmek veya Visual Studio değiştirmek için yönetici izinleri olan bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

   Örneğin, Windows 10 çalıştıran bir bilgisayarda seçin **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.

   ![Visual Studio Yükleyicisi Windows 'tan açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.

   ![Visual Studio 'Yu güncelleştirme veya değiştirme](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Bir **değiştirme** düğmesi görmüyorsanız ancak bunun yerine bir **güncelleştirme** görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio 'yu güncelleştirmeniz gerekir.
   > Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.

1. **Dil paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçimini kaldırın.

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. **Değiştir**'i seçin. Güncelleştirme başlar.

### <a name="modify-language-settings-in-visual-studio"></a>Visual Studio 'da dil ayarlarını değiştirme

İstenen dil paketlerini yükledikten sonra, Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.

1. Ana menüde **araçlar** > **Seçenekler**' i seçin. Seçenekler iletişim kutusu açılır.

1. **Ortam** klasörü altında **Uluslararası ayarlar**' ı seçin.

1. **Dil** açılan çubuğunda istediğiniz dili seçin. **Tamam**’ı seçin. 

1. Değişikliklerin etkili olması için Visual Studio 'Yu yeniden başlatmanız gerektiğini bildiren bir iletişim kutusu size bildirir. **Tamam**’ı seçin.

1. Visual Studio'yu yeniden başlatın.

Bundan sonra, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET Core projesi açtığınızda IntelliSense, beklendiği gibi çalışmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da IntelliSense](/visualstudio/ide/using-intellisense)
