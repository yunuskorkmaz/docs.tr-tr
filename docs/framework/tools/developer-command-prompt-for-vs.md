---
title: Visual Studio için geliştirici komut istemi
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc88106a54a00b4b12e5043da7961791a98102c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344370"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için geliştirici komut istemi

Visual Studio için geliştirici komut istemi, .NET Framework araçlarını kolayca kullanmanıza olanak sağlar. Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi olur.

> [!div class="button"]
> [Visual Studio'yu indirin](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Komut istemi makinenizde arayın

Visual Studio ve ek Sdk'lara yüklediğiniz sürümüne bağlı olarak birden çok komut istemi olabilir. Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar. (Çoğu araç 32-bit ve 64-bit sürümleri aynıdır; ancak, birkaç araç 32-bit ve 64 bit ortamlara özel değişiklikler.) Aşağıdaki adımlar işe yaramazsa, deneyebileceğiniz [makinenizde dosyaları el ile konumlandırmak](#manually-locate-the-files-on-your-machine) veya [komut isteminden çalıştırın Visual Studio içinde](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Windows 10

1. Görev çubuğundaki arama kutusuna gibi aracının adını yazarak Başlat `dev` veya `developer command prompt`. Bu, arama deseniyle eşleşen yüklü uygulamalar listesini getirir. Gibi farklı bir arama terimi girmek için farklı bir komut istemi arıyorsanız deneyin `prompt`.

2. Seçin **Visual Studio için geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-81"></a>Windows 8.1 içinde

1. Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.

2. Üzerinde **Başlat** tuşuna basın, ekran **Ctrl**+**sekmesini** açmak için **uygulamaları** listelemek ve enter `V`. Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.

3. Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-8"></a>Windows 8'de

1. Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.

2. Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Seçin **uygulamaları görüntüle** ekranın altındaki simgesini ve ardından girin `V`. Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.

4. Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-7"></a>Windows 7 '

1. Seçin **Başlat**, genişletme **tüm programlar**ve ardından **Microsoft Visual Studio**.

2. Yüklemiş Visual Studio sürümüne bağlı olarak, seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut istemi.

Diğer SDK'lar gibi varsa [Windows 10 SDK'sı](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümleri](https://developer.microsoft.com/windows/downloads/sdk-archive), ek komut istemleri için ARM, x 86 veya x64 mimariler görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-files-on-your-machine"></a>Makinenizde dosyaları el ile bulun

Genellikle, yüklediğiniz komut istemlerine kısayolları yerleştirilir **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları gibi Visual Studio için klasör. Ancak bazı nedenlerden dolayı için komut istemi arama beklenen sonuçları getirmek değil, kısayol makinenizde el ile bulmak deneyebilirsiniz. Komut istemi dosyasının adı için gibi aramayı deneyin *VsDevCmd.bat*, veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (yolu değişiklikleri Görselinizi göre gibi Araçlar klasörüne gidin Studio sürümü, sürümü ve yükleme konumu).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Komut İstemi'nden çalıştırmak Visual Studio içinde

Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi başka bir komut istemi, ekleyebilirsiniz **Araçları** Visual Studio'daki menü. Aracı kullanabilmek için dış araçları listesine ekleyin. Adımlar aşağıdaki gibidir:

1. Visual Studio'yu açın.

2. Seçin **Araçları** menüsünü seçip **dış Araçları**.

3. Üzerinde **dış Araçlar** iletişim kutusunda **Ekle** düğmesi. Yeni bir giriş belirir.

4. Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.

5. İçinde **komut** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe`.

6. İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemini nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Bu komut, Visual Studio 2017 Enterprise ile yüklü Geliştirici komut istemi başlatılır). Visual Studio sürümü, sürümü ve yükleme konumuna göre bu değeri değiştirin.

7. İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizini**.

8. Seçin **Tamam** düğmesi.

   Yeni menü öğesi eklendi ve Komut İstemi'nden erişebilir **Araçları** menüsü.

   ![Visual Studio komut istemi menü öğesi](media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](../../../docs/framework/tools/index.md)
- [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
