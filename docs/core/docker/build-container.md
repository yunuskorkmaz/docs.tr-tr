---
title: Docker öğreticisiyle bir uygulamayı konteynerleştirin
description: Bu eğitimde, Docker ile bir .NET Core uygulamasını nasıl kaplaştırabileceğinizi öğreneceksiniz.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157836"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: Containerize bir .NET Core uygulaması

Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsünü nasıl oluşturabileceğinizi öğretir. Görüntü, yerel geliştirme ortamınız, özel bulutunuz veya genel bulutunuz için kapsayıcılar oluşturmak için kullanılabilir.

Şunları öğreneceksiniz:

> [!div class="checklist"]
>
> - Basit bir .NET Core uygulaması oluşturma ve yayımlama
> - .NET Core için Dockerfile oluşturma ve yapılandırma
> - Docker görüntüsü oluşturma
> - Docker kapsayıcısı oluşturma ve çalıştırma

Docker kapsayıcısını anlayacak ve .NET Core uygulaması için görevleri dağıtacaksınız. *Docker platformu,* *docker görüntüleri*olarak uygulamaları hızlı bir şekilde oluşturmak ve paketlemek için *Docker motorını* kullanır. Bu görüntüler, katmanlı bir kapsayıcıda dağıtılmak ve çalıştırılmak üzere *Dockerfile* biçiminde yazılır.

