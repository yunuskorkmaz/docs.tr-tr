---
title: AKS/Kubernetes kümeler halinde Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.1 uygulamaları oluşturun
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b03b6fab9dcd53e97c2bc4d7e5c958ca4b931077
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221402"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a>AKS/Kubernetes orchestrator Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.1 uygulamaları oluşturun

Azure Kubernetes Hizmetleri (AKS), kapsayıcı dağıtımı ve Yönetimi basitleştirin Azure'nın yönetilen Kubernetes düzenlemeleri hizmetleridir.

AKS ana özellikleri şunlardır:

- Azure'da barındırılan denetim düzlemi
- Otomatik yükseltme
- Kendi kendine iyileştirme
- Kullanıcı yapılandırılabilir ölçeklendirme
- Hem geliştiriciler hem de küme operatörleri için basit bir kullanıcı deneyimi.

Aşağıdaki örnekte bir AKS kümesi, azure'da geliştirme yapıldığı sırada dağıtır ve Linux üzerinde çalışan bir ASP.NET Core 2.1 uygulama oluşturulmasını keşfedin Visual Studio 2017'yi kullanarak.

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>Visual Studio 2017'yi kullanarak ASP.NET Core 2.1 projesi oluşturma

ASP.NET Core, Microsoft ve GitHub üzerinde .NET topluluk tarafından korunan bir genel amaçlı bir geliştirme platformudur. Bu Windows, macOS ve Linux'ta destekleyen platformlar arası ve cihaz, Bulut ve katıştırılmış IOT senaryoları için kullanılabilir.

Bu örnek, örnek oluşturmak için ek bilgisine ihtiyacınız yoktur, bir Visual Studio Web API şablonuna dayanan dayalı basit bir projesi kullanır. Bir ASP.NET Core 2.1 teknolojisini kullanarak REST API'sini küçük bir proje çalıştırmak için tüm öğeleri içeren bir standart şablonu kullanarak proje oluşturmak yeterlidir.

![Yeni Proje penceresinin Visual Studio kullanarak ASP.NET Core Web uygulaması seçme ekleyin.](media/create-aspnet-core-application.png)

**Şekil 4-36**. ASP.NET Core uygulaması oluşturma

Örnek proje oluşturmak için Seç sahip **dosya** > **yeni** > **proje** Visual Studio'da. Aranacak sahip olduğu bir proje, çeşitli türleri için şablonlar listesi görürsünüz sonra **Web** > **.NET Core** Sol paneldeki. Bu örnek için select **ASP.NET Core Web uygulaması**.

Sonraki iletişim kutusunda, .NET Core ve ASP.NET Core 2.1 hedef çerçeve Şekil 4-37 gösterilen üst pulldowns olarak seçtiniz ve ASP.NET Core Web API uygulaması oluşturmak için API seçeneğini seçip emin olun.

.NET Core 2.1 dahil Visual Studio 2017 sürüm 15.7.0 ya da daha büyük ve otomatik olarak yüklenir ve seçtiğiniz sizin için yapılandırılır **.NET Core çoklu platform geliştirme** yüklemesi sırasında iş yükü.

![API seçeneği belirlenmiş bir ASP.NET Core Web uygulaması türünü seçmek için visual Studio iletişim.](media/create-web-api-application.png)

**Şekil 4-37**. ASP.NET CORE 2.1 seçme ve Web API proje türü

.NET Core herhangi bir önceki sürümü varsa, indirin ve 2.1 sürümü <https://www.microsoft.com/net/download/core#/sdk>.

Önceki adımda ya da daha sonra projeyi başlattıktan sonra gerekirse projesi oluşturduğunuz sırada, Docker desteği ekleyebilirsiniz. Proje oluşturulduktan sonra Docker desteğini eklemesi için proje dosyasında sağ **Çözüm Gezgini** seçip **Ekle** > **Docker desteği** üzerinde bağlam menüsü.

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: (Proje) sağ tıklayın > Ekle > Docker desteği.](media/add-docker-support-to-project.png)

**Şekil 4-38**. Var olan bir projeye Docker desteği ekleme

Docker destek eklemeyi tamamlamak için Windows veya Linux seçebilirsiniz. Bu örnekte **Linux**, çünkü AKS Windows kapsayıcıları (olarak, geç 2018) desteklemez.

![Hedef işletim sistemi için bir Dockerfile seçin iletişim seçeneği.](media/select-linux-docker-support.png)

**Şekil 4-39**. Linux kapsayıcıları seçme.

Bu basit adımları uygulayarak bir Linux kapsayıcısı üzerinde çalışan ASP.NET Core 2.1 uygulamanız gerekir.

Gördüğünüz gibi Visual Studio 2017 ile Docker arasında tümleştirme için geliştirici üretkenliği tamamen yönlendirilmiş demektir.

Basabilirsiniz artık **F5** oluşturup çalıştırın.

Proje çalıştırdıktan sonra kullanarak görüntüleri listeleyebilirsiniz `docker images` komutu. Görmelisiniz `mssampleapplication` otomatik dağıtma, projenin Visual Studio 2017 ile oluşturulan görüntü.

```console
docker images
```

![Konsol docker görüntüleri komuttan çıkış ile gösterilir: Depo, etiket, görüntü kimliği, oluşturulan (tarih) ve boyutu.](media/docker-images-command.png)

**Şekil 4-40**. Docker görüntüleri görüntüleme

