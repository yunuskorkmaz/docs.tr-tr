---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 99bbc67096d98622ca5c0dc83d8b1be44a9995e5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810553"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: bir .NET Core uygulamasını Kapsayıize edin

Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz. Kapsayıcılar, sabit bir altyapı olmak, taşınabilir bir mimari sağlamak ve ölçeklenebilirliği etkinleştirmek gibi birçok özellik ve avantaja sahiptir. Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.

Bu öğreticide şunları yaptınız:

> [!div class="checklist"]
>
> - Basit bir .NET Core uygulaması oluşturma ve yayımlama
> - .NET Core için Dockerfile oluşturma ve yapılandırma
> - Docker görüntüsü oluşturma
> - Docker kapsayıcısı oluşturma ve çalıştırma

Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız. *Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır. Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.

> [!NOTE]
> Bu öğretici ASP.NET Core uygulamalar için **değildir** . ASP.NET Core kullanıyorsanız, [bir ASP.NET Core uygulama](/aspnet/core/host-and-deploy/docker/building-net-docker-images) öğreticisini nasıl Kapsayıyoruz hakkında bilgi edinin.

## <a name="prerequisites"></a>Ön koşullar

Aşağıdaki önkoşulları yükler:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download)\
.NET Core yüklüyse, `dotnet --info` kullanmakta olduğunuz SDK 'yı öğrenmek için komutunu kullanın.
- [Docker Community sürümü](https://www.docker.com/products/docker-desktop)
- *Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü. Bu öğreticide, *Docker-Working* adı çalışma klasörü olarak kullanılır.

## <a name="create-net-core-app"></a>.NET Core uygulaması oluşturma

Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır. Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin. Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

Klasör ağaclarınız şöyle görünür:

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

`dotnet new`Komut, *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" konsol uygulaması oluşturur. Dizinleri değiştirin ve Terminal oturumunuzda *uygulama* klasörüne gidin. `dotnet run`Uygulamayı başlatmak için komutunu kullanın. Uygulama çalışır ve `Hello World!` komutun altına yazdırılır:

```dotnetcli
dotnet run
Hello World!
```

Varsayılan şablon, terminale yazdıran bir uygulama oluşturur ve hemen sonlandırılır. Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız. *Program.cs* dosyasını bir metin düzenleyicisinde açın.

> [!TIP]
> Visual Studio Code kullanıyorsanız, önceki Terminal oturumunda aşağıdaki komutu yazın:
>
> ```console
> code .
> ```
>
> Bu, Visual Studio Code projedeki projeyi içeren *uygulama* klasörünü açar.

*Program.cs* aşağıdaki C# kodu gibi görünmelidir:

```csharp
using System;

namespace NetCore.Docker
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
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

Dosyayı kaydedin ve ile programı test edin `dotnet run` . Bu uygulamanın süresiz olarak çalıştığını unutmayın. Durdurmak için <kbd>CTRL + C</kbd> Cancel komutunu kullanın. Aşağıda örnek bir çıktı verilmiştir:

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur. `dotnet run -- 5`Beş olarak saymak için deneyin.

> [!IMPORTANT]
> Sonrasında herhangi bir parametre `--` komutuna geçirilmez `dotnet run` ve bunun yerine uygulamanıza geçirilir.

## <a name="publish-net-core-app"></a>.NET Core uygulaması Yayımla

.NET Core uygulamasını Docker görüntüsüne eklemeden önce, önce yayımlanması gerekir. Kapsayıcının uygulamanın yayımlanmış sürümünü çalıştırması en iyisidir. Uygulamayı yayımlamak için şu komutu çalıştırın:

```dotnetcli
dotnet publish -c Release
```

Bu komut, uygulamanızı *Yayımla* klasörüne derler. Çalışma klasöründeki *Yayımla* klasörünün yolu `.\App\bin\Release\netcoreapp3.1\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

*Uygulama* klasöründen, *NetCore.Docker.dll* dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

`ls`Bir dizin listesi almak için komutunu kullanın ve *NetCore.Docker.dll* dosyasının oluşturulduğunu doğrulayın.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>Dockerfile oluşturma

*Dockerfile* dosyası `docker build` komut tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır. Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.

*. Csproj* Içeren dizinde *dockerfile* adlı bir dosya oluşturun ve bunu bir metin düzenleyicisinde açın. Bu öğretici, .NET Core çalışma zamanı görüntüsünü içeren ASP.NET Core çalışma zamanı görüntüsünü kullanır ve .NET Core konsol uygulamasına karşılık gelir.

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> ASP.NET Core çalışma zamanı görüntüsü kasıtlı olarak burada kullanılır, ancak `mcr.microsoft.com/dotnet/core/runtime:3.1` görüntü kullanılmış olabilir.

`FROM`Anahtar sözcüğü tam bir Docker kapsayıcı görüntüsü adı gerektirir. Microsoft Container Registry (MCR, mcr.microsoft.com), genel olarak erişilebilen kapsayıcıları barındıran Docker Hub 'ının bir genel yöneticisdir. Segment, kapsayıcının `dotnet/core` `aspnet` kapsayıcı görüntüsü adı olduğu yerde kapsayıcı deposudur. Görüntü, `3.1` sürüm oluşturma için kullanılan ile etiketlenir. Bu nedenle, `mcr.microsoft.com/dotnet/core/aspnet:3.1` .NET Core 3,1 çalışma zamanı. SDK 'nizin hedeflediği çalışma zamanıyla eşleşen çalışma zamanı sürümünü çekdiğinizden emin olun. Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3,1 SDK 'sını ve *Dockerfile* içinde başvurulan temel görüntüyü **3,1**ile etiketledi.

*Dockerfile* dosyasını kaydedin. Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir. Daha derin düzey dosya ve klasörlerden bazıları, makalede yer kazanmak için atlandı:

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

Terminalinizden aşağıdaki komutu çalıştırın:

```Docker
docker build -t counter-image -f Dockerfile .
```

Docker, *Dockerfile*dosyasındaki her satırı işleyecek. `.` `docker build` Komutunda Docker 'ın bir *dockerfile dosyasını*bulmak için geçerli klasörü kullanmasını söyler. Bu komut, görüntüyü oluşturur ve bu görüntüye işaret eden **Counter-Image** adlı bir yerel depo oluşturur. Bu komut tamamlandıktan sonra, `docker images` yüklenen görüntülerin listesini görmek için komutunu çalıştırın:

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun. *Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır. *Dockerfile dosyasına*üç komut ekleyelim. Her komut, için **Sayaç-görüntü** deposu giriş noktalarını temsil eden son komutla yeni bir görüntü katmanı oluşturur.

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

`COPY`Komut, Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler. Bu örnekte, *Publish* klasörü kapsayıcıda *uygulama* adlı bir klasöre kopyalanır.

`WORKDIR`Komut, kapsayıcının içindeki **geçerli dizini** *uygulama*olarak değiştirir.

Sonraki komut, `ENTRYPOINT` Docker öğesine kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler. Kapsayıcı başladığında, `ENTRYPOINT` komutu çalışır. Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.

Terminalinizden `docker build -t counter-image -f Dockerfile .` komutunu çalıştırın ve komut tamamlandığında komutunu çalıştırın `docker images` .

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu. Son **görüntü kimliği** (sizinki farklı olacak) **cd11c3df9b19** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz. Bir kapsayıcıyı iki şekilde oluşturabilirsiniz. İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

`docker create`Yukarıdaki komutu **sayaç görüntüsü** görüntüsünü temel alan bir kapsayıcı oluşturur. Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir. *Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>Kapsayıcıyı yönetme

Kapsayıcı belirli bir adla oluşturulmuştur `core-counter` , bu ad kapsayıcıyı yönetmek için kullanılır. Aşağıdaki örnek, `docker start` kapsayıcıyı başlatmak için komutunu kullanır ve sonra `docker ps` yalnızca çalıştıran kapsayıcıları göstermek için komutunu kullanır:

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur. Aşağıdaki örnek, `docker stop` kapsayıcıyı durdurmak için komutunu kullanır ve ardından `docker ps` hiçbir kapsayıcının çalışmadığını göstermek için komutunu kullanır:

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz. `docker start`Ve komutlarını kullanarak `docker attach` kapsayıcıyı başlatın ve çıkış akışına göz atın. Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu, çalışan kapsayıcıyı ayırmak için kullanılır. Bu tuş vuruşu, aksi belirtilmediği sürece kapsayıcıdaki işlemi sona erdirmek için kapsayıcıyı durdurur. `--sig-proxy=false`Parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar.

Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Kapsayıcı silme

Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez. Daha önce oluşturduğunuz kapsayıcıyı silin. Kapsayıcı çalışıyorsa durdurun.

```Docker
docker stop core-counter
```

Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir. Ardından, `docker rm` kapsayıcıyı silmek için komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>Tek çalıştırma

Docker, `docker run` kapsayıcıyı tek bir komut olarak oluşturup çalıştırmak için komutunu sağlar. Bu komut, ve daha sonra çalıştırma gereksinimini ortadan kaldırır `docker create` `docker start` . Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz. Örneğin, `docker run -it --rm` ilk olarak iki şey yapmak için kullanın, kapsayıcıya bağlanmak için otomatik olarak geçerli terminali kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Kapsayıcı Ayrıca parametreleri .NET Core uygulamasının yürütülmesine geçirir. .NET Core uygulamasının 3 ' te yalnızca 3 geçişine kadar saymasını bildirmek için.

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

İle `docker run -it` , <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur. `--rm`Parametre sağlandığı için, işlem durdurulduğunda kapsayıcı otomatik olarak silinir. Mevcut olmadığını doğrulayın:

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>GIRIŞ noktasını değiştirme

`docker run`Komut ayrıca `ENTRYPOINT` *dockerfile* ' dan komutu değiştirmenize ve yalnızca bu kapsayıcı için, başka bir şey çalıştırmanıza imkan tanır. Örneğin, veya çalıştırmak için aşağıdaki komutu kullanın `bash` `cmd.exe` . Komutu gereken şekilde düzenleyin.

#### <a name="windows"></a>[Windows](#tab/windows)

Bu örnekte, `ENTRYPOINT` olarak değiştirilir `cmd.exe` . İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL + C</kbd> tuşlarına basıldığında.

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

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

#### <a name="linux"></a>[Linux](#tab/linux)

Bu örnekte, `ENTRYPOINT` olarak değiştirilir `bash` . `exit`Komut, işlemi sonlandıran ve kapsayıcıyı durduran çalıştırılır.

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>Gerekli komutlar

Docker kapsayıcıları ve görüntüleri oluşturan, yöneten ve bunlarla etkileşim kuran birçok farklı komuta sahiptir. Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [Docker çalıştırma](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [Docker durdur](https://docs.docker.com/engine/reference/commandline/stop/)
- [Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
- [Docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [Docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz. İsterseniz, bu kaynakları silin. İçin aşağıdaki komutları kullanın

01. Tüm kapsayıcıları Listele

    ```Docker
    docker ps -a
    ```

02. Adına göre çalışan kapsayıcıları durdurun.

    ```Docker
    docker stop counter-image
    ```

03. Kapsayıcıyı silme

    ```Docker
    docker rm counter-image
    ```

Sonra, makinenizde artık istemediğiniz görüntüleri silin. *Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin. **Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

`docker images`Yüklenen görüntülerin listesini görmek için komutunu kullanın.

> [!TIP]
> Görüntü dosyaları büyük olabilir. Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız. Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [ASP.NET Core mikro hizmet öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.](https://azure.microsoft.com/overview/containers/)
- [Dockerfile komutları hakkında bilgi edinin.](https://docs.docker.com/engine/reference/builder/)
- [Visual Studio için kapsayıcı araçlarını keşfet](/visualstudio/containers/overview)