> [!TIP]
> Varolan bir ASP.NET Core uygulamasıyla çalışıyorsanız, [ASP.NET Core uygulama öğreticisini nasıl kaplaştırabileceğinizi öğrenin'e](/aspnet/core/host-and-deploy/docker/building-net-docker-images) bakın.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki ön koşulları yükleyin:

- [.NET Çekirdek 3.1 SDK](https://dotnet.microsoft.com/download)\
.NET Core yüklüyseniz, hangi `dotnet --info` SDK'yı kullandığınızı belirlemek için komutu kullanın.

- [Docker Topluluk Sürümü](https://www.docker.com/products/docker-desktop)

- *Dockerfile* ve .NET Core örnek uygulaması için geçici bir çalışma klasörü. Bu öğreticide, *docker-working* adı çalışma klasörü olarak kullanılır.

## <a name="create-net-core-app"></a>.NET Core uygulaması oluşturma

Docker konteynerinin çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır. Terminalinizi açın, çalışma klasörü oluşturun, henüz yapmadıysanız ve girin. Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console -o app -n myapp
```

Klasör ağacınız aşağıdaki gibi görünecektir:

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

`dotnet new` Komut, *uygulama* adında yeni bir klasör oluşturur ve bir "Hello World" uygulaması oluşturur. *Uygulama* klasörünü girin ve `dotnet run`komutu çalıştırın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Hello World!
```

Varsayılan şablon, terminale yazdırılan ve sonra çıkan bir uygulama oluşturur. Bu öğretici için, süresiz döngüler bir uygulama kullanırsınız. *Program.cs* dosyasını metin düzenleyicisinde açın. Şu anda aşağıdaki kod gibi görünmelidir:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Dosyayı, her saniye sayıları sayan aşağıdaki kodla değiştirin:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Dosyayı kaydedin ve `dotnet run`programı tekrar . Bu uygulamanın süresiz olarak çalıştığını unutmayın. Durdurmak için <kbd>CTRL</kbd>+<kbd>C'yi</kbd> iptal et komutunu kullanın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Komut satırındaki bir numarayı uygulamaya geçirirseniz, yalnızca bu tutara kadar sayılır ve sonra çıkar. `dotnet run -- 5` Beşe kadar saymayı dene.

> [!NOTE]
> Sonra `--` gelen parametreler komuta `dotnet run` geçirilmeyecek ve bunun yerine uygulamanıza geçirilir.

## <a name="publish-net-core-app"></a>.NET Core uygulamasını yayınla

.NET Core uygulamanızı Docker resmine eklemeden önce yayınlayın. Kapsayıcının başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırdığından emin olmak istersiniz.

Çalışma klasöründen, örnek kaynak koduyla *uygulama* klasörüne girin ve aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet publish -c Release
```

Bu komut, uygulamanızı *yayımlama* klasörüne derler. Çalışma klasöründen *yayımlama* klasörüne giden yol,`.\app\bin\Release\netcoreapp3.1\publish\`

*Uygulama* klasöründen, *myapp.dll* dosyasının oluşturulduğunu doğrulamak için yayımlama klasörünün dizin listesini alın.

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

Linux veya macOS kullanıyorsanız, bir `ls` dizin listesi almak ve *myapp.dll* dosyasının oluşturulduğunu doğrulamak için komutu kullanın.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Dockerfile'ı oluşturma

*Dockerfile* dosyası `docker build` bir kapsayıcı görüntüsü oluşturmak için komut tarafından kullanılır. Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.

Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörüne bir dizin gidin. Çalışma klasörünüzde *Dockerfile* adında bir dosya oluşturun ve bir metin düzenleyicisinde açın. Kapsayıcıhale edeceğiniz uygulamanın türüne bağlı olarak, ASP.NET Çekirdek çalışma zamanını veya .NET Core çalışma zamanını seçersiniz. Şüpheye düştüğünüzde, .NET Core çalışma süresini içeren ASP.NET Core çalışma saatini seçin. Bu öğretici, ASP.NET Core çalışma zamanı görüntüsünü kullanır, ancak önceki bölümlerde oluşturulan uygulama bir .NET Core uygulamasıdır.

- ASP.NET Core çalışma zamanı

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- .NET Çekirdek çalışma süresi

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

Komut, Docker'a `FROM` belirtilen depodan **3.1** etiketli görüntüyü aşağı çekmesini söyler. SDK'nız tarafından hedeflenen çalışma zamanı sürümüyle eşleşen çalışma zamanı sürümünü çektiğinizden emin olun. Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3.1 SDK kullanılır ve *Dockerfile'da* atıfta bulunulan temel resim **3.1**ile etiketlenir.

*Dockerfile* dosyasını kaydedin. Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir. Makalede yer kazanmak için daha derin düzeydosya ve klasörlerden bazıları kesildi:

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

Terminalinizden aşağıdaki komutu çalıştırın:

```console
docker build -t myimage -f Dockerfile .
```

Docker, *Dockerdosyasındaki*her satırı işleyecek. Komut, `.` `docker build` Docker'a geçerli klasörü kullanarak *Dockerfile'ı*bulmasını söyler. Bu komut görüntüyü oluşturur ve bu görüntüye işaret eden **myimage** adlı yerel bir depo oluşturur. Bu komut bittikten `docker images` sonra, yüklü görüntülerin listesini görmek için çalıştırın:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

İki görüntünün aynı **GÖRÜNTÜ Kimliği** değerini paylaştığına dikkat edin. *Dockerdosyasındaki* tek komut yeni görüntüyü varolan bir görüntüye dayandırmak olduğundan, değer her iki görüntü arasında da aynıdır. *Dockerfile'a*iki komut ekleyelim. Her komut, **myimage** depo giriş noktalarının görüntüye işaret ettiğini gösteren son komutla yeni bir görüntü katmanı oluşturur.

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Komut, Docker'a `COPY` bilgisayarınızda belirtilen klasörü kapsayıcıdaki bir klasöre kopyalamasını söyler. Bu örnekte, *yayımlama* klasörü kapsayıcıdaki *uygulama* adlı bir klasöre kopyalanır.

Bir sonraki `ENTRYPOINT`komut, Docker'a kapsayıcıyı çalıştırılabilir olarak çalışacak şekilde yapılandırmasını söyler. Kapsayıcı `ENTRYPOINT` başladığında, komut çalışır. Bu komut sona erdiğinde, kapsayıcı otomatik olarak durur.

Terminalinizden çalıştırın `docker build -t myimage -f Dockerfile .` ve komut bittiğinde `docker images`çalıştırın.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

*Dockerfile'daki* her komut bir katman oluşturdu ve bir **IMAGE ID**oluşturdu. Son **IMAGE ID** (sizinki farklı olacak) **ddcc6646461b** ve sonraki bu görüntüye dayalı bir kapsayıcı oluşturacaksınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Artık uygulamanızı içeren bir resminiz olduğuna göre, bir kapsayıcı oluşturabilirsiniz. Bir kapsayıcıyı iki şekilde oluşturabilirsiniz. İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

Yukarıdaki `docker create` **komut, myimage** görüntüsünü temel alan bir kapsayıcı oluşturur. Bu komutun çıktısı, oluşturulan **kapsayıcının KONTEYNER Kimliğini** (sizinki farklı olacaktır) gösterir. *Tüm* kapsayıcıların listesini görmek için `docker ps -a` aşağıdaki komutu kullanın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Kapsayıcıyı yönetme

Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz rasgele bir ad atanır. Örneğin, otomatik olarak oluşturulan kapsayıcı **gallant_lehmann** (sizinki farklı olacak) adını seçer ve bu ad kapsayıcıyı başlatmak için kullanılabilir. `docker create --name` Parametreyi kullanarak otomatik adı belirli bir adla geçersiz kılarsınız.

Aşağıdaki örnek, `docker start` kapsayıcıyı başlatmak için komutu `docker ps` kullanır ve ardından yalnızca çalışan kapsayıcıları göstermek için komutu kullanır:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur. Aşağıdaki örnek, `docker stop` kapsayıcıyı durdurmak için komutu `docker ps` kullanır ve sonra hiçbir kapsayıcının çalışmadığını göstermek için komutu kullanır:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

Bir kapsayıcı çalışmaya n ardından, çıktıyı görmek için ona bağlanabilirsiniz. Kapsayıcıyı `docker start` `docker attach` başlatmak ve çıkış akışına göz atmak için ve komutları kullanın. Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu çalışan kapsayıcıdan ayırmak için kullanılır. Bu tuş vuruşu aslında kapsayıcıdaki işlemi sonlayabilir ve bu da kapsayıcıyı durdurur. `--sig-proxy=false` <kbd>Parametre, CTRL + C'nin</kbd> kapsayıcıdaki işlemi durdurmamasını sağlar.

Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saydığını doğrulamak için yeniden takın.

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Kapsayıcı silme

Bu makalenin amaçları için sadece hiçbir şey yapmadan etrafında asılı konteyner istemiyorum. Daha önce oluşturduğunuz kapsayıcıyı silin. Kapsayıcı çalışıyorsa, durdurun.

```console
> docker stop gallant_lehmann
```

Aşağıdaki örnekte tüm kapsayıcılar listelenebedilir. Daha sonra `docker rm` kapsayıcıyı silmek için komutu kullanır ve ardından çalışan kapsayıcılar için ikinci kez denetler.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Tek çalışma

Docker, `docker run` kapsayıcıyı tek bir komut olarak oluşturma ve çalıştırma komutunu sağlar. Bu komut, çalıştırma `docker create` ve sonra `docker start`gereksinimi ortadan kaldırır. Kapsayıcı durduğunda kapsayıcıyı otomatik olarak silmek için bu komutu da ayarlayabilirsiniz. Örneğin, iki `docker run -it --rm` şey yapmak için kullanın, ilk olarak, kapsayıcıya bağlanmak için geçerli terminali otomatik olarak kullanın ve sonra kapsayıcı bittiğinde, kaldırın:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

, `docker run -it` <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, sırayla kapsayıcı durur. `--rm` Parametre sağlandığından, işlem durdurulduğunda kapsayıcı otomatik olarak silinir. Var olmadığını doğrulayın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>ENTRYPOINT'i değiştirme

Komut `docker run` ayrıca `ENTRYPOINT` *Dockerfile'deki* komutu değiştirmenize ve başka bir şey çalıştırmanıza olanak tanır, ancak yalnızca bu kapsayıcı için. Örneğin, çalıştırmak `bash` için aşağıdaki komutu kullanın veya `cmd.exe`. Komutu gerektiği gibi edin.

#### <a name="windows"></a>Windows

Bu örnekte, `ENTRYPOINT` '' olarak `cmd.exe`değiştirilir. <kbd>CTRL</kbd>+<kbd>C</kbd> işlemi sona erdirmek ve kapsayıcı durdurmak için basılır.

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>Linux

Bu örnekte, `ENTRYPOINT` '' olarak `bash`değiştirilir. İşlemi `quit` sona erdiren ve kapsayıcıyı durduran komut çalıştırılır.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Temel komutlar

Docker konteyner ve görüntüleri ile ne yapmak istediğinizi kapsayan birçok farklı komutları vardır. Bu Docker komutları, kapsayıcılarınızı yönetmek için gereklidir:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker çalıştırmak](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker durağı](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [docker görüntü](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğretici sırasında, kapsayıcılar ve görüntüler oluşturdu. İstersenizin, bu kaynakları silin. Aşağıdaki komutları kullanarak

01. Tüm kapsayıcıları listele

    ```console
    > docker ps -a
    ```

02. Çalışan kapsayıcıları durdurun. Kapsayıcıya `CONTAINER_NAME` otomatik olarak atanan adı temsil eder.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Kapsayıcıyı silme

    ```console
    > docker rm CONTAINER_NAME
    ```

Ardından, makinenizde artık istemediğiniz görüntüleri silin. *Dockerfile'Niz* tarafından oluşturulan görüntüyü silin ve ardından *Dockerfile'ın* temel inde olduğu .NET Core görüntüsünü silin. **IMAGE ID** veya **REPOSITORY:TAG** biçimlendirilmiş dizesini kullanabilirsiniz.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Yüklü `docker images` görüntülerin listesini görmek için komutu kullanın.

> [!NOTE]
> Resim dosyaları büyük olabilir. Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız. Genellikle, bu çalışma süresine bağlı olarak başka görüntüler oluşturmayı planlıyorsanız, temel görüntüleri çalışma zamanı yüklü olarak tutarsınız.

## <a name="next-steps"></a>Sonraki adımlar

- [ASP.NET Core uygulamasını nasıl kaplaştırılamayı öğrenin.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Core Microservice Tutorial ASP.NET deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Kapsayıcıları destekleyen Azure hizmetlerini inceleyin.](https://azure.microsoft.com/overview/containers/)
- [Dockerfile komutları hakkında bilgi edinin.](https://docs.docker.com/engine/reference/builder/)
- [Visual Studio için Konteyner Araçlarını Keşfedin](/visualstudio/containers/overview)
