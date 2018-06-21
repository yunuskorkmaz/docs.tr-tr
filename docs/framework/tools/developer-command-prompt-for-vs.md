---
title: Visual Studio için geliştirici komut istemi
ms.date: 06/18/2018
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
ms.openlocfilehash: 7e91822f172de8700b04847541c4b80010a22b53
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270493"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için geliştirici komut istemi

Visual Studio için geliştirici komut istemi, .NET Framework araçları kolayca kullanmanıza olanak ortam değişkenlerini otomatik olarak ayarlar. Geliştirici komut istemi tam veya topluluk Visual Studio sürümleriyle yüklenir. Visual Studio Express sürümleri ile yüklü değil.

> [!div class="button"]
[Visual Studio indirme](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a>Komut istemi makinenizde arama

Visual Studio ve yüklemiş olduğunuz herhangi bir ek SDK sürümüne bağlı olarak birçok komut istemlerini görebilirsiniz. Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar. (Çoğu araçlarının 32-bit ve 64 bit sürümleri aynıdır; ancak, bazı araçları 32-bit ve 64-bit ortamlar için belirli değişiklik.) Aşağıdaki adımlar işe yaramazsa, deneyebilirsiniz [el ile makinenizde dosyaları bulma](#manually-locating-the-files-on-your-machine) veya [komutunu çalıştırarak Visual Studio içinde sor](#running-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Windows 10

1. Görev çubuğunda arama kutusuna, aracı adı gibi yazmaya başlayın `dev` veya `developer command prompt`. Bu, arama deseniyle eşleşen yüklü uygulamaların bir listesini getirir. Farklı bir komut isteminde arıyorsanız, farklı bir arama terimi gibi girmeyi deneyin `prompt`.

2. Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-81"></a>Windows 8.1

1. Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.

2. Üzerinde **Başlat** ekranında, basın `CTRL + TAB` açmak için **uygulamaları** listelemek ve enter `V`. Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.

3. Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-8"></a>Windows 8

1. Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.

2. Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Seçin **uygulamaları görüntülemek** ekranın alt kısmındaki simgesine tıklayın ve ardından girin `V`. Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.

4. Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).

### <a name="in-windows-7"></a>Windows 7

1. Seçin **Başlat**, genişletin **tüm programlar**, genişletin ve ardından **Microsoft Visual Studio**.

2. Visual Studio, yükledim sürümüne bağlı olarak seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut isteminde.

Yüklü aşağıdaki gibi diğer SDK varsa [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive) yüklüyse, ek komutu ister ARM için x 86 veya x64 mimarileri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locating-the-files-on-your-machine"></a>El ile makinenizde dosyaları bulma

Genellikle, yüklü olan komut istemleri kısayolları yerleştirilmiş **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları gibi Visual Studio için klasör. Ancak herhangi bir nedenle komut satırından arama beklenen sonuçları değil getirirseniz, el ile kısayol makinenizde bulun deneyebilirsiniz. Komut istemi dosya adını gibi arama yapmayı deneyin *VsDevCmd.bat*, veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (yolu göre değişiklikler, Visual gibi Araçlar klasörüne gidin Studio sürümü, sürümü ve yükleme konumu).

## <a name="running-command-prompt-from-inside-visual-studio"></a>Komutunu çalıştırarak Visual Studio içinde sor

Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi bir komut istemi Visual Studio, Araçlar menüsünden harici araçlar listesine ekleyerek ekleyebilirsiniz. Bu, nasıl gerçekleştirebilirsiniz.

1. Visual Studio'yu açın.

2. Seçin **Araçları** menü ve **Harici Araçlar**.

3. Üzerinde **Harici Araçlar** iletişim kutusunda, seçin **Ekle** düğmesi. Yeni bir giriş belirir.

4. Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.

5. İçinde **komutu** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe`.

6. İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemi nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Bu komutu ile Visual Studio 2017 Enterprise yüklü Geliştirici komut istemi başlatır). Visual Studio sürümü, sürümü ve yükleme konumuna göre bu değeri değiştirin.

7. İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizinine**.

8. Seçin **Tamam** düğmesi.

Bundan sonra yeni menü öğesi eklendi ve komut isteminden erişebilirsiniz **Araçları** menüsü.

## <a name="see-also"></a>Ayrıca bkz.

 [Araçlar](../../../docs/framework/tools/index.md)  
 [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)  
