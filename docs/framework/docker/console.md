---
title: Docker'da çalışan konsol uygulamaları
description: Mevcut bir .NET Framework konsol uygulamasını alıp Windows Docker kapsayıcısında çalıştırmayı öğrenin.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: da3c814e2ae3ae646072deaf7aa932272160ce49
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611503"
---
# <a name="running-console-applications-in-windows-containers"></a>Windows kapsayıcıları içinde çalışan konsol uygulamaları

Konsol uygulamaları, birçok farklı amaçla kullanılır; Basit bir durum için uzun süre çalışan görüntüsünün sorgulamasını işleme görevlerini. Herhangi bir durumda, başlatın ve bu uygulamaları ölçeklendirme olanağı karşılanmadığı sınırlamaları donanım satın almalar, başlangıç sürelerinde veya birden fazla örneği çalışıyor.

Docker ve Windows Server'ı kullanmak için konsol uygulamaları taşıma kapsayıcıları tanır bu uygulamaları etkinleştirme işlemi ve ardından kapatma düzgün bir şekilde gerçekleştirmek için temiz bir durumdan başlatmak için. Bu konuda, bir Windows konsol uygulamaya taşımak için gerekli olan adımları kapsayıcı tabanlı ve bir PowerShell Betiği kullanarak gösterilir.

Örnek konsol uygulaması, bu durumda bir soru bağımsız değişken alır ve rastgele bir yanıt döndürür basit bir örnektir. Bu sürebilir bir `customer_id` ve bunların vergileri işlemek veya ilişkin bir küçük resim oluşturma bir `image_url` bağımsız değişken.

Yanıt yanı sıra `Environment.MachineName` yerel olarak ve bir Windows kapsayıcı uygulaması çalıştıran arasındaki farkı göstermek için yanıta eklenir. Uygulamayı yerel olarak çalışırken, yerel makine adını döndürülmesi gerektiğini ve bir Windows kapsayıcısı içinde çalışırken kapsayıcı oturum kimliği döndürülür.

[Tam bir örnek](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) dotnet/samples deposuna github'da mevcuttur. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Uygulamanız bir kapsayıcıya taşıma çalışmaya başlamadan önce koşulları bazı Docker ile ilgili bilgi sahibi olmanız gerekir.

> [!NOTE]
> A *Docker görüntüsü* ortam için işletim sistemi (OS), sistem bileşenleri ve uygulamaları dahil olmak üzere, çalışan bir kapsayıcı tanımlar salt okunur bir şablondur.

Docker görüntüleri bir önemli özelliği, görüntüleri bir temel görüntüden oluşur. Her yeni görüntüyü küçük bir özellik kümesi için mevcut bir görüntü ekler.

> [!NOTE]
> A *Docker kapsayıcısı* görüntü, çalışan bir örneğidir.

Bir uygulama, çok sayıda kapsayıcı içinde aynı görüntü çalıştırarak ölçeklendirin.
Kavramsal olarak, bu birden çok konak aynı uygulamayı çalıştırmaya benzer.

