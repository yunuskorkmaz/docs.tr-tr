---
title: Docker öğreticisiyle bir uygulamayı kapsayıcılı hale getirme
description: Bu öğreticide, bir .NET Core uygulamasını Docker ile kapsayıcılı hale getirme öğreneceksiniz.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 16edb129be679179450c485ced2586cea9ed9763
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609293"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Öğretici: .NET Core uygulamasını kapsayıcılı hale getirme

Bu öğreticide, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretiyor. Görüntü, kapsayıcılar, yerel geliştirme ortamı, özel Bulut veya genel bulut oluşturmak için kullanılabilir.

Şunları öğreneceksiniz:

> [!div class="checklist"]
> * Oluşturma ve basit bir .NET Core uygulaması yayımlama
> * Oluşturma ve .NET Core için bir Dockerfile'ı yapılandırma
> * Bir Docker görüntüsü oluşturun
> * Oluşturma ve bir Docker kapsayıcısında çalıştırma

Docker kapsayıcı derleme ve dağıtım görevleri için bir .NET Core uygulaması anlayacaksınız. *Docker platformu* kullanan *Docker altyapısı* oluşturmayı ve uygulamaları olarak paketini *Docker görüntülerini*. Bu görüntüleri yazılan *Dockerfile* dağıtılabilir ve katmanlı kapsayıcısında çalıştırma biçimi.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki önkoşulları yükleyin:

