---
title: Kod olarak altyapı
description: Azure için Cloud Native .NET uygulamaları tasarlama | Kod olarak altyapı
ms.date: 06/30/2019
ms.openlocfilehash: 3957da68ac28774f899f49fb181a29c2435902f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087243"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="1f259-103">Kod olarak altyapı</span><span class="sxs-lookup"><span data-stu-id="1f259-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1f259-104">Bulutta yerel uygulamalar, bir hizmet olarak platform (PaaS) bileşeni olan her türlü sıralamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f259-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="1f259-105">Azure gibi bir bulut platformunda, bu bileşenler depolama, Service Bus ve SignalR hizmeti gibi şeyleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="1f259-106">Uygulamalar daha karmaşık hale geldiğinde, kullanımdaki bu hizmetlerin sayısı büyük olasılıkla büyüyebilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="1f259-107">Sürekli teslimin bir ortama el ile dağıtım yaptığı geleneksel modeli ne kadar hızlı bir şekilde dağıttığı gibi, değişikliğin hızlı bir şekilde bir merkezi BT grubu ortamlarını yönetme modeli de vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="1f259-108">Ortamları derleme ve ayrıca, aynı zamanda otomatik hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="1f259-109">İşlemi kolay hale getirmek için çok sayıda iyi düşünce sunan araçlar vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="1f259-110">Azure Resource Manager şablonları</span><span class="sxs-lookup"><span data-stu-id="1f259-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="1f259-111">Azure Resource Manager şablonlar, Azure 'da çeşitli kaynakları tanımlamaya yönelik JSON tabanlı bir dildir.</span><span class="sxs-lookup"><span data-stu-id="1f259-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="1f259-112">Temel şema Şekil 11-10 gibi bir şey arar.</span><span class="sxs-lookup"><span data-stu-id="1f259-112">The basic schema looks something like Figure 11-10.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="1f259-113">**Şekil 11-10** -Kaynak Yöneticisi şablonun şeması</span><span class="sxs-lookup"><span data-stu-id="1f259-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="1f259-114">Bu şablon içinde, bir depolama kapsayıcısını kaynaklar bölümünde şöyle tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="1f259-114">Within this template, one might define a storage container inside the resources section like so:</span></span>

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="1f259-115">**Şekil 11-11** -Kaynak Yöneticisi şablonunda tanımlanan bir depolama hesabı örneği</span><span class="sxs-lookup"><span data-stu-id="1f259-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="1f259-116">Şablonlar, bir şablonun geliştirme, QA ve üretim ortamlarını tanımlamak üzere farklı ayarlarla yeniden kullanılabilmesi için parametreli hale getirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="1f259-117">Bu, düşük ortamlardan farklı şekilde ayarlanan daha yüksek bir ortama geçiş yaparken sürprizleri ortadan kaldırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1f259-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="1f259-118">Bir şablonda tanımlanan kaynaklar genellikle Azure 'daki tek bir kaynak grubu içinde oluşturulur (tek bir Kaynak Yöneticisi şablonunda birden fazla kaynak grubu tanımlamak mümkündür ancak olağan dışı).</span><span class="sxs-lookup"><span data-stu-id="1f259-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="1f259-119">Bu, yalnızca kaynak grubunu bir bütün olarak silerek bir ortamı silmeyi çok kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="1f259-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="1f259-120">Maliyet analizi, kaynak grubu düzeyinde de çalıştırılabilir, böylece her bir ortamın maliyetlendirilmesi için hızlı bir hesaplama yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="1f259-121">GitHub 'da [Azure hızlı başlangıç şablonları](https://github.com/Azure/azure-quickstart-templates) projesinde tanımlanmış birçok örnek şablon vardır. Bu, yeni bir şablon üzerinde Başlarken veya var olan bir şablona ekleme yaparken bir bacının başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f259-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="1f259-122">Kaynak Yöneticisi şablonlar, çeşitli yollarla çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="1f259-123">Belki de en kolay yolu Azure portal yapıştırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1f259-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="1f259-124">Deneysel dağıtımlar için bu yöntem çok hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="1f259-125">Azure DevOps 'da derleme veya yayın sürecinin bir parçası olarak da çalıştırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="1f259-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="1f259-126">Şablonları çalıştırmak için Azure ile bağlantıları kullanacak görevler vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="1f259-127">Kaynak Yöneticisi şablonlarındaki değişiklikler artımlı olarak uygulanır, yani yeni bir kaynak eklemek için şablona eklemek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1f259-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="1f259-128">Araç, geçerli kaynak grubunu şablonda tanımlanmış istenen kaynak grubuyla birlikte işleyecek.</span><span class="sxs-lookup"><span data-stu-id="1f259-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="1f259-129">Daha sonra, kaynaklar şablonda tanımlananla eşleşecek şekilde oluşturulur veya değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="1f259-130">Terraform</span><span class="sxs-lookup"><span data-stu-id="1f259-130">Terraform</span></span>

