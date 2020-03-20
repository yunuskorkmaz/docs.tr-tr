---
title: Visual Studio için Geliştirici Komut Komut Ustem
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715827"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için Geliştirici Komut Komut Ustem

Visual Studio için Geliştirici Komut Komut Ustem ,.NET Framework araçlarını daha kolay kullanmanızı sağlar. Belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemidir. Geliştirici Komut Komut Ustem'i açtıktan sonra [.NET](index.md) `ildasm` Framework `clrver`araçları nın komutlarını girebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Makinenizde komut istemini arama

Visual Studio'nun sürümüne ve yüklediğiniz ek SDK'lara ve iş yüklerine bağlı olarak birden çok komut isteminiz olabilir. Aşağıdaki adımlar işe yaramazsa, [makinenizdeki dosyaları el ile bulmaya](#manually-locate-the-files-on-your-machine) çalışabilir veya Visual [Studio'nun içinden komut istemini başlatabilirsiniz.](#start-the-command-prompt-from-inside-visual-studio)

### <a name="windows-10"></a>Windows 10

1. Klavyede Windows logotutu **başlat'ı** ![seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve **V**harfine kaydırın.

1. Visual **Studio 2019** klasörünü genişletin.

1. **VS 2019 için Geliştirici Komut Komut Ustem'i** (veya kullanmak istediğiniz komut istemini) seçin.

   Alternatif olarak, görev çubuğundaki arama kutusuna komut isteminin adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladığında istediğiniz sonucu seçebilirsiniz.

   ![Windows 10'daki arama davranışını gösteren animasyonlu gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Klavyedeki **Start** Windows logosu tuşu ![Windows logo tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) örneğin klavyenizde.

1. **Başlangıç** ekranında, **Uygulamalar** listesini açmak için **Ctrl**+**Sekmesine** basın ve ardından **V**tuşuna basın. Bu, yüklenen tüm Visual Studio komut istemlerini içeren bir liste getirir.

1. **VS 2019 için Geliştirici Komut Komut Ustem'i** (veya kullanmak istediğiniz komut istemini) seçin.

### <a name="windows-7"></a>Windows 7

1. **Başlat'ı** seçin ve ardından **Tüm Programları**genişletin.

1. **VS 2019 için**Visual Studio **2019** > Visual Studio**Tools** > Developer Command Prompt'ı veya kullanmak istediğiniz komut istemini seçin.

   ![Komut istemi vurgulanan Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi yüklü başka SDK'lar varsa, ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-files-on-your-machine"></a>Makinenizdeki dosyaları el ile bulma

Genellikle, yüklediğiniz komut istemleri için kısayollar Visual Studio için **Başlat Menüsü** klasörüne yerleştirilir( örneğin *ProgramData%\Microsoft\Windows\Başlat Menüsü\Programlar\Visual Studio 2019\Visual Studio Tools.* Ancak, nedense komut istemini aramak beklenen sonuçları üretmiyorsa, makinenizdeki kısayolu el ile bulmaya çalışabilirsiniz. *VsDevCmd.bat*gibi komut istemi dosyasının adını aramayı deneyin veya *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüze, sürüme ve yükleme konumunuza göre yol değişiklikleri) gibi Araçlar klasörüne gidin.

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Visual Studio'nun içinden komut istemini başlatın

Daha kolay erişim için Visual Studio'daki Araçlar menüsüne Geliştirici Komut Komut Ustem'i veya başka bir komut istemi ekleyebilirsiniz. Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin. Adımlar aşağıdaki gibidir:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kodsuz Devam**et'i seçin.

1. Menü çubuğunda **Araçlar** > **Dış Araçlar'ı**seçin.

1. Dış **Araçlar** iletişim kutusunda **Ekle** düğmesini seçin. Yeni bir giriş görüntülenir.

1. Yeni menü öğeniz **için** başlık `Command Prompt`girin.

1. **Komut** alanında, başlatmak istediğiniz dosyayı belirtin, `%comspec%` `C:\Windows\System32\cmd.exe`örneğin .

1. **Bağımsızlar** alanında, kullanmak istediğiniz komut istemini nerede bulacağınıbelirtin. `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` Bu komut Visual Studio 2019 Topluluğu ile yüklenen Geliştirici Komut Komut Komut Ustem'i başlatın. Bu değeri Visual Studio sürümünüze, sürümünüze ve yükleme konumunuza göre değiştirin.

1. İlk **dizin** alanında, komut isteminin başlatılacacağı dizini belirtin. Alanın yanındaki oku seçerek **Proje Dizini** gibi bir değer seçin.

1. **Tamam** düğmesini seçin.

   ![Dış Araçlar, doldurulan alan değerleriyle iletişim ilerler.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Yeni menü öğesi eklenir ve Araçlar menüsünden komut istemine erişebilirsiniz.

   ![Visual Studio'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Araçları](index.md)
- [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
- [Komut satırından Microsoft C++ araç kümesini kullanma](/cpp/build/building-on-the-command-line)
