---
title: "Docker çalışan konsol uygulamaları"
description: "Varolan bir .NET Framework konsol uygulaması almak ve bir Windows Docker kapsayıcısı çalıştırmak öğrenin."
author: spboyer
keywords: ".NET, kapsayıcı, konsol, uygulamaları"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 037d94452dd62c06fe6d8ac7aea1143f52b96d32
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="running-console-applications-in-windows-containers"></a>Windows kapsayıcılarında çalışan konsol uygulamaları

Konsol uygulamaları birçok amaçlar için kullanılır; Basit durum uzun süre çalışan belge görüntüsüne sorgulamasını görevleri işleniyor. Herhangi bir durumda, başlatılması ve bu uygulamaları ölçeklendirme olanağı karşılanmadığı donanım satın almalar, başlatma süreleri veya birden çok örneği çalıştıran kısıtlamalarla.

Docker ve Windows Server kullanmak için konsol uygulamaları taşıma kapsayıcıları sağlar işlem ve ardından kapatma düzgün bir şekilde gerçekleştirmek üzere bunları etkinleştirme temiz bir durumdan bu uygulamaları başlatmak için. Bu konuda, bir Windows konsol uygulaması taşımak için gerekli olan adımları kapsayıcı temel ve bunu bir PowerShell Betiği kullanılarak gösterir.

Örnek konsol uygulaması bağımsız değişken, bir soru bu durumda alır ve rastgele bir yanıt döndüren basit bir örnektir. Bu sürebilir bir `customer_id` ve bunların vergileri işlem veya için bir küçük resim oluşturma bir `image_url` bağımsız değişkeni.

Yanıt yanı sıra `Environment.MachineName` uygulama yerel olarak ve bir Windows kapsayıcıda çalışan arasındaki farkı göstermek için yanıta eklenir. Uygulamayı yerel olarak çalışırken, yerel makine adınızı döndürülmelidir ve bir Windows kapsayıcısında; çalıştırırken kapsayıcı oturum kimliği döndürülür.

[Tam örnek](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) github'da dotnet/docs Havuzda kullanılabilir. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bir kapsayıcı uygulamanıza taşıma çalışmaya başlamadan önce koşulları bazı Docker ile ilgili bilgi sahibi olmanız gerekir.

> A *Docker görüntü* ortam için işletim sistemi (OS), sistem bileşenleri ve uygulamaları dahil olmak üzere, çalışan bir kapsayıcı tanımlar salt okunur bir şablondur.

Görüntüleri temel bir görüntüden oluşan Docker görüntülerinin bir önemli özelliklerinden biridir. Her yeni görüntüyü küçük bir özellikler kümesi için varolan bir görüntü ekler. 

> A *Docker kapsayıcısı* bir görüntü, çalışan bir örneğidir. 

Aynı görüntüyü birçok kapsayıcılarında çalıştırarak uygulama ölçeklendirme.
Kavramsal olarak, bu aynı uygulamayı birden çok ana çalıştırmaya benzer.

