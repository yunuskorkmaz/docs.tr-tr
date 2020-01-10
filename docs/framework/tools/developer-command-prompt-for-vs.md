---
title: Visual Studio için Geliştirici Komut İstemi
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715827"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için Geliştirici Komut İstemi

Visual Studio için Geliştirici Komut İstemi, .NET Framework araçları daha kolay kullanmanıza olanak sağlar. Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi. Geliştirici Komut İstemi açtıktan sonra, `ildasm` veya `clrver`gibi [.NET Framework araçlara](index.md) yönelik komutları girebilirsiniz.

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Makinenizde komut istemi araması yapın

Visual Studio sürümüne ve yüklediğiniz ek SDK ve iş yüklerine bağlı olarak birden çok komut istemi olabilir. Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-files-on-your-machine) deneyebilir veya [komut Istemi 'Ni Visual Studio 'nun içinden başlatabilirsiniz](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Klavyede ![Windows logo tuşunu **Başlat** ' ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve **V**harfine kaydırın.

1. **Visual Studio 2019** klasörünü genişletin.

1. VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.

   Alternatif olarak, görev çubuğundaki arama kutusuna komut isteminin adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladıktan sonra istediğiniz sonucu seçebilirsiniz.

   ![Windows 10 ' da arama davranışını gösteren animasyonlu GIF](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Klavyede Windows logosu tuşu ![Windows logosu tuşuna basarak **Başlangıç** ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

1. **Başlat** ekranında, **CTRL**+**sekmesine** basarak **uygulamalar** listesini açın ve ardından **V**' ye basın. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste görüntüler.

1. VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.

### <a name="windows-7"></a>Windows 7

1. **Başlat** ' ı ve ardından **tüm programlar**' ı seçin.

1. **VS 2019 için** > **Visual Studio Araçları** > Geliştirici komut istemi ya da kullanmak istediğiniz komut istemi ' ni **2019** seçin.

   ![Komut istemi vurgulanmış olarak Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-files-on-your-machine"></a>Makinenizde dosyaları el ile bulun

Genellikle, yüklediğiniz komut istemlerinin kısayolları, *% ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları*gibi Visual Studio Için **Başlat menüsü** klasörüne yerleştirilir. Ancak, bazı nedenlerle komut istemi araması beklenen sonuçları oluşturmazsa, bu kısayolu makinenizde el ile bulmayı deneyebilirsiniz. Komut istemi dosyasının adını ( *Vsdevcmd. bat*gibi) aramayı deneyin veya *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüz, sürüm ve yükleme konumunuza göre yol değişiklikleri) gibi Araçlar klasörüne gidin.

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Komut istemi 'ni Visual Studio 'Nun içinden başlatın

Daha kolay erişim için, Visual Studio 'daki Araçlar menüsüne Geliştirici Komut İstemi veya başka bir komut istemi ekleyebilirsiniz. Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin. Adımlar aşağıdaki gibidir:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.

1. Menü çubuğunda **araçlar** > **dış araçlar**' ı seçin.

1. **Dış araçlar** Iletişim kutusunda **Ekle** düğmesini seçin. Yeni bir giriş görüntülenir.

1. Yeni menü öğesi için `Command Prompt`gibi bir **başlık** girin.

1. **Komut** alanında, başlatmak istediğiniz dosyayı (`%comspec%` veya `C:\Windows\System32\cmd.exe`gibi) belirtin.

1. **Bağımsız değişkenler** alanında, kullanmak istediğiniz belirli komut isteminin nerede bulunacağını belirtin, örneğin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`. Bu komut, Visual Studio 2019 topluluğuyla yüklenmiş Geliştirici Komut İstemi başlatır. Bu değeri, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değiştirin.

1. **İlk dizin** alanında, komut istemi 'nin başlayacağı dizini belirtin. Alanın yanındaki oku seçerek **proje dizini** gibi bir değer seçin.

1. Seçin **Tamam** düğmesi.

   ![Alan değerleri doldurulmuş Dış Araçlar iletişim kutusu.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Yeni menü öğesi eklenir ve komut istemine Araçlar menüsünden erişebilirsiniz.

   ![Visual Studio 'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework araçları](index.md)
- [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
- [Komut satırından Microsoft C++ araç takımını kullanma](/cpp/build/building-on-the-command-line)
