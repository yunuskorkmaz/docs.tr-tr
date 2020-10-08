---
title: AKS/Kubernetes kümelerine Linux kapsayıcıları olarak dağıtılan ASP.NET Core uygulamalar oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 08/06/2020
ms.openlocfilehash: 8b3141d79eeb252ec3721d57293bed0e335b41d3
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844569"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Bir AKS/Kubernetes Orchestrator 'a Linux kapsayıcıları olarak dağıtılan ASP.NET Core uygulamalar oluşturun

Azure Kubernetes Hizmetleri (AKS), Azure 'un kapsayıcı dağıtımı ve yönetimini kolaylaştıran yönetilen Kubernetes yönetimi hizmetidir.

AKS ana özellikleri şunlardır:

- Azure 'da barındırılan denetim düzlemi
- Otomatik yükseltmeler
- Kendi kendini onarma
- Kullanıcı tarafından yapılandırılabilir ölçekleme
- Hem geliştiriciler hem de küme işleçleri için daha basit kullanıcı deneyimi.

Aşağıdaki örneklerde, Linux üzerinde çalışan ve Azure 'daki bir AKS kümesine dağıtan ASP.NET Core 3,1 uygulamasının oluşturulması araştırırken Visual Studio 2019 kullanılarak geliştirme yapılır.

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a>Visual Studio 2019 kullanarak ASP.NET Core projesi oluşturma

ASP.NET Core, GitHub 'da Microsoft ve .NET Community tarafından tutulan genel amaçlı bir geliştirme platformudur. Windows, macOS ve Linux 'un desteklenme ve cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanılabilen platformlar arası bir platformdur.

Bu örnek, Visual Studio şablonlarına dayalı birkaç basit proje kullanır, bu nedenle örneği oluşturmak için çok fazla ek bilgiye gerek kalmaz. Projeyi, ASP.NET Core 3,1 teknolojisini kullanarak REST API ve Razor sayfaları olan bir Web uygulamasıyla küçük bir proje çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak oluşturmanız yeterlidir.

