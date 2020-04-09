---
title: Linux konteynerolarak AKS/Kubernetes kümelerine dağıtılan core 2.2 ASP.NET uygulamaları oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/25/2019
ms.openlocfilehash: 83d4d0a60db4bdc112bb35bfbf61c0396646ad31
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989031"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Linux konteynerolarak dağıtılan ASP.NET Core 2.2 uygulamalarını AKS/Kubernetes orkestratörüne dönüştürün

Azure Kubernetes Services (AKS), Azure'un konteyner dağıtımını ve yönetimini basitleştiren yönetilen Kubernetes orkestrasyon hizmetleridir.

AKS'nin başlıca özellikleri şunlardır:

- Azure tarafından barındırılan bir denetim düzlemi
- Otomatik yükseltmeler
- Kendi kendini iyileştirme
- Kullanıcı yapılandırılabilir ölçekleme
- Hem geliştiriciler hem de küme işleçleri için daha basit bir kullanıcı deneyimi.

Aşağıdaki örnekler, Linux üzerinde çalışan ve Azure'da bir AKS Cluster'a dağıtılan bir ASP.NET Core 2.2 uygulamasının oluşturulmasını incelerken, geliştirme Visual Studio 2017 kullanılarak yapılır.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Visual Studio 2017'yi kullanarak ASP.NET Core 2.2 Projesi Oluşturma

ASP.NET Core, Microsoft ve GitHub'daki .NET topluluğu tarafından korunan genel amaçlı bir geliştirme platformudur. Windows, macOS ve Linux'u destekleyen çapraz platformdur ve aygıt, bulut ve gömülü/IoT senaryolarında kullanılabilir.

Bu örnek, Visual Studio Web API şablonuna dayanan basit bir proje kullanır, böylece örneği oluşturmak için ek bilgiye ihtiyacınız olmaz. Yalnızca, Core 2.2 teknolojisini kullanarak REST API'li küçük bir projeyi çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak proje ASP.NETyi oluşturmanız gerekir.

