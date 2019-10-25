---
title: WCF geliştiricileri için Kubernetes-gRPC
description: Bir Kubernetes kümesinde ASP.NET Core gRPC hizmetlerini çalıştırma.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 819c761a7a55485612b7fb0c8b392971751d8724
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846637"
---
# <a name="kubernetes"></a><span data-ttu-id="5241e-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5241e-103">Kubernetes</span></span>

<span data-ttu-id="5241e-104">Kapsayıcıları Docker konaklarında el ile çalıştırmak mümkün olsa da, güvenilir üretim sistemleri için bir kümedeki çeşitli sunucularda çalışan birden çok örneği yönetmek üzere bir kapsayıcı düzenleme motoru kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's preferable to use a Container Orchestration Engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="5241e-105">Kubernetes, Docker Sısınma ve Apache Mesos dahil çeşitli kapsayıcı düzenleme altyapıları mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5241e-105">There are various Container Orchestration Engines available, including Kubernetes, Docker Swarm and Apache Mesos.</span></span> <span data-ttu-id="5241e-106">Ancak bu altyapılardan, Kubernetes, en yaygın olarak kullanıldığından, bu bölümün odağı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5241e-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="5241e-107">Kubernetes aşağıdaki işlevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="5241e-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="5241e-108">**Zamanlama** , bir küme içindeki birden çok düğümdeki kapsayıcıları çalıştırır, kullanılabilir kaynağın dengeli kullanımını sağlar, kesintiler varsa kapsayıcıları çalışır durumda tutun ve görüntülerin yeni sürümlerine veya yeni yapılandırmalara yapılan güncelleştirmeleri idare edin.</span><span class="sxs-lookup"><span data-stu-id="5241e-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="5241e-109">**Sistem durumu denetimleri** devam eden hizmeti sağlamak için kapsayıcıları izler.</span><span class="sxs-lookup"><span data-stu-id="5241e-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="5241e-110">**DNS & hizmeti bulma** , bir küme içindeki hizmetler arasında yönlendirmeyi işler.</span><span class="sxs-lookup"><span data-stu-id="5241e-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="5241e-111">Giriş seçili Hizmetleri **dışarıdan kullanıma sunar** ve genellikle bu hizmetlerin örneklerinde yük dengelemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-111">**Ingress** exposes selected services externally, and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="5241e-112">**Kaynak yönetimi** , kapsayıcılara depolama gibi dış kaynakları ekler.</span><span class="sxs-lookup"><span data-stu-id="5241e-112">**Resource management** attaches external resources such as storage to containers.</span></span>

<span data-ttu-id="5241e-113">Bu bölümde, bir ASP.NET Core gRPC hizmetinin ve hizmeti bir Kubernetes kümesine tüketen bir Web sitesinin nasıl dağıtılacağı ayrıntılandıralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="5241e-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="5241e-114">Kullanılan örnek uygulama, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur,</span><span class="sxs-lookup"><span data-stu-id="5241e-114">The sample application used is available from on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub,</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="5241e-115">Kubernetes terminolojisi</span><span class="sxs-lookup"><span data-stu-id="5241e-115">Kubernetes terminology</span></span>

<span data-ttu-id="5241e-116">Kubernetes *istenen durum yapılandırmasını*KULLANıR: API, *pods*, *dağıtımlar* ve *Hizmetler*gibi nesneleri ve *Denetim düzlemi* , istenen durumu tüm düğümlerde uygulamayı dikkate alır.bir *kümede*.</span><span class="sxs-lookup"><span data-stu-id="5241e-116">Kubernetes uses *desired state configuration*: the API is used to describe objects such as *Pods*, *Deployments* and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="5241e-117">Bir Kubernetes kümesi, programlı olarak veya `kubectl` komut satırı aracı kullanılarak iletilebileceği *KUBERNETES API*'sini çalıştıran bir *ana* düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5241e-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which can be communicated with programmatically or using the `kubectl` command-line tool.</span></span> <span data-ttu-id="5241e-118">`kubectl`, komut satırı bağımsız değişkenleri kullanarak nesneleri oluşturabilir ve yönetebilir, ancak Kubernetes nesneleri için bildirim verilerini içeren YAML dosyalarıyla en iyi şekilde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-118">`kubectl` can create and manage objects using command-line arguments, but works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="5241e-119">Kubernetes YAML dosyaları</span><span class="sxs-lookup"><span data-stu-id="5241e-119">Kubernetes YAML files</span></span>

