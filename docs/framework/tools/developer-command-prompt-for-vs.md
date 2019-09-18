---
title: Visual Studio için Geliştirici Komut İstemi
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
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044735"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için Geliştirici Komut İstemi

Visual Studio için Geliştirici Komut İstemi, .NET Framework araçları daha kolay kullanmanıza olanak sağlar. Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi.

> [!div class="button"]
> [Visual Studio 'Yu indirin](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Makinenizde komut istemi araması yapın

Visual Studio sürümüne ve yüklediğiniz ek SDK 'lara bağlı olarak birden çok komut istemi olabilir. Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar. (Çoğu araç için 32-bit ve 64 bit sürümleri aynıdır; ancak, birkaç araç, 32-bit ve 64 bit ortamlara özgü değişiklikler yapar.) Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-files-on-your-machine) deneyebilir veya [komut satırını Visual Studio 'nun içinden çalıştırabilirsiniz](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Windows 10 ' da

1. Görev çubuğundaki arama kutusuna, veya `dev` `developer command prompt`gibi aracın adını yazmaya başlayın. Bu, arama örüntüsiyle eşleşen yüklü uygulamaların bir listesini getirir. Farklı bir komut istemi arıyorsanız, gibi farklı bir arama terimi `prompt`girmeyi deneyin.

2. **Visual Studio için geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.

### <a name="in-windows-81"></a>Windows 8.1

1. Klavyede Windows logosu tuşu ![Windows logosu tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

2. **Başlat** ekranında, **CTRL**+tuşuna basarak **uygulamalar** listesini açın ve ardından yazın `V`. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste getirir.

3. **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.

### <a name="in-windows-8"></a>Windows 8 ' de

1. Klavyede Windows logosu tuşu ![Windows logosu tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) Örneğin, klavyenizde.

2. **Başlat** ekranında klavyede Windows logosu tuşu ![Windows logosu tuşuna basın.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) `+ Z`.

3. Ekranın alt kısmındaki **Uygulamalar görünümü** simgesini seçin ve ardından girin `V`. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste getirir.

4. **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.

### <a name="in-windows-7"></a>Windows 7 ' de

1. **Başlat**' ı seçin, **tüm programlar**' ı genişletin ve **Microsoft Visual Studio**' ı genişletin.

2. Yüklediğiniz Visual Studio sürümüne bağlı olarak **Visual Studio Araçları**, **Visual Studio komut istemi**veya kullanmak istediğiniz komut istemi ' ni seçin.

[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ARM, x86 veya x64 mimarileri için ek komut istemleri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.

## <a name="manually-locate-the-files-on-your-machine"></a>Makinenizde dosyaları el ile bulun

Genellikle, yüklediğiniz komut istemlerinin kısayolları, C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Araçları gibi Visual Studio için **Başlat menüsü** klasörüne yerleştirilir. Ancak, bazı nedenlerle komut istemi araması beklenen sonuçları getirmiyorsa, bu kısayolu makinenizde el ile bulmayı deneyebilirsiniz. Örneğin, *Vsdevcmd. bat*gibi komut istemi dosyasının adını aramayı deneyin veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools gibi Araçlar klasörüne gidin (Visual Studio sürümünüz sürümüne göre yol değişiklikleri) ve yükleme konumu).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Komut istemi 'ni Visual Studio 'Nun içinden çalıştırma

Daha kolay erişim için Visual Studio Geliştirici Komut İstemi veya başka bir komut istemi, Visual Studio 'daki **Araçlar** menüsüne eklenebilir. Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin. Adımlar aşağıdaki gibidir:

1. Visual Studio'yu açın.

2. **Araçlar** menüsünü ve ardından **dış araçlar**' ı seçin.

3. **Dış araçlar** Iletişim kutusunda **Ekle** düğmesini seçin. Yeni bir giriş görüntülenir.

4. Yeni menü öğesi için gibi `Command Prompt`bir başlık girin.

5. **Komut** alanında, başlatmak `%comspec%` istediğiniz dosyayı (veya `C:\Windows\System32\cmd.exe`gibi) belirtin.

6. **Bağımsız değişkenler** alanında, gibi kullanmak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` istediğiniz belirli komut isteminin nerede bulunacağını belirtin (Bu komut, Visual Studio 2017 Enterprise ile yüklenen Geliştirici komut istemi başlatır). Bu değeri, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değiştirin.

7. **İlk dizin** alanı Için **proje dizini**gibi bir değer seçin.

8. Seçin **Tamam** düğmesi.

   Yeni menü öğesi eklenir ve komut istemine **Araçlar** menüsünden erişebilirsiniz.

   ![Visual Studio 'da komut istemi menü öğesi](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
