---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157836"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: bir .NET Core uygulamasını Kapsayıize edin

Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretir. Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.

Şunları öğreneceksiniz:

> [!div class="checklist"]
>
> - Basit bir .NET Core uygulaması oluşturma ve yayımlama
> - .NET Core için Dockerfile oluşturma ve yapılandırma
> - Docker görüntüsü oluşturma
> - Docker kapsayıcısı oluşturma ve çalıştırma

Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız. *Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır. Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.

> [!TIP]
> Mevcut bir ASP.NET Core uygulamasıyla çalışıyorsanız, [bir ASP.NET Core uygulama öğreticisini nasıl kapsayıtabilecek hakkında bilgi edinin](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki önkoşulları yükler:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download)\
.NET Core yüklüyse, kullanmakta olduğunuz SDK 'yı öğrenmek için `dotnet --info` komutunu kullanın.

- [Docker Community sürümü](https://www.docker.com/products/docker-desktop)

- *Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü. Bu öğreticide, *Docker-Working* adı çalışma klasörü olarak kullanılır.

## <a name="create-net-core-app"></a>.NET Core uygulaması oluşturma

Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır. Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin. Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console -o app -n myapp
```

Klasör ağaclarınız şöyle görünür:

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

`dotnet new` komutu, *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" uygulaması oluşturur. *Uygulama* klasörünü girin ve `dotnet run`komutu çalıştırın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Hello World!
```

Varsayılan şablon, terminale yazdıran ve ardından çıkış yapan bir uygulama oluşturur. Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız. *Program.cs* dosyasını bir metin düzenleyicisinde açın. Şu anda şu kod gibi görünmelidir:

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

Dosyayı her saniye sayı sayan aşağıdaki kodla değiştirin:

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

Dosyayı kaydedin ve `dotnet run`programı yeniden test edin. Bu uygulamanın süresiz olarak çalıştığını unutmayın. Durdurmak için <kbd>CTRL</kbd>+, Cancel <kbd></kbd> komutunu kullanın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur. Beş ile saymak için `dotnet run -- 5` deneyin.

> [!NOTE]
> `--` sonraki parametreler `dotnet run` komutuna geçirilmez ve bunun yerine uygulamanıza geçirilir.

## <a name="publish-net-core-app"></a>.NET Core uygulaması Yayımla

.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın. Kapsayıcının, başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırmasını sağlamak istiyorsunuz.

Çalışma klasöründen, örnek kaynak kodu ile *uygulama* klasörünü girin ve şu komutu çalıştırın:

```dotnetcli
dotnet publish -c Release
```

Bu komut, uygulamanızı *Yayımla* klasörüne derler. Çalışma klasöründeki *Yayımla* klasörünün yolu `.\app\bin\Release\netcoreapp3.1\publish\` olmalıdır

*App* klasöründen, *MyApp. dll* dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.

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

Linux veya macOS kullanıyorsanız, dizin listesi almak için `ls` komutunu kullanın ve *MyApp. dll* dosyasının oluşturulduğunu doğrulayın.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Dockerfile oluşturma

*Dockerfile* dosyası `docker build` komutu tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır. Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.

Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörünün dizinine gidin. Çalışma klasörünüzde *Dockerfile* adlı bir dosya oluşturun ve dosyayı bir metin düzenleyicisinde açın. Kapsayıcılı olduğunuz uygulamanın türüne bağlı olarak, ASP.NET Core çalışma zamanını veya .NET Core çalışma zamanını seçersiniz. Şüpheli olduğunda, .NET Core çalışma zamanını içeren ASP.NET Core çalışma zamanını seçin. Bu öğretici ASP.NET Core çalışma zamanı görüntüsünü kullanır, ancak önceki bölümlerde oluşturulan uygulama bir .NET Core uygulamasıdır.

- ASP.NET Core çalışma zamanı

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- .NET core çalışma zamanı

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

`FROM` komutu, Docker 'ın belirtilen depodan etiketlenen **3,1** görüntüsünü çekmesini söyler. SDK 'nizin hedeflediği çalışma zamanıyla eşleşen çalışma zamanı sürümünü çekdiğinizden emin olun. Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3,1 SDK 'sını ve *Dockerfile* içinde başvurulan temel görüntüyü **3,1**ile etiketledi.

*Dockerfile* dosyasını kaydedin. Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir. Daha derin düzey dosya ve klasörlerin bazıları, makalede yer kazanmak için kesildi:

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

Docker, *Dockerfile*dosyasındaki her satırı işleyecek. `docker build` komutundaki `.`, Docker 'ın bir *Dockerfile*bulmak için geçerli klasörü kullanmasını söyler. Bu komut, görüntüyü oluşturur ve bu görüntüyü işaret eden **MyImage** adlı bir yerel depo oluşturur. Bu komut bittikten sonra, yüklenen görüntülerin listesini görmek için `docker images` çalıştırın:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun. *Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır. *Dockerfile dosyasına*iki komut ekleyelim. Her komut, **MyImage** Repository girişinin işaret ettiği görüntüyü temsil eden son komutla yeni bir görüntü katmanı oluşturur.

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` komutu, Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler. Bu örnekte, *Publish* klasörü kapsayıcıda *uygulama* adlı bir klasöre kopyalanır.

`ENTRYPOINT`sonraki komut, Docker 'ın kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler. Kapsayıcı başladığında `ENTRYPOINT` komutu çalışır. Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.

Terminalinizden `docker build -t myimage -f Dockerfile .` çalıştırın ve bu komutun ne zaman tamamlanerdiğinde `docker images`çalıştırın.

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

*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu. Son **görüntü kimliği** (sizinki farklı olacak) **ddcc6646461b** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz. Bir kapsayıcıyı iki şekilde oluşturabilirsiniz. İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

Yukarıdaki `docker create` komutu, **MyImage** görüntüsünü temel alan bir kapsayıcı oluşturur. Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir. *Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Kapsayıcıyı yönetme

Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz bir rastgele ad atanır. Örneğin, otomatik olarak oluşturulan kapsayıcı **gallant_lehmann** adı (sizinki farklı olacaktır) seçti ve bu ad kapsayıcıyı başlatmak için kullanılabilir. Otomatik adı, `docker create --name` parametresini kullanarak belirli bir adla geçersiz kılabilirsiniz.

Aşağıdaki örnek, kapsayıcıyı başlatmak için `docker start` komutunu kullanır ve sonra yalnızca çalıştıran kapsayıcıları göstermek için `docker ps` komutunu kullanır:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Benzer şekilde, `docker stop` komutu kapsayıcıyı durdurur. Aşağıdaki örnek, kapsayıcıyı durdurmak için `docker stop` komutunu kullanır ve ardından hiçbir kapsayıcının çalışmadığını göstermek için `docker ps` komutunu kullanır:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz. Kapsayıcıyı başlatmak ve çıkış akışına gözatmak için `docker start` ve `docker attach` komutlarını kullanın. Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu, çalışan kapsayıcıyı ayırmak için kullanılır. Bu tuş vuruşu, kapsayıcıyı durduran kapsayıcıyı gerçekten sonlandırarak işlemden çıkabilir. `--sig-proxy=false` parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar.

Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.

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

Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez. Daha önce oluşturduğunuz kapsayıcıyı silin. Kapsayıcı çalışıyorsa durdurun.

```console
> docker stop gallant_lehmann
```

Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir. Ardından, kapsayıcıyı silmek için `docker rm` komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Tek çalıştırma

Docker, kapsayıcıyı tek bir komut olarak oluşturup çalıştırmak için `docker run` komutu sağlar. Bu komut `docker create` çalıştırma gereksinimini ortadan kaldırır ve `docker start`. Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz. Örneğin, iki şeyi yapmak için `docker run -it --rm` kullanın, ilk olarak kapsayıcıya bağlanmak için geçerli terminali otomatik olarak kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

`docker run -it`, <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur. `--rm` parametresi sağlandığından, işlem durdurulduğunda kapsayıcı otomatik olarak silinir. Mevcut olmadığını doğrulayın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>GIRIŞ noktasını değiştirme

`docker run` komutu aynı zamanda *Dockerfile* içindeki `ENTRYPOINT` komutunu değiştirmenize ve yalnızca bu kapsayıcı için başka bir şey çalıştırmanıza imkan tanır. Örneğin, `bash` veya `cmd.exe`çalıştırmak için aşağıdaki komutu kullanın. Komutu gereken şekilde düzenleyin.

#### <a name="windows"></a>Windows

Bu örnekte, `ENTRYPOINT` `cmd.exe`olarak değiştirilir. İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL</kbd>+<kbd>C</kbd> 'ye basıldığında.

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

Bu örnekte, `ENTRYPOINT` `bash`olarak değiştirilir. `quit` komutu işlemi sonlandırır ve kapsayıcıyı durdurur.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Gerekli komutlar

Docker, kapsayıcınıza ve görüntülerinize ne yapmak istediğinizi kapsayan birçok farklı komuta sahiptir. Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:

- [Docker derlemesi](https://docs.docker.com/engine/reference/commandline/build/)
- [Docker çalıştırma](https://docs.docker.com/engine/reference/commandline/run/)
- [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/)
- [Docker durdur](https://docs.docker.com/engine/reference/commandline/stop/)
- [Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
- [Docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [Docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz. İsterseniz, bu kaynakları silin. İçin aşağıdaki komutları kullanın

01. Tüm kapsayıcıları Listele

    ```console
    > docker ps -a
    ```

02. Çalıştıran kapsayıcıları durdurun. `CONTAINER_NAME`, kapsayıcıya otomatik olarak atanan adı temsil eder.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Kapsayıcıyı silme

    ```console
    > docker rm CONTAINER_NAME
    ```

Sonra, makinenizde artık istemediğiniz görüntüleri silin. *Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin. **Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Yüklenen görüntülerin listesini görmek için `docker images` komutunu kullanın.

> [!NOTE]
> Görüntü dosyaları büyük olabilir. Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız. Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [ASP.NET Core mikro hizmet öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.](https://azure.microsoft.com/overview/containers/)
- [Dockerfile komutları hakkında bilgi edinin.](https://docs.docker.com/engine/reference/builder/)
- [Visual Studio için kapsayıcı araçlarını keşfet](/visualstudio/containers/overview)