<span data-ttu-id="5241e-120">Her Kubernetes YAML dosyası en az üç en üst düzey özelliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-120">Every Kubernetes YAML file will have at least three top-level properties.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="5241e-121">`apiVersion` özelliği, dosyanın hangi sürümü (ve hangi API) hedeflenmiştir belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="5241e-122">`kind` özelliği, YAML 'nin gösterdiği nesne türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5241e-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="5241e-123">`metadata` özelliği, `name`, `namespace`veya `labels`gibi nesne özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5241e-123">The `metadata` property contains object properties such as `name`, `namespace`, or `labels`.</span></span>

<span data-ttu-id="5241e-124">Çoğu Kubernetes YAML dosyalarında, nesneyi oluşturmak için gereken kaynakları ve yapılandırmayı açıklayan bir `spec` bölümü de olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="5241e-125">Pod</span><span class="sxs-lookup"><span data-stu-id="5241e-125">Pods</span></span>

<span data-ttu-id="5241e-126">Pods, Kubernetes içindeki temel yürütme birimleridir.</span><span class="sxs-lookup"><span data-stu-id="5241e-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="5241e-127">Birden çok kapsayıcı çalıştırabilir, ancak aynı zamanda tek kapsayıcıları çalıştırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-127">They can run multiple containers, but are also used to run single containers.</span></span> <span data-ttu-id="5241e-128">Pod, kapsayıcı (ler) ve ağ IP adresi için gereken tüm depolama kaynaklarını da içerir.</span><span class="sxs-lookup"><span data-stu-id="5241e-128">The pod also includes any storage resources required by the container(s), and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="5241e-129">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="5241e-129">Services</span></span>

<span data-ttu-id="5241e-130">Hizmetler, Pod 'leri (veya Pod kümelerini) tanımlayan meta nesnelerdir ve küme DNS hizmetini kullanarak bir hizmet adını Pod IP adresleri kümesine eşleme gibi küme içinde bunlara erişmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-130">Services are meta-objects that describe pods (or sets of pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="5241e-131">Dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="5241e-131">Deployments</span></span>

<span data-ttu-id="5241e-132">Dağıtımlar, pods için *açıklanan durum* nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="5241e-132">Deployments are the *described state* objects for Pods.</span></span> <span data-ttu-id="5241e-133">El ile bir pod oluşturursanız, bu, sonlandırılırsa yeniden başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="5241e-133">If you create a Pod manually, when it terminates it won't be restarted.</span></span> <span data-ttu-id="5241e-134">Dağıtımlar, kümeye olan ve bu yığınların kaç kopyasının mevcut zamanda çalışıyor olduğunu bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-134">Deployments are used to tell the cluster which pods, and how many replicas of those pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="5241e-135">Diğer nesneler</span><span class="sxs-lookup"><span data-stu-id="5241e-135">Other objects</span></span>