## <a name="register-the-solution-in-the-azure-container-registry"></a>Azure kapsayıcı kayıt defterinde çözümü

Resim gibi herhangi bir Docker kayıt defterine yükleyin [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker hub'ı AKS kümeye, kayıt defterinden görüntüleri dağıtılacak şekilde. Bu durumda, biz görüntü Azure Container Registry'ye yükleme.

### <a name="create-the-image-in-release-mode"></a>Yayın modunda görüntüsü oluşturma

Görüntüyü oluşturmak **yayın** burada gösterildiği gibi sürümüne (üretim için hazır) modunu değiştirme ve uygulamayı yeniden çalıştırmak için F5 tuşuna basın.

![Yayın modunda oluşturmak için VS araç seçeneği.](media/select-release-mode.png)

**Şekil 4-41**. Sürüm modu seçme

Yürütüyorsa `docker image` komutu, oluşturulan her iki görüntüleri göreceksiniz. Birincisi `debug` diğeri `release` modu.

### <a name="create-a-new-tag-for-the-image"></a>Yeni bir etiket oluşturmak için görüntü

Her kapsayıcı görüntüsü ile etiketlenmesi gerekir `loginServer` kayıt defteri adı. Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderirken yönlendirme için kullanılır.

Görüntüleyebileceğiniz `loginServer` ad Azure portalı, Azure Container Registry'den bilgileri alma

![Sağ üst kısımdaki tarayıcı görünümü, Azure kapsayıcı kayıt defteri adı.](media/loginServer-name.png)

**Şekil 4-42**. Kayıt defteri adını görüntüle

Veya aşağıdaki komutu çalıştırarak:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan çıkış konsol.](media/az-cli-loginServer-name.png)

**Şekil 4-43**. PowerShell kullanarak kayıt defteri adını alın

Her iki durumda da adı elde. Bizim örneğimizde `mssampleacr.azurecr.io`.

Artık son görüntü (sürüm görüntü) aşağıdaki komutla alma görüntü etiketleyebilirsiniz:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Çalıştırdıktan sonra `docker tag` komutu, görüntülerle listesi `docker images` komutu. Yeni etiket görüntüsüyle görmeniz gerekir.

![Docker görüntüleri komuttan çıkış konsol.](media/tagged-docker-images-list.png)

**Şekil 4-44**. Etiketli Görüntü görüntüle

### <a name="push-the-image-into-the-azure-acr"></a>Azure ACR görüntü gönderme

Aşağıdaki komutu kullanarak Azure ACR görüntüyü gönderin:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Bu komut biraz uzun sürebilir. görüntü karşıya ancak işlem sırasında geri bildirim sağlar.

![Konsol çıktısı docker itme komutundan: her katman için bir karakter tabanlı bir ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

**Şekil 4-45**. Görüntüyü ACR'ye yükleme

İşlem tamamlandığında almalısınız sonucu görebilirsiniz:

![Docker push komutu, tüm katmanlar veya düğümleri gösterme, tamamlanmış çıktı Konsolu.](media/uploading-docker-images-complete.png)

**Şekil 4-46**. Düğüm görünümü

Sonraki adım, AKS Kubernetes kümenize kapsayıcınızı dağıtmaktır. Bunun için bir dosya gereksinim (**.yml dosyası dağıtma**), bu durumda, içerir:

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
        - mane: mssample-services-app
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
> Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Kullanarak dağıtmak neredeyse hazırsınız artık **Kubectl**, ancak önce bu komutu ile bir AKS kümesi için kimlik bilgilerini edinmeniz gerekir:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Konsolu, yukarıdaki komuttan çıkış: Geçerli bağlamda /root/.kube/config olarak birleştirilmiş "MSSampleK8Cluster](media/getting-aks-credentials.png)

**Şekil 4-47**. kimlik bilgilerini alma

Ardından, `kubectl create` dağıtımı başlatmak için komutu.

```console
kubectl create -f mssample-deploy.yml
```

![Konsol çıktısı yukarıdaki komutu: dağıtım "oluşturulan mssamplesbook". Hizmeti "mssample kub-oluşturduğunuz uygulama".](media/kubectl-create-command.png)

**Şekil 4-48**. Kubernetes için dağıtma

Dağıtım tamamlandığında, bu komutla zamansal olarak erişebileceğiniz bir yerel ara sunucusu ile Kubernetes konsol erişebilirsiniz:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

Ve URL'ye erişilirken `http://127.0.0.1:8001`.

![Kubernetes panosunu, dağıtımlar, pod'ları, çoğaltma kümeleri ve Hizmetleri gösteren tarayıcı görünümü.](media/kubernetes-cluster-information.png)

**Şekil 4-49**. Kubernetes küme bilgilerini görüntüleme

Artık Azure'da bir Linux kapsayıcısı ve Kubernetes AKS kümesi kullanarak, dağıtılan uygulamanız var. Uygulamanızı Azure portalından alabilirsiniz hizmetinizin genel IP için gözatma erişebilirsiniz.

> [!NOTE]
> Bu örnekte bir AKS kümesi oluşturma bölümünde görebilirsiniz [ **Dağıt Azure Kubernetes Service (AKS) için** ](deploy-azure-kubernetes-service.md) üzerinde bu kılavuzu.

>[!div class="step-by-step"]
>[Önceki](set-up-windows-containers-with-powershell.md)
>[İleri](../docker-devops-workflow/index.md)