* [.NET core SDK'sını 2.2](https://dotnet.microsoft.com/download)\
.NET Core yüklü varsa `dotnet --info` kullandığınız hangi SDK belirlemek için komutu.

* [Docker Community Edition](https://www.docker.com/products/docker-desktop)

* Geçici bir çalışma klasörü için *Dockerfile* ve .NET Core örnek uygulaması. Bu öğreticide, adı `docker-working` çalışma klasörü olarak kullanılır.

### <a name="use-sdk-version-22"></a>SDK 2.2 sürümünü kullanın

3\.0 gibi yeni bir SDK kullanıyorsanız, uygulamanızı 2.2 SDK'yı kullanmaya zorlanır emin olun. Adlı bir dosya oluşturun `global.json` çalışma klasörü ve aşağıdaki json kodunu yapıştırın:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

Bu dosyayı kaydedin. Sürüm 2.2 için kullanılacak .NET Core dosyasının varlığını zorlayacak `dotnet` bu klasörden ve aşağıdaki komutu olarak adlandırılır.

## <a name="create-net-core-app"></a>Oluşturma .NET Core uygulaması

Docker kapsayıcısı çalıştıracak bir .NET Core uygulaması gerekir. Terminalinizi açın, henüz indirmediyseniz ve girin, bir çalışma klasörü oluşturun. Çalışma klasörü içinde uygulama adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new console -o app -n myapp
```

Klasörü ağacında aşağıdaki gibi görünür:

```console
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

`dotnet new` Komut adlı yeni bir klasör oluşturur *uygulama* ve bir "Hello World" uygulaması oluşturur. Girin *uygulama* klasör ve şu komutu çalıştırın `dotnet run`. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Hello World!
```

Varsayılan şablonu, terminale yazdırır ve kapanır bir uygulama oluşturur. Bu öğreticide, sonsuza kadar döngü bir uygulama kullanmanız gerekir. Açık **Program.cs** dosyasını bir metin düzenleyicisinde. Bu, şu anda şu kod gibi görünmelidir:

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

Dosya, her saniye sayısını sayar aşağıdaki kodla değiştirin:

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

Dosyayı kaydedin ve programı yeniden test `dotnet run`. Bu uygulama süresiz olarak çalıştığını unutmayın. Cancel komutu kullanma <kbd>CTRL + C</kbd> durdurmak ister. Aşağıdaki çıktıyı görürsünüz:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Uygulama için komut satırında bir sayı geçirirseniz, bunu yalnızca kadar tutar ve ardından çıkış sayılır. İle deneyin `dotnet run -- 5` beş sayısı.

> [!NOTE]
> Sonra herhangi bir parametre `--` için geçmedi `dotnet run` komut ve bunun yerine, uygulamanıza geçirilir.

## <a name="publish-net-core-app"></a>Yayımlama .NET Core uygulaması

.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın. Kapsayıcı başlatıldığında uygulama yayımlanmış sürümü çalıştığından emin olmanız gerekir.

Çalışma klasöründen girin **uygulama** klasörü örnek kaynak kodu ve şu komutu çalıştırın:

```console
dotnet publish -c Release
```

Bu komut, uygulamanızın derler **yayımlama** klasör. Yolu **yayımlama** çalışma klasörü klasöründen olmalıdır. `.\app\bin\Release\netcoreapp2.2\publish\`

Doğrulamak için yayımlama klasörünün dizin bir listesini **myapp.dll** oluşturuldu. Gelen **uygulama** klasörü, aşağıdaki komutlardan birini çalıştırın:

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

## <a name="create-the-dockerfile"></a>Dockerfile'ı oluşturma

*Dockerfile* dosya tarafından kullanılan `docker build` bir kapsayıcı görüntüsü oluşturmak için komutu. Adlı bir düz metin dosyası bu dosyadır *Dockerfile* uzantı yok.

Terminalinizde başında oluşturduğunuz çalışma klasörü için bir dizin yukarı gidin. Adlı bir dosya oluşturun *Dockerfile* çalışma klasöründeki bir metin düzenleyicisinde açın. Aşağıdaki komut dosyasının ilk satırı ekleyin:

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
```

`FROM` Komutu bildirir etiketli görüntüyü çekmek için Docker **2.2** gelen **mcr.microsoft.com/dotnet/core/runtime** depo. Çalışma zamanı, SDK'sı tarafından hedeflenen eşleşen .NET Core çalışma zamanı çekme emin olun. Örneğin, önceki oluşturulan uygulama bölümünde kullanılan .NET Core 2.2 SDK ve .NET Core 2.2 hedefleyen bir uygulama oluşturdunuz. Temel görüntü başvurulan şekilde *Dockerfile* ile etiketlenmiş **2.2**.

Kaydet *Dockerfile* dosya. Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir. Daha ayrıntılı düzeyinde dosya ve klasörleri bazıları makalesinde yer kazanmak için kaldırılmıştır:

```console
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

Uygulamanızı terminalden çalıştırın `docker build -t myimage -f Dockerfile .` ve Docker, her satır işleyecek *Dockerfile*. `.` İçinde `docker build` komut geçerli klasörü bulmak için kullanmak üzere docker belirten bir *Dockerfile*. Bu komut, görüntüyü oluşturur ve adlı yerel bir depo oluşturur **myımage** görüntüsünü işaret eder. Bu komut bittikten sonra Çalıştır `docker images` yüklü görüntülerin listesini görmek için:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

İki görüntü aynı paylaşım bildirimi **görüntü kimliği** değeri. Değer her iki görüntü arasında aynı çünkü yalnızca komutta *Dockerfile* üzerinde mevcut bir görüntüyü yeni görüntüyü temel oluşturmaktı. İki komutu ekleyelim *Dockerfile*. Her komut, görüntünün temsil eden son komutu ile yeni bir görüntü katmanı oluşturur **myımage** depo işaret.

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` Komut Docker kapsayıcısında bir klasöre bilgisayarınız üzerindeki belirtilen klasöre kopyalamak için bildirir. Bu örnekte, **yayımlama** klasör adlı bir klasöre kopyalanır **uygulama** kapsayıcısında.

Sonraki komut `ENTRYPOINT`, yürütülebilir dosya olarak çalıştırmak için kapsayıcı yapılandırmak için docker söyler. Kapsayıcı başlatıldığında, `ENTRYPOINT` komutunu çalıştırır. Bu komut sona erdiğinde, kapsayıcı otomatik olarak durdurulur.

Uygulamanızı terminalden çalıştırın `docker build -t myimage -f Dockerfile .` ve tamamlandığında, komut, çalıştırılabilir `docker images`.

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

Her komut, *Dockerfile* katmanındaki oluşturulur ve oluşturulan bir **görüntü kimliği**. En son **görüntü kimliği** (sizinki farklı olacaktır) olan **ddcc6646461b** ve ardından bu görüntüyü temel alarak bir kapsayıcı oluşturursunuz.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Uygulamanızı içeren bir görüntünüz olduğuna göre bir kapsayıcı oluşturabilirsiniz. Bir kapsayıcı iki şekilde oluşturabilirsiniz. İlk olarak durduruldu yeni bir kapsayıcı oluşturun.

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

`docker create` Yukarıdaki komut, temel bir kapsayıcı oluşturur **myımage** görüntü. Bu komutun çıktısı, gösterir **KAPSAYICI kimliği** (sizinki farklı olacaktır) oluşturulan kapsayıcı. Bir listesini görmek için *tüm* kapsayıcılarını, `docker ps -a` komutu:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>Kapsayıcı yönetme

Her kapsayıcı, bir kapsayıcı örneğe atıfta için kullanabileceğiniz rastgele bir ad atanmıştır. Örneğin, otomatik olarak oluşturulan kapsayıcı adı seçtiğiniz **boring_matsumoto** (sizinki farklı olacaktır) ve bu ad, kapsayıcı başlatma için kullanılabilir. Otomatik adıyla kullanarak belirli bir geçersiz kılma `docker create --name` parametresi.

Aşağıdaki örnekte `docker start` kapsayıcı ve ardından kullandığı başlatmak için komut `docker ps` komutu yalnızca çalışan kapsayıcılar göstermek için:

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

Benzer şekilde, `docker stop` komutu, kapsayıcı durdurur. Aşağıdaki örnekte `docker stop` kapsayıcı ve ardından kullandığı durdurmak için komutu `docker ps` kapsayıcı çalıştığını göstermek için komutu.

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Bir kapsayıcıya bağlanma

Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bağlanabilirsiniz. Kullanım `docker start` ve `docker attach` kapsayıcı ve çıkış akışına göz at'ı başlatmak için komutları. Bu örnekte, <kbd>CTRL + C</kbd> komutu, çalışmakta olan kapsayıcıyı ayırmak için kullanılır. Bu, gerçekten kapsayıcı durdurur kapsayıcı işlemde sonlandırabiliriz. `--sig-proxy=false` Parametresi sağlar <kbd>CTRL + C</kbd> kapsayıcı işlemde durdurmaz.

Kapsayıcıdan ayırdıktan sonra bunu hala çalışan sayım ve olduğunu doğrulamak için yeniden bağlayın.

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

### <a name="delete-a-container"></a>Bir kapsayıcıyı Sil

Bu makalenin amaçları yalnızca geçici bir çözüm birşey asılı kapsayıcıları istemezsiniz. Daha önce oluşturduğunuz kapsayıcıya silin. Kapsayıcı çalışıyorsa durdurun.

```console
> docker stop boring_matsumoto
```

Aşağıdaki örnek, tüm kapsayıcıları listeler. Ardından kullanır `docker rm` kapsayıcısını silme komutunu ve ardından ikinci bir kez çalıştıran tüm kapsayıcıları için denetler.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Tek çalışma

Docker sağlar `docker run` oluşturma ve kapsayıcı tek bir komut çalıştırmak için komutu. Bu komutu çalıştırma ihtiyacı ortadan kaldırır. `docker create` ardından `docker start`. Kapsayıcı durduğunda kapsayıcı otomatik olarak silmek için bu komutu da ayarlayabilirsiniz. Örneğin, `docker run -it --rm` iki işlem gerçekleştirmesi için ilk olarak, otomatik olarak kapsayıcıya bağlanmak için geçerli terminal kullanın ve kapsayıcı sona erdiğinde, kaldırın:

```
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

İle `docker run -it`, <kbd>CTRL + C</kbd> komutu sırayla kapsayıcısını durdurur kapsayıcı içinde çalışmakta olan işlemi durdurur. Bu yana `--rm` parametresi sağlanmadığından, işlem durduğunda kapsayıcı otomatik olarak silinir. Mevcut olduğunu doğrulayın:

```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Giriş noktası değiştirme

`docker run` Komut ayrıca, değiştirmenize imkan tanır `ENTRYPOINT` komutunu *Dockerfile* ve başka bir ancak için yalnızca o kapsayıcı çalıştırın. Örneğin, çalıştırmak için aşağıdaki komutu kullanın `bash` veya `cmd.exe`. Komutu, gerektiği gibi düzenleyin.

#### <a name="windows"></a>Windows
Bu örnekte, `ENTRYPOINT` değiştirilir `cmd.exe`. <kbd>CTRL + C</kbd> işlemi sona erdirmek ve kapsayıcıyı durdurmak için basılan.

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

Bu örnekte, `ENTRYPOINT` değiştirilir `bash`. `quit` İşlemi sonlandırır ve kapsayıcı Durdur komutu çalıştırın.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Gerekli komutları

Docker, kapsayıcı ve görüntülerle yapmak istediğiniz kapsayan çok sayıda farklı komutlar vardır. Bu Docker komutlarını kapsayıcıları yönetmek için gereklidir:

* [docker derleme](https://docs.docker.com/engine/reference/commandline/build/)
* [docker Run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker durdurma](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker RMI](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker görüntüsü](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğretici sırasında kapsayıcılar ve görüntüleri oluşturuldu. İsterseniz, bu kaynakları silin. İçin aşağıdaki komutları kullanın

01. Tüm kapsayıcıları listesi

    ```console
    > docker ps -a
    ```

02. Çalışan kapsayıcıları durdurmak. `CONTAINER_NAME` Kapsayıcıya otomatik olarak atanan adını temsil eder.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Kapsayıcıyı Sil

    ```console
    > docker rm CONTAINER_NAME
    ```

Ardından, makinenizde artık istemediğiniz tüm görüntüleri silin. Tarafından oluşturulan görüntüyü silin, *Dockerfile* ve .NET Core görüntüyü silin *Dockerfile* temel. Kullanabileceğiniz **görüntü kimliği** veya **DEPO: Etiket** biçimlendirilmiş dize.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

Kullanım `docker images` yüklü görüntülerin listesini görmek için komutu.

> [!NOTE]
> Görüntü dosyaları büyük olabilir. Genellikle, test ve uygulama geliştirme sırasında oluşturulan geçici kapsayıcıları kaldırın. Genellikle, bu çalışma zamanına göre diğer görüntüleri oluşturmaya düşünüyorsanız yüklü olan çalışma zamanı ile temel görüntüleri tutun.

## <a name="next-steps"></a>Sonraki adımlar

* [ASP.NET Core mikro hizmet öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Kapsayıcıları destekleyen Azure Hizmetleri gözden geçirin.](https://azure.microsoft.com/overview/containers/)
* [Dockerfile komutlarının hakkında okuyun.](https://docs.docker.com/engine/reference/builder/)
* [Visual Studio kapsayıcı araçları keşfedin](/visualstudio/containers/overview)