<span data-ttu-id="1f259-131">Kaynak Yöneticisi şablonlarının algılanan bir dezavantajı, Azure bulutuna özgü olduklarından emin olmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="1f259-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="1f259-132">Birden fazla buluttan kaynak içeren uygulamalar oluşturmak olağan dışı bir durumlardır, ancak işin yansımalı çalışma süresine dayanmasına neden olduğu durumlarda, birden fazla bulutu destekleme maliyeti çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="1f259-133">Her bulut genelinde kullanılabilecek bir şablon oluşturma dili varsa, geliştirici becerilerinin çok daha taşınabilir olmasını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f259-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="1f259-134">Yalnızca bunu yapan çeşitli teknolojiler vardır!</span><span class="sxs-lookup"><span data-stu-id="1f259-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="1f259-135">Bu alandaki en çok sayıda teklif [Terrayform](https://www.terraform.io/)olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1f259-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="1f259-136">Terminform, Azure, Google Cloud Platform, AWS ve AliCloud gibi her büyük bulut oynatıcıyı destekler ve ayrıca Heroku ve DigitalOcean gibi düzinelerce küçük oyuncuları da destekler.</span><span class="sxs-lookup"><span data-stu-id="1f259-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="1f259-137">Şablon tanımlama dili olarak JSON kullanmak yerine, biraz daha terse YAML kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f259-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="1f259-138">Şekil 11-12 ' de, önceki Kaynak Yöneticisi şablonuyla aynı olan bir örnek Teraform dosyası (Şekil 11-11) gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1f259-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="1f259-139">**Şekil 11-12** -Kaynak Yöneticisi Şablon örneği</span><span class="sxs-lookup"><span data-stu-id="1f259-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="1f259-140">Terkform, şablondaki bir hata nedeniyle bir kaynak dağıtılırsa, daha iyi bir hata iletileri sağlamaya yönelik daha iyi bir iş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f259-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="1f259-141">Bu, Kaynak Yöneticisi şablonlarının devam eden zorluklara sahip olduğu bir alandır.</span><span class="sxs-lookup"><span data-stu-id="1f259-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="1f259-142">Ayrıca, şablon hatalarının erken yakalanması için derleme aşamasında kullanılabilecek çok kullanışlı bir görev vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="1f259-143">Kaynak Yöneticisi şablonlarda olduğu gibi, Terrayform şablonlarını dağıtmak için kullanılabilecek komut satırı araçları vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="1f259-144">Ayrıca, Azure Pipelines ' de, Terkform şablonlarını doğrulayabilen ve uygulayabilen topluluk tarafından oluşturulan görevler de vardır.</span><span class="sxs-lookup"><span data-stu-id="1f259-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="1f259-145">Terrayform veya Kaynak Yöneticisi şablonunun, yeni oluşturulan bir veritabanına bağlantı dizesi gibi ilginç değerler çıktılarına çıkış durumunda, derleme ardışık düzeninde yakalanıp sonraki görevlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f259-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1f259-146">[Önceki](devops.md)
>[İleri](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="1f259-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
