---
title: AKS/Kubernetes kümeler halinde Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.2 uygulamalar oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: 28d2f557e4434ef7e5c2c3f8d17d6d3d6a80ce2a
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452779"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Linux kapsayıcıları olarak dağıtılan bir AKS/Kubernetes orchestrator içinde ASP.NET Core 2.2 uygulamalar oluşturun

Azure Kubernetes Hizmetleri (AKS), kapsayıcı dağıtımı ve Yönetimi basitleştirin Azure'nın yönetilen Kubernetes düzenlemeleri hizmetleridir.

AKS ana özellikleri şunlardır:

- Azure'da barındırılan denetim düzlemi
- Otomatik yükseltme
- Kendi kendine iyileştirme
- Kullanıcı yapılandırılabilir ölçeklendirme
- Hem geliştiriciler hem de küme operatörleri için basit bir kullanıcı deneyimi.

Aşağıdaki örnekler, Linux üzerinde çalışan ve geliştirme işlemi sırasında bir AKS kümesi, azure'da dağıtır bir ASP.NET Core 2.2 uygulama oluşturulmasını keşfedin. Visual Studio 2017'yi kullanarak.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Visual Studio 2017'yi kullanarak ASP.NET Core 2.2 projesi oluşturma

ASP.NET Core, Microsoft ve GitHub üzerinde .NET topluluk tarafından korunan bir genel amaçlı bir geliştirme platformudur. Bu Windows, macOS ve Linux'ta destekleyen platformlar arası ve cihaz, Bulut ve katıştırılmış IOT senaryoları için kullanılabilir.

Bu örnek, örnek oluşturmak için ek bilgisine ihtiyacınız yoktur, bir Visual Studio Web API şablonu temel alan basit bir proje kullanır. Bir ASP.NET Core 2.2 teknolojisini kullanarak REST API'sini küçük bir proje çalıştırmak için tüm öğeleri içeren bir standart şablonu kullanarak proje oluşturmak yeterlidir.

![Yeni Proje penceresinin Visual Studio kullanarak ASP.NET Core Web uygulaması seçme ekleyin.](media/create-aspnet-core-application.png)

**Şekil 4-36**. ASP.NET Core uygulaması oluşturma

Visual Studio'da örnek proje oluşturmak için seçin **dosya** > **yeni** > **proje**seçin **Web**proje türleri ardından sol bölmedeki **ASP.NET Core Web uygulaması**.

Visual Studio web projeleri için şablonları listeler. Bizim örneğimizde, seçin **API** bir ASP.NET Web API uygulaması oluşturmak için.

Çerçeve ASP.NET Core 2.2 seçtiğinizden emin olun. .NET core 2.2 en son Visual Studio 2017 sürümünde bulunan ve otomatik olarak yüklenir ve Visual Studio 2017'yi yüklediğinizde sizin için yapılandırılır.

![API seçeneği belirlenmiş bir ASP.NET Core Web uygulaması türünü seçmek için visual Studio iletişim.](media/create-web-api-application.png)

**Şekil 4-37**. ASP.NET CORE 2.2 seçme ve Web API proje türü

.NET Core herhangi bir önceki sürümü varsa, indirin ve yükleyin 2.2 sürümünden <https://www.microsoft.com/net/download/core#/sdk>.

Docker desteği projeyi oluştururken ekleyebilir veya daha sonra bu nedenle, "projenizin herhangi bir zamanda docker kapsayıcılarında çalıştırın". Proje oluşturulduktan sonra Docker desteği eklemek için Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **Ekle** > **Docker desteği** bağlam menüsünde.

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: (Proje) sağ tıklayın > Ekle > Docker desteği.](media/add-docker-support-to-project.png)

**Şekil 4-38**. Var olan bir projeye Docker desteği ekleme

Docker destek eklemeyi tamamlamak için Windows veya Linux seçebilirsiniz. Bu örnekte **Linux**, çünkü AKS Windows kapsayıcıları (olarak, geç 2018) desteklemez.

![Hedef işletim sistemi için bir Dockerfile seçin iletişim seçeneği.](media/select-linux-docker-support.png)

**Şekil 4-39**. Linux kapsayıcıları seçme.

Bu basit adımları uygulayarak bir Linux kapsayıcısı üzerinde çalışan ASP.NET Core 2.2 uygulamanızı sahip.

Gördüğünüz gibi Visual Studio 2017 ile Docker arasında tümleştirme için geliştirici üretkenliği tamamen yönlendirilmiş demektir.

Uygulamanız ile çalıştırabileceğiniz artık **F5** kullanarak veya anahtar **Play** düğmesi.

Proje çalıştırdıktan sonra kullanarak görüntüleri listeleyebilirsiniz `docker images` komutu. Görmelisiniz `mssampleapplication` Projemizin Visual Studio 2017 ile otomatik dağıtımı tarafından oluşturulmuş görüntü.

```console
docker images
```

![Konsol docker görüntüleri komuttan çıkış ile gösterilir: Depo, etiket, görüntü kimliği, oluşturulan (tarih) ve boyutu.](media/docker-images-command.png)

**Şekil 4-40**. Docker görüntüleri görüntüleme

## <a name="register-the-solution-in-the-azure-container-registry"></a>Azure kapsayıcı kayıt defterinde çözümü

Resim gibi herhangi bir Docker kayıt defterine yükleyin [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) ya da Docker Hub, AKS kümeye, kayıt defterinden görüntüleri dağıtılacak şekilde. Bu durumda, biz görüntü Azure Container Registry'ye yükleme.

### <a name="create-the-image-in-release-mode"></a>Yayın modunda görüntüsü oluşturma

Görüntüde artık oluşturacağız **yayın** için değiştirerek modu (üretim için hazır) **yayın**gösterildiği Şekil 4-41 ve önce yaptığımız gibi uygulamayı çalıştırma.

![Yayın modunda oluşturmak için VS araç seçeneği.](media/select-release-mode.png)

**Şekil 4-41**. Sürüm modu seçme

Yürütüyorsa `docker image` komutu, oluşturulan her iki görüntüleri için bir tane göreceksiniz `debug` diğeri `release` modu.

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

Artık, görüntünün en son görüntü (sürüm görüntü) alma komutu ile etiketleyebilirsiniz:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Çalıştırdıktan sonra `docker tag` komutu, görüntülerle listesi `docker images` komut ve yeni etiket görüntüsüyle görmelisiniz.

![Docker görüntüleri komuttan çıkış konsol.](media/tagged-docker-images-list.png)

**Şekil 4-44**. Etiketli Görüntü görüntüle

### <a name="push-the-image-into-the-azure-acr"></a>Azure ACR görüntü gönderme

Azure Container Registry'ye oturum açın

```console
az acr login --name mssampleacr
```

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

Sonraki adım, AKS Kubernetes kümenize kapsayıcınızı dağıtmaktır. Bunun için bir dosyasına ihtiyacınız vardır (**.yml dosyası dağıtma**), aşağıdakileri içerir:

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