Docker mimarisi hakkında daha fazla okuyarak bilgi [Docker genel bakış](https://docs.docker.com/engine/understanding-docker/) Docker sitesinde. 

Konsol uygulamanızın taşıma birkaç adım bir konudur.

1. [Uygulama oluşturma](#building-the-application)
1. [Görüntüsü için bir Dockerfile oluşturma](#creating-the-dockerfile)
1. [Derleme ve Docker kapsayıcısı çalıştırma işlemi](#creating-the-image)

## <a name="prerequisites"></a>Önkoşullar
Windows kapsayıcıları üzerinde desteklenir [Windows 10 Anniversary güncelleştirme](https://www.microsoft.com/en-us/software-download/windows10/) veya [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Windows Server 2016 kullanıyorsanız, Docker için Windows Installer özelliğini etkinleştirmemeniz beri kapsayıcıları el ile etkinleştirmeniz gerekir. Tüm güncelleştirmeler için işletim sistemi çalıştıran ve makalesindeki yönergeleri izleyin emin olun [kapsayıcı konak dağıtımı](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) kapsayıcıları ve Docker özellikleri yüklemek için makale.

Docker için Windows, sürüm 1.12 desteklemek için Beta 26 ya da daha yüksek Windows kapsayıcıları olması gerekir. Varsayılan olarak, Linux tabanlı kapsayıcıları Docker sağlar; geçiş Windows kapsayıcılara sistem tepsisindeki Docker simgesini sağ tıklayarak ve seçin **geçiş Windows kapsayıcılara**. Docker değiştirme işlemi çalışacak ve yeniden başlatma gerekli olabilir.

![Windows kapsayıcıları](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Uygulama oluşturma
Yükleyici, FTP veya dosya paylaşımı konsol uygulamaları genellikle dağıtılmış dağıtım. Bir kapsayıcıya dağıtırken varlıklar derlenir ve Docker görüntü oluşturulduğunda, kullanılabilir bir konuma hazırlanan gerekir.

İçinde *build.ps1*, komut dosyası kullanan [MSBuild](/visualstudio/msbuild/msbuild) varlıkları oluşturma görevini tamamlamak için uygulamayı derlemek için. Gerekli varlıklar sonlandırmaya MSBuild için geçirilen birkaç parametre vardır. Proje dosyası veya derlenecek çözüm, konum adı çıkış ve son olarak yapılandırma (sürüm ya da hata ayıklama).

Çağrısında `Invoke-MSBuild` `OutputPath` ayarlanır **yayımlama** ve `Configuration` kümesine **sürüm**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Dockerfile oluşturma
.NET Framework uygulama Konsolu için kullanılan temel görüntü `microsoft/windowsservercore`, genel kullanıma açık üzerinde [Docker hub'a](https://hub.docker.com/r/microsoft/windowsservercore/). Temel görüntü en az bir Windows Server 2016, .NET Framework 4.6.2 yüklemesini içerir ve Windows kapsayıcıları için temel işletim sistemi görüntüsü görev yapar.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
Temel görüntü kullanarak Dockerfile ilk satırı atar [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) yönergesi. İleri [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) dosyasında uygulama varlıklarından kopyalar **yayımlama** klasörü kök klasöre kapsayıcı ve son; ayarı [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) Görüntü durumlarını bu kapsayıcı başlatıldığında, çalıştırılacak komut veya uygulamadır. 

## <a name="creating-the-image"></a>Görüntü oluşturma
Docker görüntü oluşturmak için aşağıdaki kodu eklenen *build.ps1* komut dosyası. Komut dosyasını çalıştırdığınızda `console-random-answer-generator` görüntü tanımlanan MSBuild gelen derlenmiş varlıklar kullanılarak oluşturulan [uygulama oluşturma](#building-the-application) bölümü.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Komut dosyası kullanarak çalıştırmak `.\build.ps1` PowerShell komut isteminde.

Yapı tamamlandığında kullanarak `docker images` komutu bir komut satırından veya PowerShell komut isteminde; görüntü oluşturulan ve çalıştırılmaya hazır olduğunu görürsünüz.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Kapsayıcı çalıştırma
Kapsayıcı Docker komutları kullanarak komut satırından başlatabilirsiniz.

```
docker run console-random-answer-generator "Are you a square container?"
```

Çıktı

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Çalıştırırsanız `docker ps -a` komutunu Powershell'den, kapsayıcı hala var olduğundan görebilirsiniz.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

Durum sütununda "yaklaşık bir dakika önce", gösterir uygulama tam ve kapatılabilir. Komutu yüzlerce kez çalıştırırsanız kapsayıcıları sol statik yapması ile yüzlerce olacaktır. İşlerini yapmak için ideal işlemi başına senaryoda oldu ve kapatma veya temizleme. Bu iş akışı gerçekleştirmek için ekleme `--rm` için seçenek `docker run` komutu kapsayıcı kaldırmak hemen `Exited` sinyali aldı.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Bu seçenekle komutu çalıştırmak ve çıktısını arayan `docker ps -a` dikkat edin; komutu kapsayıcı kimliği ( `Environment.MachineName`) listesinde değil.

### <a name="running-the-container-using-powershell"></a>PowerShell kullanarak kapsayıcı çalıştırma
Örnek proje dosyalarında bulunmaktadır bir *run.ps1* bağımsız değişkenleri kabul uygulamayı çalıştırmak için PowerShell kullanma örneği verilmiştir.

Çalıştırmak için PowerShell'i açın ve aşağıdaki komutu kullanın:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Özet
Yalnızca bir Dockerfile ekleme ve uygulama yayımlama, .NET Framework'te konsol uygulamaları containerize ve artık birden çok örneği, temiz Başlat ve Durdur ve daha fazla Windows Server 2016 yetenekleri herhangi yapmadan çalıştıran avantajlarından yararlanmak uygulama kodu hiç değiştirir.