![Visual Studio 'da ASP.NET Core Web uygulaması ' nı seçerek yeni proje penceresi ekleyin.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

**Şekil 4-35**. Visual Studio 2019 ' de ASP.NET Core Web uygulaması oluşturma.

Visual Studio 'da örnek proje oluşturmak için **Dosya**  >  **Yeni**  >  **Proje**' yi seçin, **Web** projesi türünü ve ardından **ASP.NET Core Web uygulaması** şablonunu seçin. Ayrıca, gerekirse şablon için arama yapabilirsiniz.

Ardından, sonraki görüntüde gösterildiği gibi uygulama adını ve konumunu girin.

![Proje adını ve konumunu girin.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

**Şekil 4-36**. Visual Studio 2019 ' de proje adını ve konumunu girin.

Framework olarak ASP.NET Core 3,1 ' i seçtiğinizi doğrulayın. .NET Core 3,1, Visual Studio 2019 ' nin en son sürümüne dahildir ve Visual Studio 'Yu yüklediğinizde sizin için otomatik olarak yüklenir ve yapılandırılır.

![API seçeneği seçili ASP.NET Core Web uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

**Şekil 4-37**. ASP.NET CORE 3,1 ve Web API proje türünü seçme

Artık Docker desteğinin, Proje oluşturulduktan sonra yapılabileceğini göstermek için etkin olmadığına dikkat edin.

.NET Core 'un önceki bir sürümüne sahipseniz, 3,1 sürümünü indirip yükleyebilirsiniz <https://dotnet.microsoft.com/download> .

Projenizi dilediğiniz zaman "Dockerize" gösterebilmeniz için artık Docker desteği ekleyeceğiz. Bu nedenle Çözüm Gezgini içindeki proje düğümüne sağ tıklayın ve **Add**  >  bağlam menüsünde**Docker desteği** Ekle ' yi seçin.

![Mevcut bir projeye Docker desteği eklemek için bağlam menü seçeneği: > Docker desteği eklemek > (projede) öğesine sağ tıklayın.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

**Şekil 4-38**. Mevcut bir projeye Docker desteği ekleme

Docker desteği ekleme işleminin tamamlanabilmesi için Windows veya Linux ' u seçebilirsiniz. Bu durumda, **Linux**' u seçin.

![Dockerfile için hedef işletim sistemini seçmek üzere seçenek iletişim kutusu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

**Şekil 4-39**. Linux kapsayıcıları seçiliyor.

Bu basit adımlarla bir Linux kapsayıcısında çalışan ASP.NET Core 3,1 uygulamanız vardır.

Benzer bir şekilde, Web API uç noktasını kullanmak için çok basit bir **WebApp** projesi (Şekil 4-40) ekleyebilirsiniz, ancak Ayrıntılar burada açıklanmaz.

Bundan sonra, görüntü 4-40 ' de aşağıda gösterildiği gibi, **WebApi** projeniz için Orchestrator desteği eklersiniz.

![WebApi projesine Orchestrator desteği ekleniyor](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

**Şekil 4-40**. *WebApi* projesine Orchestrator desteği ekleniyor.

`Docker Compose`Yerel geliştirme için iyi olan seçeneğini belirlediğinizde, Visual Studio Docker-Compose projesini, görüntü 4-41 ' de gösterildiği gibi Docker-Compose dosyaları ile ekler.

![Docker-Compose çözüme eklendi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

**Şekil 4-41**. *WebApi* projesine Orchestrator desteği ekleniyor.

Eklenen ilk dosyalar bunlara benzerdir:

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

Uygulamanızı çalıştırmak için Docker Compose yalnızca birkaç tdalgalı KS yapmanız gerekir `docker-compose.override.yml`

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

Artık, görüntü 4-42 ' de gösterildiği gibi, uygulamanızı **F5** tuşuyla veya **oynat** düğmesini ya da **CTRL + F5** tuşunu kullanarak Docker-Compose projesini seçerek çalıştırabilirsiniz.

![Visual Studio ile Docker-Compose projesi çalıştırma](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

**Şekil 4-42**. *WebApi* projesine Orchestrator desteği ekleniyor.

Docker-Compose uygulamasını açıklandığı şekilde çalıştırırken şunları alırsınız:

1. Docker-Compose dosyasına göre oluşturulan ve kapsayıcı görüntüleri.
2. Tarayıcı, proje için "Özellikler" iletişim kutusunda yapılandırılan adreste açılır `docker-compose` .
3. **Kapsayıcı** penceresi açık (Visual Studio 2019 sürüm 16,4 ve sonraki sürümlerde).
4. Aşağıdaki resimlerde gösterildiği gibi, Çözümdeki tüm projeler için hata ayıklayıcı desteği.

Tarayıcı açıldı:

![Web uygulamasının çalıştığı tarayıcı görünümü](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

**Şekil 4-43**. Birden çok kapsayıcı üzerinde çalışan bir uygulamayla tarayıcı penceresi.

Kapsayıcılar penceresi:

![Visual Studio "kapsayıcılar" penceresi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

**Şekil 4-44**. Visual Studio "kapsayıcılar" penceresi

**Kapsayıcılar** penceresi, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir Terminal penceresi açmaya olanak sağlar.

Gördüğünüz gibi, Visual Studio 2019 ile Docker arasındaki tümleştirme, geliştiricinin verimliliğine tamamen dayalıdır.

Kuşkusuz, komutunu kullanarak da görüntüleri listeleyebilirsiniz `docker images` . `webapi` `webapp` `dev` Visual Studio 2019 ile projemizin otomatik dağıtımı tarafından oluşturulan etiketlerle ve görüntülerini görmeniz gerekir.

```console
docker images
```

![Docker görüntüleri komutundan konsol çıktısı: depo, etiket, görüntü KIMLIĞI, oluşturulan (Tarih) ve boyut içeren bir liste gösterir.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

**Şekil 4-45**. Docker görüntülerinin görünümü

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a>Çözümü bir Azure Container Registry kaydetme (ACR)

Görüntüleri [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)yükleyebilirsiniz, ancak Docker Hub veya başka bir kayıt defteri de kullanabilirsiniz. bu sayede, görüntüler bu kayıt defterinden aks kümesine dağıtılabilir.

### <a name="create-an-acr-instance"></a>ACR örneği oluşturma

**Az CLI**konumundan şu komutu çalıştırın:

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> Kapsayıcı kayıt defteri adı (ör. `exploredocker` ) Azure içinde benzersiz olmalı ve 5-50 alfasayısal karakter içermelidir. Daha ayrıntılı bilgi için bkz. [kapsayıcı kayıt defteri oluşturma](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)

### <a name="create-the-image-in-release-mode"></a>Görüntüyü yayın modunda oluşturma

Şimdi, Şekil 4-46 ' de gösterildiği gibi, **yayın**moduna geçiş yaparak ve uygulamayı daha önce yaptığınız gibi çalıştırarak **yayın** modunda (üretim için hazır) görüntüyü oluşturacaksınız.

![Yayın modunda derleme ' deki araç çubuğu seçeneği.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

**Şekil 4-46**. Yayın modunu seçme

`docker images`Komutu çalıştırırsanız, bir tane `debug` (**geliştirme**) ve diğeri `release` (**en son**) modu için oluşturulan görüntüleri görürsünüz.

### <a name="create-a-new-tag-for-the-image"></a>Görüntü için yeni bir etiket oluşturun

Her kapsayıcı görüntüsünün kayıt defteri adıyla etiketlenmesi gerekir `loginServer` . Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderilirken kullanılır.

`loginServer`Azure Container Registry bilgileri alarak Azure Portal adı görüntüleyebilirsiniz

![Azure Container kayıt defteri adının sağ üst tarafındaki tarayıcı görünümü.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

**Şekil 4-47**. Kayıt defterinin adının görünümü

Ya da aşağıdaki komutu çalıştırarak:

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

**Şekil 4-48**. **Az CLI** kullanarak kayıt defterinin adını alın

Her iki durumda da adı elde edersiniz. Örneğimizde, `exploredocker.azurecr.io` .

Artık, şu komutla birlikte en son görüntüyü (yayın görüntüsü) alarak resmi etiketleyebilir:

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

Komutunu çalıştırdıktan sonra, `docker tag` komutuyla görüntüleri listeleyin `docker images` ve yeni etiketiyle birlikte resmi görmeniz gerekir.

![Docker görüntüleri komutundan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

**Şekil 4-49**. Etiketli görüntülerin görünümü

### <a name="push-the-image-into-the-azure-acr"></a>Görüntüyü Azure ACR 'ye gönderme

Azure Container Registry oturum açın

```console
az acr login --name exploredocker
```

Aşağıdaki komutu kullanarak görüntüyü Azure ACR 'ye gönderin:

```console
docker push <login-server-name>/<image-name>:v1
```

Bu komut, görüntüleri karşıya yüklerken bir işlem gerçekleştirir, ancak işlemde geri bildirim sağlar. Aşağıdaki görüntüde, bir görüntüden alınan çıktıyı ve devam eden başka bir görüntüyü görebilirsiniz.

![Docker Push komutundan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

**Şekil 4-50**. Push komutundan konsol çıktısı.

Çok Kapsayıcılı uygulamanızı AKS kümenize dağıtmak için, `.yaml` ve dosyalarından alınan özelliklerin büyük bir bölümü olan bazı bildirim dosyalarına ihtiyacınız vardır `docker-compose.yml` `docker-compose.override.yml` .

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> Önceki `.yml` dosyalar, `HTTP` `ASPNETCORE_URLS` örnek uygulamadaki eksik sertifikayla ilgili sorunları önlemek için, yalnızca parametresini kullanarak bağlantı noktalarını etkinleştirir.

> [!TIP]
> Bu kılavuzda [**Azure Kubernetes Service 'e (aks) dağıtım**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için aks kümesini nasıl oluşturacağınız hakkında bilgi alabilirsiniz.

Artık, **kubectl**kullanarak dağıtıma hazırsınız, ancak ilk olarak aks kümesindeki kimlik bilgilerini şu komutla almalısınız:

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Yukarıdaki komuttan konsol çıkışı: "keşfet-Docker-aks" değerini C:\users\mıguel.exe Kube\config içinde geçerli bağlam olarak birleştirildi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

**Şekil 4-51**. AKS 'ten kubectl ortamına kimlik bilgileri alma.

Ayrıca, AKS kümesinin bu komutu kullanarak ACR 'den görüntü çekmesine de izin vermeniz gerekir:

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

Önceki komutun tamamlanması birkaç dakika sürebilir. Ardından, `kubectl apply` dağıtımları başlatmak için komutunu kullanın ve ardından `kubectl get all` küme nesnelerini listeleyin.

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Yukarıdaki komutlardan konsol çıkışı: dağıtımlar uygulandı. Hizmetler oluşturuldu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

**Şekil 4-52**. Kubernetes 'e dağıtım

Yük dengeleyici dış IP 'yi alıncaya kadar beklemeniz gerekir, ile kontrol edin `kubectl get services` ve ardından sonraki görüntüde gösterildiği gibi uygulamanın o adreste kullanılabilir olması gerekir:

![AKS 'e dağıtılan uygulamanın tarayıcı görünümü](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

**Şekil 4-53**. Kubernetes 'e dağıtım

Dağıtım tamamlandığında, bir SSH tüneli kullanarak [Kubernetes Web Kullanıcı arabirimine](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) yerel bir ara sunucu ile erişebilirsiniz.

Önce aşağıdaki komutla bir ClusterRoleBinding oluşturmanız gerekir:

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

Ardından, proxy 'yi başlatmak için şu komutu kullanabilirsiniz:

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

Bir tarayıcı penceresi `http://127.0.0.1:8001` Şuna benzer bir görünümle birlikte açılmalıdır:

![Dağıtım, dizin, çoğaltma kümesi ve hizmet gösteren Kubernetes panosunun tarayıcı görünümü.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

**Şekil 4-54**. Kubernetes kümesi bilgilerini görüntüle

Artık ASP.NET Core uygulamanız var, Linux kapsayıcılarında çalışıyor ve Azure 'da bir AKS kümesine dağıtıldı.

> [!NOTE]
> Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

> [!div class="step-by-step"]
> [Önceki](set-up-windows-containers-with-powershell.md) 
>  [Sonraki](../docker-devops-workflow/index.md)
