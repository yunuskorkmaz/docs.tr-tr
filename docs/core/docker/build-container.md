---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek öğreneceksiniz.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: f0e0fad9bde4c35fb5c5b0b505b9fa8441e432ba
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926313"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: .NET Core uygulamasını kapsayıcılı hale getirme

Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretir. Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.

Şunları öğreneceksiniz:

> [!div class="checklist"]
>
> * Basit bir .NET Core uygulaması oluşturma ve yayımlama
> * .NET Core için Dockerfile oluşturma ve yapılandırma
> * Docker görüntüsü oluşturma
> * Docker kapsayıcısı oluşturma ve çalıştırma

Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız. *Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır. Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki önkoşulları yükler:

* [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download)\
.NET Core yüklüyse, kullanmakta olduğunuz SDK 'yı öğrenmek `dotnet --info` için komutunu kullanın.

* [Docker Community sürümü](https://www.docker.com/products/docker-desktop)

* *Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü. Bu öğreticide, ad `docker-working` çalışma klasörü olarak kullanılır.

### <a name="use-sdk-version-22"></a>SDK sürüm 2,2 kullanma

3,0 gibi daha yeni bir SDK kullanıyorsanız uygulamanızın 2,2 SDK 'Yı kullanmaya zorlandığından emin olun. Çalışma klasörünüzde adlı `global.json` bir dosya oluşturun ve aşağıdaki JSON kodunu yapıştırın:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Bu dosyayı kaydedin. Dosya varlığı, .NET Core 'un bu klasörden ve aşağıda çağrılan herhangi bir `dotnet` komut için sürüm 2,2 ' i kullanmasına zorlayacaktır.

## <a name="create-net-core-app"></a>.NET Core uygulaması oluşturma

Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır. Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin. Çalışma klasöründe, uygulama adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new console -o app -n myapp
```

Klasör ağaclarınız şöyle görünür:

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

Komut `dotnet new` , *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" uygulaması oluşturur. *Uygulama* klasörünü girip komutunu `dotnet run`çalıştırın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Hello World!
```

Varsayılan şablon, terminale yazdıran ve ardından çıkış yapan bir uygulama oluşturur. Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız. **Program.cs** dosyasını bir metin düzenleyicisinde açın. Şu anda şu kod gibi görünmelidir:

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Dosyayı kaydedin ve ile `dotnet run`programı test edin. Bu uygulamanın süresiz olarak çalıştığını unutmayın. Durdurmak için <kbd>CTRL + C</kbd> Cancel komutunu kullanın. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur. Beş olarak saymak için deneyin. `dotnet run -- 5`

> [!NOTE]
> Sonrasında `--` herhangi bir parametre `dotnet run` komutuna geçirilmez ve bunun yerine uygulamanıza geçirilir.

## <a name="publish-net-core-app"></a>.NET Core uygulaması Yayımla

.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın. Kapsayıcının, başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırmasını sağlamak istiyorsunuz.

Çalışma klasöründen, örnek kaynak kodu ile **uygulama** klasörünü girin ve şu komutu çalıştırın:

```console
dotnet publish -c Release
```

Bu komut, uygulamanızı **Yayımla** klasörüne derler. Çalışma klasöründeki **Yayımla** klasörünün yolu`.\app\bin\Release\netcoreapp2.2\publish\`

**MyApp. dll** dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın. **Uygulama** klasöründen aşağıdaki komutlardan birini çalıştırın:

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Dockerfile oluşturma

*Dockerfile* dosyası `docker build` komut tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır. Bu dosya, uzantısı olmayan *Dockerfile* adlı bir düz metin dosyasıdır.

Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörünün dizinine gidin. Çalışma klasörünüzde *Dockerfile* adlı bir dosya oluşturun ve dosyayı bir metin düzenleyicisinde açın. Aşağıdaki komutu dosyanın ilk satırı olarak ekleyin:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

Komut `FROM` , Docker 'ın **MCR.Microsoft.com/DotNet/Core/Runtime** deposundan etiketli **2,2** görüntüsünü çekmesini söyler. SDK 'nizin hedeflediği çalışma zamanına uyan .NET Core çalışma zamanını çekdiğinizden emin olun. Örneğin, önceki bölümde oluşturulan uygulama .NET Core 2,2 SDK 'sını kullandı ve .NET Core 2,2 ' yi hedefleyen bir uygulama oluşturdu. Bu nedenle, *Dockerfile* dosyasında başvurulan temel görüntü **2,2**ile etiketlenir.

*Dockerfile* dosyasını kaydedin. Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir. Daha derin düzey dosya ve klasörlerin bazıları, makalede yer kazanmak için kesildi:

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
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

Docker, *Dockerfile*dosyasındaki her satırı işleyecek. Komutunda Docker 'ın bir *dockerfile dosyasını*bulmak için geçerli klasörü kullanmasını söyler. `.` `docker build` Bu komut, görüntüyü oluşturur ve bu görüntüyü işaret eden **MyImage** adlı bir yerel depo oluşturur. Bu komut tamamlandıktan sonra, yüklenen `docker images` görüntülerin listesini görmek için komutunu çalıştırın:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun. *Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır. *Dockerfile dosyasına*iki komut ekleyelim. Her komut, **MyImage** deposunun işaret ettiği görüntüyü temsil eden son komutla yeni bir görüntü katmanı oluşturur.

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

Komut `COPY` , Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler. Bu örnekte, **Publish** klasörü kapsayıcıda **uygulama** adlı bir klasöre kopyalanır.

Sonraki komut `ENTRYPOINT`, Docker öğesine kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler. Kapsayıcı başladığında, `ENTRYPOINT` komutu çalışır. Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.

Terminalinizden komutunu çalıştırın `docker build -t myimage -f Dockerfile .` ve komut tamamlandığında komutunu çalıştırın `docker images`.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu. Son **görüntü kimliği** (sizinki farklı olacak) **ddcc6646461b** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.

## <a name="create-a-container"></a>Kapsayıcı oluşturma

Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz. Bir kapsayıcıyı iki şekilde oluşturabilirsiniz. İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

Yukarıdaki komut, MyImage görüntüsünü temel alan bir kapsayıcı oluşturur. `docker create` Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir. *Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Kapsayıcıyı yönetme

Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz bir rastgele ad atanır. Örneğin, otomatik olarak oluşturulan kapsayıcı **boring_matsumoto** adını (sizinki farklı olur) seçti ve bu ad kapsayıcıyı başlatmak için kullanılabilir. `docker create --name` Parametresini kullanarak otomatik adı belirli bir ile geçersiz kılabilirsiniz.

Aşağıdaki örnek, kapsayıcıyı başlatmak `docker start` için komutunu kullanır ve sonra yalnızca çalıştıran kapsayıcıları göstermek için `docker ps` komutunu kullanır:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur. Aşağıdaki örnek, kapsayıcıyı durdurmak `docker stop` için komutunu kullanır ve ardından hiçbir kapsayıcının çalışmadığını göstermek için `docker ps` komutunu kullanır.

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz. `docker start` Ve`docker attach` komutlarını kullanarak kapsayıcıyı başlatın ve çıkış akışına göz atın. Bu örnekte, <kbd>CTRL + C</kbd> komutu, çalışan kapsayıcıyı ayırmak için kullanılır. Bu işlem, kapsayıcıyı durduran kapsayıcıyı gerçekten sonlandıracaktır. Parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar. `--sig-proxy=false`

Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Kapsayıcıyı silme

Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez. Daha önce oluşturduğunuz kapsayıcıyı silin. Kapsayıcı çalışıyorsa durdurun.

```console
> docker stop boring_matsumoto
```

Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir. Ardından, kapsayıcıyı silmek `docker rm` için komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Tek çalıştırma

Docker, kapsayıcıyı `docker run` tek bir komut olarak oluşturup çalıştırmak için komutunu sağlar. Bu komut, ve daha sonra `docker create` `docker start`çalıştırma gereksinimini ortadan kaldırır. Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz. Örneğin, ilk olarak `docker run -it --rm` iki şey yapmak için kullanın, kapsayıcıya bağlanmak için otomatik olarak geçerli terminali kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

İle `docker run -it`, <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur. `--rm` Parametre sağlandığı için, işlem durdurulduğunda kapsayıcı otomatik olarak silinir. Mevcut olmadığını doğrulayın:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>GIRIŞ noktasını değiştirme

Komut ayrıca *dockerfile* ' dan `ENTRYPOINT` komutu değiştirmenize ve yalnızca bu kapsayıcı için, başka bir şey çalıştırmanıza imkan tanır. `docker run` Örneğin, veya `bash` `cmd.exe`çalıştırmak için aşağıdaki komutu kullanın. Komutu gereken şekilde düzenleyin.

#### <a name="windows"></a>Windows
Bu örnekte, `ENTRYPOINT` olarak `cmd.exe`değiştirilir. İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL + C</kbd> tuşlarına basıldığında.

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

Bu örnekte, `ENTRYPOINT` olarak `bash`değiştirilir. `quit` Komut, işlemi sonlandıran ve kapsayıcıyı durduran çalıştırılır.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Gerekli komutlar

Docker, kapsayıcınıza ve görüntülerinize ne yapmak istediğinizi kapsayan birçok farklı komuta sahiptir. Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:

* [Docker derlemesi](https://docs.docker.com/engine/reference/commandline/build/)
* [Docker çalıştırma](https://docs.docker.com/engine/reference/commandline/run/)
* [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/)
* [Docker durdur](https://docs.docker.com/engine/reference/commandline/stop/)
* [Docker RM](https://docs.docker.com/engine/reference/commandline/rm/)
* [Docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [Docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz. İsterseniz, bu kaynakları silin. İçin aşağıdaki komutları kullanın

01. Tüm kapsayıcıları Listele

    ```console
    > docker ps -a
    ```

02. Çalıştıran kapsayıcıları durdurun. , `CONTAINER_NAME` Kapsayıcıya otomatik olarak atanan adı temsil eder.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Kapsayıcıyı sil

    ```console
    > docker rm CONTAINER_NAME
    ```

Sonra, makinenizde artık istemediğiniz görüntüleri silin. *Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin. **Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

Yüklenen görüntülerin listesini görmek için komutunukullanın.`docker images`

> [!NOTE]
> Görüntü dosyaları büyük olabilir. Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız. Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

* [ASP.NET Core mikro hizmet öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.](https://azure.microsoft.com/overview/containers/)
* [Dockerfile komutları hakkında bilgi edinin.](https://docs.docker.com/engine/reference/builder/)
* [Visual Studio için kapsayıcı araçlarını keşfet](/visualstudio/containers/overview)