Okuyarak Docker mimarisi hakkında daha fazla bilgi edinebilirsiniz [Docker'a genel bakış](https://docs.docker.com/engine/understanding-docker/) Docker sitesinde.

Konsol uygulamanızı taşımak birkaç adım bir konudur.

1. [Uygulamayı oluşturun](#building-the-application)
1. [Görüntü için bir Dockerfile'ı oluşturma](#creating-the-dockerfile)
1. [Derleme ve Docker kapsayıcısını çalıştırma işlemi](#creating-the-image)

## <a name="prerequisites"></a>Önkoşullar

Windows kapsayıcıları desteklenmektedir [Windows 10 Yıldönümü güncelleştirmesi](https://www.microsoft.com/en-us/software-download/windows10/) veya [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Windows Server 2016'yı kullanıyorsanız, Docker için Windows Yükleyici özelliği etkin değildir bu yana kapsayıcılar el ile etkinleştirmeniz gerekir. Tüm güncelleştirmeler için işletim sistemi çalıştıran ve ardından yönergeleri izleyin emin [kapsayıcı konak dağıtımı](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) kapsayıcıları ve Docker özellikleri yüklemek için makale.

Docker için Windows, sürüm 1.12 desteklemek için Beta 26 veya üzeri Windows kapsayıcıları olması gerekir. Varsayılan olarak, Docker, Linux tabanlı kapsayıcılar sağlar; Windows kapsayıcıları için Docker sistem tepsisindeki simgeye sağ tıklayarak geçin ve seçin **Windows kapsayıcılarına geç**. Docker değiştirme işlemi çalışır ve bir yeniden başlatma gerekebilir.

![Windows kapsayıcı menü seçeneğinin ekran görüntüsü.](./media/console/windows-container-option.png)

## <a name="building-the-application"></a>Uygulama oluşturma

Yükleyici, FTP veya dosya paylaşımı konsol uygulamaları genellikle dağıtılmış dağıtım. Bir kapsayıcıya dağıtılırken varlıkları derlenir ve Docker görüntüsü oluşturulduğunda kullanılabilecek bir konuma aşamalı gerekir.

Örnek uygulamayı şu şekildedir: [ConsoleRandomAnswerGenerator](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator)

İçinde *build.ps1*<sup>[[kaynak]](https://github.com/dotnet/samples/blob/master/framework/docker/ConsoleRandomAnswerGenerator/ConsoleRandomAnswerGenerator/build.ps1)</sup>, betikte [MSBuild](/visualstudio/msbuild/msbuild) varlıkları oluşturma görevini tamamlamak için bir uygulama derlemek için. Gerekli varlıkları sonlandırmak için MSBuild'e geçirilen birkaç parametre yok. Proje dosyası veya derlenecek çözüm, konum adı için çıktı ve son olarak yapılandırma (yayınlama veya hata ayıklama).

Çağrısında `Invoke-MSBuild` `OutputPath` ayarlanır **yayımlama** ve `Configuration` kümesine **yayın**.

```powershell
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Dockerfile'ı oluşturma
.NET Framework uygulamasına Konsolu için kullanılan temel görüntü `microsoft/windowsservercore`, üzerinde genel kullanıma açık [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/). Temel görüntü en az bir Windows Server 2016, .NET Framework 4.6.2 yüklenmesini içerir ve Windows kapsayıcıları için temel işletim sistemi görüntüsü görev yapar.

```Dockerfile
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```

Temel görüntüyü kullanarak Dockerfile ilk satırı atayan [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) yönergesi. Ardından, [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) dosyasında uygulama varlıklarından kopyalar **yayımlama** klasörünü kök klasöre kapsayıcı ve son; ayarı [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) Görüntü durumlarını söz konusu komut veya kapsayıcı başlatıldığında çalıştırılacak uygulama budur.

## <a name="creating-the-image"></a>Görüntü oluşturma

Docker görüntüsünü oluşturmak için aşağıdaki kodu eklenir *build.ps1* betiği. Betiği çalıştırdığınızda `console-random-answer-generator` görüntü MSBuild içinde tanımlanan gelen derlenmiş varlıklar kullanılarak oluşturulan [uygulama oluşturma](#building-the-application) bölümü.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Betik kullanarak çalıştırma `.\build.ps1` PowerShell komut isteminde.

Derleme tamamlandığında kullanarak `docker images` komutu bir komut satırı ya da PowerShell isteminden; görüntü oluşturulur ve çalıştırılmaya hazır olduğunu görürsünüz.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Kapsayıcı çalıştırma

Kapsayıcı Docker komutlarını kullanarak komut satırından başlayabilirsiniz.

```
docker run console-random-answer-generator "Are you a square container?"
```

Çıktı

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Çalıştırırsanız `docker ps -a` komutunu Powershell'den kapsayıcının hala olduğunu görebilirsiniz.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago
```

Durum sütununda "yaklaşık bir dakika önce", gösterir uygulama tam ve kapatılabilir. Komutu yüzlerce kez çalıştırırsanız yapması ile kapsayıcıları sol statik bir yüz olacaktır. Başlangıç senaryosunda, işlerini gerçekleştirmek için ideal işlemin tamamlandığını ve kapatma veya temizleme. O iş akışını gerçekleştirmek için ekleme `--rm` seçeneğini `docker run` komutu, kapsayıcı kaldırılır hemen sonra `Exited` sinyali aldı.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Bu seçenek ile çalıştırarak ve ardından çıktısına arayarak `docker ps -a` komut; dikkat kapsayıcı kimliği ( `Environment.MachineName`) listesinde değil.

### <a name="running-the-container-using-powershell"></a>PowerShell kullanarak kapsayıcı çalıştırma

Örnek proje dosyalarında olduğu da bir *run.ps1* bağımsız değişkenleri kabul eden uygulamayı çalıştırmak için PowerShell kullanma örneği verilmiştir.

Çalıştırmak için PowerShell'i açın ve aşağıdaki komutu kullanın:

```powershell
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Özet

Yalnızca bir Dockerfile ekleme ve uygulama yayımlama, .NET Framework konsol uygulamalarınızı kapsayıcılı hale getirme ve artık birden çok örneği, temiz bir başlangıç ve durdurma ve daha fazla Windows Server 2016 özellikleri, herhangi yapmadan çalıştıran avantajından faydalanın hiç uygulama koduna değiştirir.
