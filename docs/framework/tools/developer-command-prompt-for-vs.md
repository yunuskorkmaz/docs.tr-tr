---
title: Visual Studio için Geliştirici Komut İstemi
description: .NET araçlarını daha kolay kullanmanıza imkan tanıyan Visual Studio için Geliştirici Komut İstemi kullanmayı öğrenin. Belirli ortam değişkenlerini otomatik olarak ayarlar.
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
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167175"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için Geliştirici Komut İstemi

Visual Studio için Geliştirici Komut İstemi, .NET Framework araçları daha kolay kullanmanıza olanak sağlar. Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi. Geliştirici Komut İstemi açtıktan sonra, veya gibi [.NET Framework araçlara](index.md) yönelik komutları girebilirsiniz `ildasm` `clrver` .

## <a name="prerequisites"></a>Ön koşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Makinenizde komut istemi araması yapın

Visual Studio sürümüne ve yüklediğiniz ek SDK ve iş yüklerine bağlı olarak birden çok komut istemi olabilir. Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-files-on-your-machine) deneyebilir veya [komut Istemi 'Ni Visual Studio 'nun içinden başlatabilirsiniz](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. **Start** ![ Klavyede Windows logo tuşunu Başlat ' ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) ve **V**harfine kaydırın.

1. **Visual Studio 2019** klasörünü genişletin.

1. VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.

   Alternatif olarak, görev çubuğundaki arama kutusuna komut isteminin adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladıktan sonra istediğiniz sonucu seçebilirsiniz.

   ![Windows 10 ' da arama davranışını gösteren animasyonlu GIF](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Klavyede Windows logosu tuşu Windows logosu tuşuna basarak **Başlangıç** ekranına gidin ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

1. **Başlat** ekranında, CTRL tuşuna basarak **Ctrl** + **Tab** **uygulamalar** listesini açın ve ardından **V**tuşuna basın. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste görüntüler.

1. VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.

### <a name="windows-7"></a>Windows 7

1. **Başlat** ' ı ve ardından **tüm programlar**' ı seçin.

1. VS 2019 için **Visual Studio 2019**  >  **Visual Studio Araçları**  >  **Geliştirici komut istemi**veya kullanmak istediğiniz komut istemi ' ni seçin.

   ![Komut istemi vurgulanmış olarak Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows7-menu.png)

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-files-on-your-machine"></a>Makinenizde dosyaları el ile bulun

Genellikle, yüklediğiniz komut istemlerinin kısayolları, *% ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları*gibi Visual Studio Için **Başlat menüsü** klasörüne yerleştirilir. Ancak, bazı nedenlerle komut istemi araması beklenen sonuçları oluşturmazsa, bu kısayolu makinenizde el ile bulmayı deneyebilirsiniz. *VsDevCmd.bat*gibi komut istemi dosyasının adını aramayı deneyin veya *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüz, sürüm ve yükleme konumunuza göre yol değişiklikleri) gibi Araçlar klasörüne gidin.

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Komut istemi 'ni Visual Studio 'Nun içinden başlatın

Daha kolay erişim için, Visual Studio 'daki Araçlar menüsüne Geliştirici Komut İstemi veya başka bir komut istemi ekleyebilirsiniz. Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin. Adımlar şunlardır:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.

1. Menü çubuğunda **Araçlar**  >  **dış araçlar**' ı seçin.

1. **Dış araçlar** Iletişim kutusunda **Ekle** düğmesini seçin. Yeni bir giriş görüntülenir.

1. Yeni menü öğesi için gibi bir **başlık** girin `Command Prompt` .

1. **Komut** alanında, başlatmak istediğiniz dosyayı (veya gibi) belirtin `%comspec%` `C:\Windows\System32\cmd.exe` .

1. **Bağımsız değişkenler** alanında, kullanmak istediğiniz belirli komut isteminin nerede bulunacağını belirtin, örneğin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` . Bu komut, Visual Studio 2019 topluluğuyla yüklenmiş Geliştirici Komut İstemi başlatır. Bu değeri, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değiştirin.

1. **İlk dizin** alanında, komut istemi 'nin başlayacağı dizini belirtin. Alanın yanındaki oku seçerek **proje dizini** gibi bir değer seçin.

1. **Tamam** düğmesini seçin.

   ![Alan değerleri doldurulmuş Dış Araçlar iletişim kutusu.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Yeni menü öğesi eklenir ve komut istemine Araçlar menüsünden erişebilirsiniz.

   ![Visual Studio 'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Araçları](index.md)
- [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
- [Komut satırından Microsoft C++ araç takımını kullanın](/cpp/build/building-on-the-command-line)
