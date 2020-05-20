---
title: Bulutta Yerel Uygulama Paketleri
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native uygulama demeti
ms.date: 05/13/2020
ms.openlocfilehash: fc6ee96078650dccd2ebeb3e65a0a00c4e05ecdb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614350"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="983f2-103">Bulutta Yerel Uygulama Paketleri</span><span class="sxs-lookup"><span data-stu-id="983f2-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="983f2-104">Bulutta yerel uygulamaların anahtar özelliği, geliştirmeyi hızlandırmak için bulutun özelliklerinden faydalandıklarından.</span><span class="sxs-lookup"><span data-stu-id="983f2-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="983f2-105">Bu tasarım genellikle tam uygulamanın farklı teknoloji türlerini kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="983f2-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="983f2-106">Uygulamalar Docker kapsayıcılarında sevk edilebilir, ancak bazı hizmetler Azure Işlevlerini kullanabilir, ancak diğer parçalar donanım GPU hızlandırmalı büyük metal sunucularda ayrılan sanal makinelerde doğrudan çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="983f2-107">İki bulut Yerel uygulaması aynı değildir; bu nedenle, sevk etmek için tek bir mekanizma sağlamak zordur.</span><span class="sxs-lookup"><span data-stu-id="983f2-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="983f2-108">Docker kapsayıcıları, dağıtım için bir helk grafiği kullanılarak Kubernetes üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="983f2-109">Azure Işlevleri Terrayform şablonları kullanılarak ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="983f2-110">Son olarak, sanal makineler Terrayform kullanılarak ayrılabilir ancak anormal kullanılarak oluşturulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="983f2-111">Bu bir bütün teknolojiden oluşur ve bunları makul bir pakette paketetmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="983f2-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="983f2-112">Şimdi.</span><span class="sxs-lookup"><span data-stu-id="983f2-112">Until now.</span></span>

<span data-ttu-id="983f2-113">Bulut Yerel uygulama paketleri (CNABs), dağıtılmış uygulamaları paketlemeyle bir belirtim geliştirmek için Microsoft, Docker ve HashiCorp gibi topluluk tarafından yapılan bir dizi şirket tarafından sunulan bir iş malzemelidir.</span><span class="sxs-lookup"><span data-stu-id="983f2-113">Cloud Native Application Bundles (CNABs) are a joint effort by a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="983f2-114">Çaba, Aralık 2018 ' de duyuruldu. bu nedenle, daha fazla topluluğun çabasını sergilemek için bir iş gücü de daha fazla.</span><span class="sxs-lookup"><span data-stu-id="983f2-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="983f2-115">Ancak, zaten [Duffle](https://duffle.sh/)olarak bilinen [açık bir belirtim](https://github.com/deislabs/cnab-spec) ve başvuru uygulamanız vardır.</span><span class="sxs-lookup"><span data-stu-id="983f2-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="983f2-116">Go 'da yazılmış olan bu araç, Docker ve Microsoft arasındaki bir birleşme çabadır.</span><span class="sxs-lookup"><span data-stu-id="983f2-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="983f2-117">CNABs, farklı türlerde yükleme teknolojileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="983f2-118">Bu, Helm grafikleri, Terkaform şablonları ve anormal PlayBook gibi öğelerin aynı pakette yer almasına imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="983f2-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="983f2-119">Oluşturulduktan sonra paketler kendi içinde ve taşınabilir; Bu, USB Stick yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="983f2-120">Paketler, talep ettikleri taraftan kaynaklandıklarından emin olmak için şifreli olarak imzalanır.</span><span class="sxs-lookup"><span data-stu-id="983f2-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="983f2-121">CNAB 'nin çekirdeği adlı bir dosyadır `bundle.json` .</span><span class="sxs-lookup"><span data-stu-id="983f2-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="983f2-122">Bu dosya, paket içeriğini tanımlar, bu, bunlar veya resimler ya da başka bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="983f2-123">Şekil 11-9, bazı Tersform çağıran bir CNAB tanımlar.</span><span class="sxs-lookup"><span data-stu-id="983f2-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="983f2-124">Bununla birlikte, aslında Terrayform çağırmak için kullanılan bir çağırma görüntüsünü tanımladığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="983f2-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="983f2-125">Paket oluşturulduğunda, *CNAB* dizininde bulunan Docker dosyası, pakete dahil edilecek bir Docker görüntüsüne yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="983f2-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="983f2-126">Terşform 'ın paket içindeki bir Docker kapsayıcısı içinde yüklü olması, kullanıcıların paketlemeyi çalıştırması için makinenizde Terırform 'ın yüklü olması gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="983f2-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="983f2-127">**Şekil 10-18** -örnek bir Terrayform dosyası</span><span class="sxs-lookup"><span data-stu-id="983f2-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="983f2-128">`bundle.json`Ayrıca, Terrayform 'a geçirilmiş bir parametre kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="983f2-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="983f2-129">Paketin Parametreleştirme özelliği, çeşitli farklı ortamlarda yüklemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="983f2-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="983f2-130">CNAB biçimi de esnektir ve bu da tüm bulutlarca kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="983f2-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="983f2-131">Bu, [OpenStack](https://www.openstack.org/)gibi şirket içi çözümlere karşı bile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="983f2-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="983f2-132">DevOps kararları</span><span class="sxs-lookup"><span data-stu-id="983f2-132">DevOps Decisions</span></span>

<span data-ttu-id="983f2-133">DevOps alanında bu günlerde çok sayıda harika araç ve hatta daha fazla harika kitap ve bilgi</span><span class="sxs-lookup"><span data-stu-id="983f2-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="983f2-134">DevOps yolculuğuna başlamak için sık kullanılan bir kitap, NoOps 'dan DevOps 'a kurgusal bir şirketin dönüşümünü izleyen [Phoenix projenidir](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/).</span><span class="sxs-lookup"><span data-stu-id="983f2-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="983f2-135">Bir şey belirli bir şeydir: DevOps, karmaşık, bulut Yerel uygulamaları dağıtımında artık "daha iyi" olsun.</span><span class="sxs-lookup"><span data-stu-id="983f2-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="983f2-136">Bu bir gereksinimdir ve herhangi bir projenin başlangıcında planlanmış ve kaynakları planlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="983f2-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="983f2-137">Başvurular</span><span class="sxs-lookup"><span data-stu-id="983f2-137">References</span></span>

- [<span data-ttu-id="983f2-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="983f2-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="983f2-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="983f2-139">Azure Resource Manager</span></span>](https://azure.microsoft.com/documentation/articles/resource-group-overview/)
- [<span data-ttu-id="983f2-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="983f2-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="983f2-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="983f2-141">Azure CLI</span></span>](https://docs.microsoft.com/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="983f2-142">[Önceki](infrastructure-as-code.md) 
> [Sonraki](summary.md)</span><span class="sxs-lookup"><span data-stu-id="983f2-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
