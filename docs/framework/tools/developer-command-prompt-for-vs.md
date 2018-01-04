---
title: "Visual Studio için geliştirici komut istemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bd7baec77e6e776f93a2a13156d66c1199f918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a>Visual Studio için geliştirici komut istemi
Visual Studio için geliştirici komut istemi, .NET Framework araçları kolayca kullanmanıza olanak ortam değişkenlerini otomatik olarak ayarlar. Geliştirici komut istemi tam veya topluluk Visual Studio sürümleriyle yüklenir. Visual Studio Express sürümleri ile yüklenmedi.  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a>Komut istemi makinenizde arama  
 Visual Studio ve yüklemiş olduğunuz herhangi bir ek SDK sürümüne bağlı olarak birden çok komut istemlerini görebilirsiniz. Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar. (Çoğu aracın 32 bit ve 64 bit sürümleri aynıdır; ancak, birkaç araç, 32 bit ve 64 bit ortamlara özel değişiklikler yapar.) Aşağıdaki adımlar işe yaramazsa, deneyebilirsiniz [el ile makinenizde dosyaları bulma](#alternative) veya [komutunu çalıştırarak Visual Studio içinde sor](#visualstudio).  
  
 **Windows 10**  
  
1.  Açık **Başlat** Windows logosu tuşuna basarak menüsünde ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.  
  
2.  Üzerinde **Başlat** menüsünde girin `dev`. Bu, arama deseniyle eşleşen yüklü uygulamaların bir listesini getirir. Farklı bir komut isteminde arıyorsanız, farklı bir arama terimi gibi girmeyi deneyin `prompt`.  
  
3.  Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).  
  
 **Windows 8.1**  
  
1.  Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.  
  
2.  Üzerinde **Başlat** ekranında, basın `CTRL + TAB` açmak için **uygulamaları** listelemek ve enter `V`. Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.  
  
3.  Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).  
  
 **Windows 8**  
  
1.  Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.  
  
2.  Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.  
  
3.  Seçin **uygulamaları görüntülemek** ekranın alt kısmındaki simgesine tıklayın ve ardından girin `V`. Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.  
  
4.  Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).  
  
 **Windows 7**  
  
1.  Seçin **Başlat**, genişletin **tüm programlar**, genişletin ve ardından **Microsoft Visual Studio**.  
  
2.  Yüklü olan Visual Studio sürümüne bağlı olarak seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut isteminde.  
  
 Varsa [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) veya [Windows Phone SDK'sı](https://dev.windowsphone.com/downloadsdk) yüklüyse, ek komutu ister ARM için x 86 veya x64 mimarileri görebilirsiniz. Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a>El ile makinenizde dosyaları bulma  
  Genellikle, yüklü olan komut istemleri kısayolları adresindeki yerleştirilecek **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio olduğu gibi Visual Studio için klasör Araçları.    Ancak herhangi bir nedenle komut satırından arama beklenen sonuçları elde etmek değil, el ile kullanmak için makinenizde kısayol bulun deneyebilirsiniz.   VsDevCmd.bat gibi bir komut istemi dosyasının adı için arama yapmayı deneyin veya C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools gibi Araçlar klasörüne gidin (Visual Studio sürümü ve yükleme konumuna göre yolu değiştirir).  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a>Komutunu çalıştırarak Visual Studio içinde sor  
 Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi bir komut istemi Visual Studio, Araçlar menüsünden harici araçlar listesine ekleyerek ekleyebilirsiniz. Bu, nasıl gerçekleştirebilirsiniz.  
  
1.  Visual Studio'yu açın.  
  
2.  Seçin **Araçları** menü ve **harici araçlar...** .  
  
3.  Üzerinde **Harici Araçlar** iletişim kutusunda, seçin **Ekle** düğmesi. Yeni bir giriş belirir  
  
4.  Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.  
  
5.  İçinde **komutu** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe` .  
  
6.  İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemi nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (Bu yüklenmiş Geliştirici komut istemi başlatacak [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]). Bu değer, Visual Studio sürümü ve yükleme konumuna göre değiştirilmesi gerekiyor.  
  
7.  İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizinine** .  
  
8.  Seçin **Tamam** düğmesi.  
  
 Bundan sonra yeni menü öğesi eklendi ve komut isteminden erişebilirsiniz **Araçları** menüsü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Dış Araçları Yönetme](/visualstudio/ide/managing-external-tools)