![Visual Studio'da core web uygulamasını ASP.NET seçerek yeni proje penceresi ekleyin.](media/create-aspnet-core-application.png)

**Şekil 4-36**. ASP.NET Çekirdek Uygulama Oluşturma

Visual Studio'da örnek proje oluşturmak **için, Dosya** > **Yeni** > **Proje'yi**seçin, sol bölmedeki **Web** proje türlerini seçin ve ardından ASP.NET Çekirdek **Web Uygulaması.**

Visual Studio, web projeleri için şablonları listeler. Örneğin, ASP.NET bir Web API Uygulaması oluşturmak için **API'yi** seçin.

Çerçeve olarak Core 2.2ASP.NET seçtiğinizi doğrulayın. .NET Core 2.2, Visual Studio 2017'nin son sürümüne dahildir ve Visual Studio 2017'yi yüklediğinizde otomatik olarak yüklenir ve sizin için yapılandırılır.

![API seçeneği seçili bir ASP.NET Çekirdek Web Uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/create-web-api-application.png)

**Şekil 4-37.** CORE 2.2 ve Web API proje türü ASP.NET seçme

.NET Core'un önceki bir sürümünüz varsa, 2.2 sürümünü <https://dotnet.microsoft.com/download>'den indirebilir ve yükleyebilirsiniz.

Projeyi oluştururken veya sonrasında Docker desteği ekleyebilirsiniz, böylece projenizi istediğiniz zaman "Dockerize" edebilirsiniz. Proje oluşturulduktan sonra Docker desteği eklemek için Solution Explorer'daki proje düğümüne sağ tıklayın ve bağlam menüsünde**Docker ekle desteğini** seçin. **Add** > 

![Varolan bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: Sağ tıklayın (projeye) > > Docker Desteği ekleyin.](media/add-docker-support-to-project.png)

**Şekil 4-38**. Mevcut projeye Docker desteği ekleme

Docker desteğini eklemeyi tamamlamak için Windows veya Linux'u seçebilirsiniz. Bu durumda, AKS Windows Kapsayıcılarını desteklemediği için (2018 sonu itibariyle) **Linux'u**seçin.

![Dockerfile için Hedef İşletim Sistemi'ni seçmek için seçenek iletişim kutusu.](media/select-linux-docker-support.png)

**Şekil 4-39**. Linux kapsayıcıları seçme.

Bu basit adımlarla, ASP.NET Core 2.2 uygulamanız bir Linux kapsayıcısı üzerinde çalışır.

Gördüğünüz gibi Visual Studio 2017 ve Docker arasındaki entegrasyon tamamen geliştiricinin üretkenliğine odaklıdır.

Artık **f5** tuşu ile veya **Oynat** düğmesini kullanarak uygulamanızı çalıştırabilirsiniz.

Projeyi çalıştırdıktan sonra, komutu `docker images` kullanarak görüntüleri listeleyebilirsiniz. Visual Studio `mssampleapplication` 2017 ile projemizin otomatik olarak dağıtılmasıyla oluşturulan görüntüyü görmelisiniz.

```console
docker images
```

![Docker images komutundan konsol çıkışı, bir liste gösterir: Depo, Etiket, Resim Kimliği, Oluşturulan (tarih) ve Boyut.](media/docker-images-command.png)

**Şekil 4-40.** Docker görüntülerini görüntüle

## <a name="register-the-solution-in-the-azure-container-registry"></a>Çözümü Azure Konteyner Kayıt Defterine Kaydedin

Görüntülerin söz kayıt defterinden AKS kümesine dağıtılaabilmesi için resmi [Azure Konteyner Kayıt Defteri (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker Hub gibi herhangi bir Docker kayıt defterine yükleyin. Bu durumda, resmi Azure Kapsayıcı Kayıt Defteri'ne yüklüyoruz.

### <a name="create-the-image-in-release-mode"></a>Görüntüyü Yayın modunda oluşturma

Şimdi, Şekil 4-41'de gösterildiği gibi **Release** **Release**(üretime hazır) görüntü oluşturacağız ve uygulamayı daha önce yaptığımız gibi çalıştıracağız.

![Sürüm modunda oluşturmak için VS araç çubuğu seçeneği.](media/select-release-mode.png)

**Şekil 4-41.** Serbest Bırakma Modu'nu Seçme

Komutu `docker image` çalıştırırsanız, biri için diğeri mod `debug` için `release` olmak üzere her iki görüntünün oluşturulduğunu görürsünüz.

### <a name="create-a-new-tag-for-the-image"></a>Resim için yeni bir Etiket Oluşturma

Her kapsayıcı görüntüsünün kayıt `loginServer` defterinin adıyla etiketlenmiş olması gerekir. Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderilirken kullanılır.

Azure Konteyner `loginServer` Kayıt Defteri'nden bilgileri alarak adı Azure portalından görüntüleyebilirsiniz

![Sağ üstteki Azure kapsayıcı kayıt defteri adının tarayıcı görünümü.](media/loginServer-name.png)

**Şekil 4-42**. Kayıt Defterinin adının görünümü

Veya aşağıdaki komutu çalıştırarak:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıkışı.](media/az-cli-loginServer-name.png)

**Şekil 4-43**. PowerShell'i kullanarak kayıt defterinin adını alın

Her iki durumda da, adı alırsınız. Bizim örneğimizde, `mssampleacr.azurecr.io`.

Şimdi en son görüntüyü (Yayın görüntüsü) komutuyla alarak görüntüyü etiketleyebilirsiniz:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Komutu `docker tag` çalıştırdıktan sonra, görüntüleri `docker images` komutla listeleyin ve yeni etiketle görüntüyü görmeniz gerekir.

![Docker images komutundan konsol çıkışı.](media/tagged-docker-images-list.png)

**Şekil 4-44.** Etiketli resimlerin görünümü

### <a name="push-the-image-into-the-azure-acr"></a>Görüntüyü Azure ACR'ye itin

Azure Konteyner Kayıt Defteri'nde oturum açın

```console
az acr login --name mssampleacr
```

Aşağıdaki komutu kullanarak görüntüyü Azure ACR'ye itin:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Bu komut görüntüleri yüklemek biraz zaman alır, ancak işlem sırasında geribildirim verir.

![Docker push komutundan konsol çıkışı: her katman için karakter tabanlı bir ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

**Şekil 4-45.** Görüntüyü ACR'ye yükleme

İşlem tamamlandığında elde ediletmeniz gereken sonucu aşağıda görebilirsiniz:

![Docker push komutundan konsol çıkışı, tüm katmanları veya düğümleri gösteren tamamlandı.](media/uploading-docker-images-complete.png)

**Şekil 4-46.** Düğümlerin görünümü

Bir sonraki adım, kapsayıcınızı AKS Kubernetes kümenize dağıtmaktır. Bunun için aşağıdakileri içeren bir dosyaya **(.yml dağıtım dosyası)** ihtiyacınız vardır:

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Şimdi **kubectl**kullanarak dağıtmak için neredeyse hazırsınız, ama önce bu komutile AKS Cluster kimlik bilgilerini almak gerekir:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Yukarıdaki komuttan konsol çıkışı: Birleştirilmiş "MSSampleK8Cluster /root/.kube/config'deki geçerli bağlam olarak](media/getting-aks-credentials.png)

**Şekil 4-47.** kimlik bilgileri alma

Ardından, dağıtımı `kubectl create` başlatmak için komutu kullanın.

```console
kubectl create -f mssample-deploy.yml
```

![Yukarıdaki komuttan konsol çıkışı: dağıtım "mssamplesbook" oluşturuldu. hizmet "mssample-kub-app" oluşturuldu.](media/kubectl-create-command.png)

**Şekil 4-48**. Kubernetes’e dağıtma

Dağıtım tamamlandığında, kubernetes konsoluna bu komutla zamansal olarak erişebileceğiniz yerel bir proxy ile erişebilirsiniz:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

Ve url `http://127.0.0.1:8001`erişim .

![Dağıtımları, Bölmeleri, Çoğaltma Kümelerini ve Hizmetleri gösteren Kubernetes panosunun tarayıcı görünümü.](media/kubernetes-cluster-information.png)

**Şekil 4-49**. Kubernetes küme bilgilerini görüntüleme

Artık uygulamanızı Bir Linux Kapsayıcısı ve bir AKS Kubernetes Kümesi kullanarak Azure'da dağıttınız. Azure portalından alabileceğiniz uygulamanızın genel IP'sine erişebilirsiniz.

> [!NOTE]
> Bu kılavuzda [**Azure Kubernetes Hizmetine (AKS) dağıt**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için AKS Kümesi'nin nasıl oluşturulabileceğini görebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](set-up-windows-containers-with-powershell.md)
>[Sonraki](../docker-devops-workflow/index.md)