<span data-ttu-id="5241e-136">Pods, hizmetler ve dağıtımlar en temel nesne türlerinden yalnızca üçüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5241e-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="5241e-137">Bir Kubernetes kümesi tarafından yönetilen düzinelerce daha fazla nesne türü vardır.</span><span class="sxs-lookup"><span data-stu-id="5241e-137">There are dozens of other types of object that are managed by a Kubernetes cluster.</span></span> <span data-ttu-id="5241e-138">Daha fazla bilgi için bkz. [Kubernetes kavramları](https://kubernetes.io/docs/concepts/) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5241e-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="5241e-139">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="5241e-139">Namespaces</span></span>

<span data-ttu-id="5241e-140">Kubernetes kümeleri yüzlerce veya binlerce düğüme ölçeklendirilecek şekilde tasarlanmıştır ve benzer sayıda hizmeti çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5241e-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes, and run similar numbers of services.</span></span> <span data-ttu-id="5241e-141">Nesne adlarıyla çakışıyor önlemek için ad alanları, nesneleri daha büyük uygulamaların bir parçası olarak gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="5241e-142">Kubernetes kendi hizmetleri bir `default` ad alanında çalışır.</span><span class="sxs-lookup"><span data-stu-id="5241e-142">Kubernetes own services run in a `default` namespace.</span></span> <span data-ttu-id="5241e-143">Varsayılan nesneler veya kümedeki diğer kiracılar ile ilgili potansiyel çakışıyor kaçınmak için tüm Kullanıcı nesnelerinin kendi ad alanlarında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5241e-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="5241e-144">Kubernetes 'i kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="5241e-144">Get started with Kubernetes</span></span>

<span data-ttu-id="5241e-145">Windows veya macOS için Docker Desktop çalıştırıyorsanız, Kubernetes zaten kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-145">If you're running Docker Desktop for Windows or macOS, Kubernetes is already available.</span></span> <span data-ttu-id="5241e-146">Bunu, ayarlar penceresinin Kubernetes bölümünde etkinleştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5241e-146">Just enable it in the Kubernetes section of the Settings window.</span></span>

![Docker Desktop 'ta Kubernetes 'i etkinleştirme](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="5241e-148">Linux 'ta yerel bir Kubernetes kümesi çalıştırmak için, [minikube](https://github.com/kubernetes/minikube)veya [MicroK8s](https://microk8s.io/) bölümüne [bakın.](https://snapcraft.io/)</span><span class="sxs-lookup"><span data-stu-id="5241e-148">To run a local Kubernetes cluster in Linux, look at [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="5241e-149">Kümenizin çalıştığını ve erişilebilir olduğunu denetlemek için `kubectl version` komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5241e-149">To check that your cluster is running and accessible, run the `kubectl version` command.</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="5241e-150">Bu örnekte, hem `kubectl` CLı hem de Kubernetes sunucusu 1.14.6 sürümünü çalıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="5241e-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="5241e-151">Her bir `kubectl` sürümünün sunucunun önceki ve sonraki sürümünü desteklemesi gerekir, bu nedenle `kubectl` 1,14 sunucu sürümleri 1,13 ve 1,15 ile çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5241e-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="5241e-152">Kubernetes üzerinde hizmetleri çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5241e-152">Run services on Kubernetes</span></span>

<span data-ttu-id="5241e-153">Örnek uygulamanın üç YAML dosyası içeren bir `kube` dizini vardır.</span><span class="sxs-lookup"><span data-stu-id="5241e-153">The sample application has a `kube` directory containing three YAML files.</span></span> <span data-ttu-id="5241e-154">`namespace.yml` dosyası, `stocks`özel bir ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-154">The `namespace.yml` file declares a custom namespace, `stocks`.</span></span> <span data-ttu-id="5241e-155">`stockdata.yml` dosyası, gRPC uygulaması için dağıtımı ve hizmeti bildirir ve `stockweb.yml` dosyası, gRPC hizmetini kullanan bir ASP.NET Core 3,0 MVC web uygulaması için dağıtımı ve hizmeti bildirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="5241e-156">`kubectl`bir `YAML` dosyası kullanmak için `apply -f` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5241e-156">To use a `YAML` file with `kubectl`, use the `apply -f` command.</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="5241e-157">`apply` komutu, YAML dosyasının geçerliliğini denetler ve API 'den alınan tüm hataları görüntüler, ancak bu işlem biraz zaman alabilir çünkü dosyada belirtilen tüm nesneler oluşturuluncaya kadar beklemez.</span><span class="sxs-lookup"><span data-stu-id="5241e-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created as this can take some time.</span></span> <span data-ttu-id="5241e-158">Kümedeki nesne oluşturmayı denetlemek için ilgili nesne türleriyle birlikte `kubectl get` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5241e-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="5241e-159">Ad alanı bildirimi</span><span class="sxs-lookup"><span data-stu-id="5241e-159">The namespace declaration</span></span>

<span data-ttu-id="5241e-160">Ad alanı bildirimi basittir ve yalnızca bir `name` atanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-160">Namespace declaration is simple and requires only assigning a `name`.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="5241e-161">`namespace.yml` dosyasını uygulamak ve ad alanının başarıyla oluşturulduğunu denetlemek için `kubectl` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5241e-161">Use `kubectl` to apply the `namespace.yml` file and check the namespace is created successfully.</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="5241e-162">StockData uygulaması</span><span class="sxs-lookup"><span data-stu-id="5241e-162">The StockData application</span></span>

<span data-ttu-id="5241e-163">`stockdata.yml` dosyası iki nesne bildirir: bir dağıtım ve bir hizmet.</span><span class="sxs-lookup"><span data-stu-id="5241e-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="5241e-164">StockData dağıtımı</span><span class="sxs-lookup"><span data-stu-id="5241e-164">The StockData Deployment</span></span>

<span data-ttu-id="5241e-165">Dağıtım bölümü, gereken kopyaların sayısı ve dağıtım tarafından oluşturulup yönetilecek Pod nesnelerinin bir `template` dahil olmak üzere dağıtımın kendisi için `spec` sağlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-165">The Deployment part provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="5241e-166">Dağıtım nesnelerinin, ana Kubernetes API 'SI yerine `apiVersion` belirtilen `apps` API 'siyle yönetildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5241e-166">Note that Deployment objects are managed with the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

<span data-ttu-id="5241e-167">`spec.selector` özelliği, çalışan pods 'yi dağıtıma eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="5241e-168">Pod 'un `metadata.labels` özelliği `matchLabels` özelliğiyle eşleşmelidir veya API çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="5241e-169">`template.spec` bölümü kapsayıcıyı çalıştırılacak şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="5241e-170">Docker Desktop tarafından sağlandıkları gibi yerel bir Kubernetes kümesiyle çalışırken, bir sürüm etiketi olduğu sürece yerel olarak oluşturulan görüntüleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5241e-170">When working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5241e-171">Varsayılan olarak, Kubernetes her zaman yeni bir görüntü çekmeyi ve çekmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="5241e-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="5241e-172">Görüntüyü bilinen depolarından hiçbirinde bulamazsa Pod oluşturma işlemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="5241e-173">Yerel görüntülerle çalışmak için `imagePullPolicy` `Never` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5241e-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="5241e-174">`ports` özelliği, pod üzerinde hangi kapsayıcı bağlantı noktalarının yayımlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5241e-174">The `ports` property specifies which container ports should be published on the Pod.</span></span>  <span data-ttu-id="5241e-175">`stockservice` görüntüsü, hizmeti standart HTTP bağlantı noktasında çalıştırır, bu nedenle bağlantı noktası 80 yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="5241e-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="5241e-176">`resources` bölümü, Pod içinde çalışan kapsayıcıya kaynak sınırları uygular.</span><span class="sxs-lookup"><span data-stu-id="5241e-176">The `resources` section applies resource limits to the container running within the pod.</span></span> <span data-ttu-id="5241e-177">Bu, tek bir pod 'ın bir düğümdeki tüm kullanılabilir CPU veya bellek tüketmesini önlediği için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5241e-177">This is good practice as it prevents an individual pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="5241e-178">ASP.NET Core 3,0, en iyi duruma getirildi ve kaynak sınırlı kapsayıcılarda çalışacak şekilde ayarlanmıştır ve `dotnet/core/aspnet` Docker görüntüsü bir ortam değişkenini ayarlayarak `dotnet` çalışma zamanına bir kapsayıcıda olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="5241e-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers, and the `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="5241e-179">StockData hizmeti</span><span class="sxs-lookup"><span data-stu-id="5241e-179">The StockData Service</span></span>

<span data-ttu-id="5241e-180">YAML dosyasının hizmet bölümü, küme içindeki yığınlara erişim sağlayan hizmeti bildirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-180">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="5241e-181">Service spec, çalışan `Pods` eşleştirmek için `selector` özelliğini kullanır, bu durumda bir etiket `run: stockdata` olan pods 'yi arıyor.</span><span class="sxs-lookup"><span data-stu-id="5241e-181">The Service spec uses the `selector` property to match running `Pods`, in this case looking for Pods with a label `run: stockdata`.</span></span> <span data-ttu-id="5241e-182">Eşleşen FID 'ler üzerinde belirtilen `port`, adlandırılmış hizmet tarafından yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-182">The specified `port` on matching Pods are published by the named service.</span></span> <span data-ttu-id="5241e-183">`stocks` ad alanında çalışan diğer pods 'Ler, bu hizmette bulunan HTTP 'ye adres olarak `http://stockdata` kullanarak erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-183">Other Pods running in the `stocks` namespace can access HTTP on this service using `http://stockdata` as the address.</span></span> <span data-ttu-id="5241e-184">Diğer ad alanlarında çalışan pods `http://stockdata.stocks` ana bilgisayar adını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-184">Pods running in other namespaces can use the `http://stockdata.stocks` hostname.</span></span> <span data-ttu-id="5241e-185">[Ağ ilkelerini](https://kubernetes.io/docs/concepts/services-networking/network-policies/)kullanarak, siteler arası hizmet erişimini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5241e-185">You can control cross-namespace service access using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="5241e-186">StockData uygulamasını dağıtma</span><span class="sxs-lookup"><span data-stu-id="5241e-186">Deploy the StockData application</span></span>

<span data-ttu-id="5241e-187">`stockdata.yml` dosyasını uygulamak ve dağıtım ve hizmetin oluşturulduğunu denetlemek için `kubectl` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5241e-187">Use `kubectl` to apply the `stockdata.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="5241e-188">StockWeb uygulaması</span><span class="sxs-lookup"><span data-stu-id="5241e-188">The StockWeb application</span></span>

<span data-ttu-id="5241e-189">`stockweb.yml` dosyası, MVC uygulaması için dağıtımı ve hizmeti bildirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-189">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="5241e-190">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5241e-190">Environment variables</span></span>

<span data-ttu-id="5241e-191">Dağıtım nesnesinin `env` bölümü, `stockweb:1.0.0` görüntülerini çalıştıran kapsayıcıda ayarlanacak ortam değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5241e-191">The `env` section of the Deployment object specifies environment variables to be set in the container running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="5241e-192">**`StockData__Address`** ortam değişkeni, EnvironmentVariables yapılandırma sağlayıcısı için teşekkürler `StockData:Address` yapılandırma ayarıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="5241e-192">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="5241e-193">Bu ayar, adlar arasında ayrı bölümlere iki alt çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-193">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="5241e-194">Adres, aynı Kubernetes ad alanında çalışan `stockdata` hizmetinin hizmet adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-194">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="5241e-195">**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** ortam değişkeni <xref:System.Net.Http.HttpClient>IÇIN şifrelenmemiş HTTP/2 bağlantılarına izin veren bir <xref:System.AppContext> anahtarı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-195">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="5241e-196">Bu ortam değişkeni, burada gösterildiği gibi, kodda anahtarı ayarlamanın eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="5241e-196">This environment variable is the equivalent of setting the switch in code as shown here.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="5241e-197">Anahtar için bir ortam değişkeni kullanmak, ayarın uygulamanın çalıştığı bağlama göre kolayca değiştirilebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5241e-197">Using an environment variable for the switch means the setting can easily be changed depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="5241e-198">Hizmet türleri</span><span class="sxs-lookup"><span data-stu-id="5241e-198">Service types</span></span>

<span data-ttu-id="5241e-199">Web uygulamasını küme dışından erişilebilir hale getirmek için `type: NodePort` özelliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-199">To make the Web application accessible from outside the cluster, the `type: NodePort` property is used.</span></span> <span data-ttu-id="5241e-200">Bu özellik türü, Kubernetes 'in hizmette bağlantı noktası 80 ' i kümenin dış ağ yuvaları üzerinde rastgele bir bağlantı noktasına yayımlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-200">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="5241e-201">Atanan bağlantı noktası `kubectl get service` komutu kullanılarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-201">The port assigned can be found using the `kubectl get service` command.</span></span>

<span data-ttu-id="5241e-202">`stockdata` hizmetine küme dışından erişilememelidir, bu nedenle varsayılan tür olan `ClusterIP`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-202">The `stockdata` service shouldn't be accessible from outside the cluster, so it used the default type, `ClusterIP`.</span></span>

<span data-ttu-id="5241e-203">Üretim sistemleri, ortak uygulamaları dış tüketicilere sunmak için büyük olasılıkla tümleşik bir yük dengeleyici kullanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-203">Production systems will most likely use an integrated load-balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="5241e-204">Bu şekilde sunulan hizmetler `LoadBalancer` türünü kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5241e-204">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="5241e-205">Hizmet türleri hakkında daha fazla bilgi için bkz. [Kubernetes yayımlama hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5241e-205">For more information on service types, see the [Kubernetes' Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="5241e-206">StockWeb uygulamasını dağıtma</span><span class="sxs-lookup"><span data-stu-id="5241e-206">Deploy the StockWeb application</span></span>

<span data-ttu-id="5241e-207">`stockweb.yml` dosyasını uygulamak ve dağıtım ve hizmetin oluşturulduğunu denetlemek için `kubectl` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5241e-207">Use `kubectl` to apply the `stockweb.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="5241e-208">`get service` komutunun çıktısı, HTTP bağlantı noktasının dış ağdaki `32564` bağlantı noktasına yayımlandığını gösterir; Docker Desktop için bu, localhost olur.</span><span class="sxs-lookup"><span data-stu-id="5241e-208">The output from the `get service` command shows that the HTTP port has been published to port `32564` on the external network; for Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="5241e-209">Uygulamaya `http://localhost:32564` göz atarak uygulamaya erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5241e-209">The application can be accessed by browsing to `http://localhost:32564`.</span></span>

### <a name="testing-the-application"></a><span data-ttu-id="5241e-210">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="5241e-210">Testing the application</span></span>

<span data-ttu-id="5241e-211">StockWeb uygulaması, basit bir istek-yanıt hizmetinden alınan NASDAQ hisse senetleri listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5241e-211">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="5241e-212">Tanıtım amacıyla her satırda Ayrıca döndürülen hizmet örneğinin benzersiz KIMLIĞI gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-212">For demonstration purposes, each line also shows the unique ID of the service instance that returned it.</span></span>

![StockWeb ekran görüntüsü](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="5241e-214">`stockdata` hizmetinin çoğaltmalarının sayısı artdıysa, **sunucu** değerinin satırdan satıra değiştirilmesini bekleyebilir, ancak aslında tüm 100 kayıtları aynı örnekten döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5241e-214">If the number of replicas of the `stockdata` service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="5241e-215">Sayfayı birkaç saniyede bir kez yenilerseniz, sunucu KIMLIĞI aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="5241e-215">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="5241e-216">Bunun nedeni nedir?</span><span class="sxs-lookup"><span data-stu-id="5241e-216">Why does this happen?</span></span> <span data-ttu-id="5241e-217">Burada çalmak için iki etken vardır.</span><span class="sxs-lookup"><span data-stu-id="5241e-217">There are two factors at play here.</span></span>

<span data-ttu-id="5241e-218">İlk olarak, Kubernetes hizmeti bulma sistemi varsayılan olarak "hepsini bir kez deneme" yük dengelemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-218">First, the Kubernetes service discovery system uses "round-robin" load-balancing by default.</span></span> <span data-ttu-id="5241e-219">DNS sunucusu ilk kez sorgulandığında, hizmet için ilk eşleşen IP adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5241e-219">The first time the DNS server is queried, it will return the first matching IP address for the service.</span></span> <span data-ttu-id="5241e-220">Sonraki sefer, listedeki bir sonraki IP adresi ve bu şekilde, sonuna kadar, başlangıç noktasına geri döngü.</span><span class="sxs-lookup"><span data-stu-id="5241e-220">The next time, the next IP address in the list, and so on, until the end, at which point it loops back to the start.</span></span>

<span data-ttu-id="5241e-221">İkincisi, StockWeb uygulamasının gRPC istemcisi için kullanılan `HttpClient`, [HttpClientFactory ASP.NET Core](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)tarafından oluşturulup yönetilir ve bu istemcinin tek bir örneği, sayfaya yapılan her çağrı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-221">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="5241e-222">İstemci yalnızca bir DNS araması yapar, bu nedenle tüm istekler aynı IP adresine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-222">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="5241e-223">Ayrıca, `HttpClientHandler` performans nedenleriyle önbelleğe alındığından, önbelleğe alınan DNS girişinin süresi dolana veya işleyici örneği bazı nedenlerle atılana kadar, hızlı bir şekilde art arda birden çok istek aynı IP *adresini kullanacaktır.*</span><span class="sxs-lookup"><span data-stu-id="5241e-223">Furthermore, because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="5241e-224">Bu, varsayılan olarak bir gRPC hizmetine yapılan isteklerin kümedeki hizmetin tüm örneklerine dengelenmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5241e-224">This means that by default requests to a gRPC service aren't balanced across all instances of that service in the cluster.</span></span> <span data-ttu-id="5241e-225">Farklı tüketiciler farklı örnekler kullanacaktır, ancak isteklerin iyi bir şekilde dağıtılmasını ve kaynakların dengeli kullanımını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="5241e-225">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests and a balanced use of resources.</span></span>

<span data-ttu-id="5241e-226">Sonraki bölümde, [hizmet kafesleri](service-mesh.md)bu sorunun nasıl ele alınacağını arayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5241e-226">The next chapter, [Service Meshes](service-mesh.md), will look at how to address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5241e-227">[Önceki](docker.md)
>[İleri](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="5241e-227">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
