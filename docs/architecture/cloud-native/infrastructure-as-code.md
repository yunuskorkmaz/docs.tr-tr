---
title: Kod olarak altyapı
description: Bulutta yerel uygulamalarla kod olarak altyapı (IAC)
ms.date: 05/12/2020
ms.openlocfilehash: 309dd8610ab3b72a6c6da5297f109f822520c5ff
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395343"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="c97ac-103">Kod olarak altyapı</span><span class="sxs-lookup"><span data-stu-id="c97ac-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c97ac-104">Bulut Yerel sistemleri, hızlı ve çeviklik sağlamak için mikro hizmetleri, kapsayıcıları ve modern sistem tasarımını imine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c97ac-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="c97ac-105">Tutarlı ve kalite kodu sağlamak için otomatik derleme ve sürüm aşamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="c97ac-106">Ancak bu yalnızca hikayenin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-106">But, that's only part of the story.</span></span> <span data-ttu-id="c97ac-107">Bu sistemlerin üzerinde çalıştığı bulut ortamlarını nasıl sağlayacaksınız?</span><span class="sxs-lookup"><span data-stu-id="c97ac-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="c97ac-108">Modern bulutla yerel uygulamalar, [altyapının kod olarak](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)kabul edilen yaygın olarak benimsenme yöntemini benimseyin `IaC` .</span><span class="sxs-lookup"><span data-stu-id="c97ac-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="c97ac-109">IAC ile platform sağlamayı otomatikleştirin.</span><span class="sxs-lookup"><span data-stu-id="c97ac-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="c97ac-110">Aslında DevOps uygulamalarınıza test ve sürüm oluşturma gibi yazılım mühendisliği uygulamalarını uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="c97ac-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="c97ac-111">Altyapınız ve dağıtımlarınız otomatik, tutarlı ve yinelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="c97ac-112">Sürekli teslim, el ile yapılan dağıtımların geleneksel modelini otomatik olarak, kod olarak altyapı (IAC), uygulama ortamlarının nasıl yönetildiğini de gelişiyor.</span><span class="sxs-lookup"><span data-stu-id="c97ac-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="c97ac-113">Azure Resource Manager (ARM), Terkform ve Azure komut satırı arabirimi (CLı) gibi araçlar, ihtiyacınız olan bulut altyapısını bildirimli olarak betiğe olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="c97ac-114">Azure Resource Manager şablonları</span><span class="sxs-lookup"><span data-stu-id="c97ac-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="c97ac-115">ARM [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/)için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c97ac-115">ARM stands for [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span></span> <span data-ttu-id="c97ac-116">Bu, Azure 'da yerleşik olan ve API hizmeti olarak sunulan bir API sağlama altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="c97ac-117">ARM, Azure Kaynak grubu 'nda bulunan kaynakları tek ve eşgüdümlü bir işlem halinde dağıtmanıza, güncelleştirmenize, silmenizi ve yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="c97ac-118">Altyapıyı, ihtiyacınız olan kaynakları ve bunların yapılandırmalarını belirten bir JSON tabanlı şablonla birlikte sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="c97ac-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="c97ac-119">ARM, dağıtımı otomatik olarak doğru sırada düzenler ve bağımlılıkları kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="c97ac-120">Motor, üst sınırı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-120">The engine ensures idempotency.</span></span> <span data-ttu-id="c97ac-121">Aynı yapılandırmaya sahip istenen bir kaynak zaten varsa, sağlama yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="c97ac-122">Azure Resource Manager şablonlar, Azure 'da çeşitli kaynakları tanımlamaya yönelik JSON tabanlı bir dildir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="c97ac-123">Temel şema Şekil 10-14 gibi bir şey arar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="c97ac-124">**Şekil 10-14** -Kaynak Yöneticisi şablonun şeması</span><span class="sxs-lookup"><span data-stu-id="c97ac-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="c97ac-125">Bu şablon içinde, bir depolama kapsayıcısını kaynaklar bölümünde şöyle tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="c97ac-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="c97ac-126">**Şekil 10-15** -Kaynak Yöneticisi şablonunda tanımlanan bir depolama hesabı örneği</span><span class="sxs-lookup"><span data-stu-id="c97ac-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="c97ac-127">ARM şablonu, dinamik ortam ve yapılandırma bilgileriyle parametrelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="c97ac-128">Bunun yapılması, geliştirme, QA veya üretim gibi farklı ortamları tanımlamak için yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="c97ac-129">Normalde, şablon tek bir Azure Kaynak grubu içindeki tüm kaynakları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c97ac-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="c97ac-130">Gerekirse, tek bir Kaynak Yöneticisi şablonunda birden fazla kaynak grubu tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c97ac-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="c97ac-131">Kaynak grubunun kendisini silerek, bir ortamdaki tüm kaynakları silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c97ac-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="c97ac-132">Maliyet analizi, kaynak grubu düzeyinde de çalıştırılabilir, böylece her bir ortamın maliyetlendirilmesi için hızlı bir hesaplama yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="c97ac-133">GitHub 'da [Azure hızlı başlangıç şablonları](https://github.com/Azure/azure-quickstart-templates) projesinde birçok örnek veya ARM şablonu mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c97ac-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="c97ac-134">Yeni bir şablon oluşturmayı veya var olan bir şablonu değiştirmeyi hızlandırmaya yardımcı olabilirler.</span><span class="sxs-lookup"><span data-stu-id="c97ac-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="c97ac-135">Kaynak Yöneticisi şablonlar birçok şekilde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="c97ac-136">Belki de en kolay yolu Azure portal yapıştırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="c97ac-137">Deneysel dağıtımlar için bu yöntem hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="c97ac-138">Azure DevOps 'da derleme veya yayın sürecinin bir parçası olarak da çalıştırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="c97ac-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="c97ac-139">Şablonları çalıştırmak için Azure ile bağlantıları kullanacak görevler vardır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="c97ac-140">Kaynak Yöneticisi şablonlarındaki değişiklikler artımlı olarak uygulanır, yani yeni bir kaynak eklemek için şablona eklemek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="c97ac-141">Araç, geçerli kaynaklar ile şablonda tanımlananlar arasındaki farkları uzlaştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="c97ac-142">Daha sonra, kaynaklar şablonda tanımlananla eşleşecek şekilde oluşturulur veya değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="c97ac-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="c97ac-143">Terraform</span></span>

<span data-ttu-id="c97ac-144">Bulutta yerel uygulamalar genellikle olarak oluşturulur `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="c97ac-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="c97ac-145">Bu şekilde, uygulamanın belirli bir bulut satıcısına sıkı bir şekilde bağlı olmaması ve herhangi bir genel buluta dağıtılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="c97ac-146">[Terminform](https://www.terraform.io/) , tüm büyük bulut oynatıcılarda bulutta yerel uygulamalar sağlayabileceğiniz ticari şablon oluşturma aracıdır: Azure, Google Cloud Platform, AWS ve alicloud.</span><span class="sxs-lookup"><span data-stu-id="c97ac-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="c97ac-147">Şablon tanımlama dili olarak JSON kullanmak yerine, biraz daha terse YAML kullanır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="c97ac-148">Şekil 10-16 ' de, önceki Kaynak Yöneticisi şablonuyla aynı olan bir örnek Teraform dosyası (Şekil 10-15) gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c97ac-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="c97ac-149">**Şekil 10-16** -Kaynak Yöneticisi Şablon örneği</span><span class="sxs-lookup"><span data-stu-id="c97ac-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="c97ac-150">Terrayform, sorun şablonları için sezgisel hata iletileri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="c97ac-151">Ayrıca, şablon hatalarının erken yakalanması için derleme aşamasında kullanılabilecek yararlı bir doğrulama görevi vardır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="c97ac-152">Kaynak Yöneticisi şablonlarda olduğu gibi, Terrayform şablonlarını dağıtmak için komut satırı araçları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="c97ac-153">Ayrıca, Azure Pipelines ' de, Terkform şablonlarını doğrulayabilen ve uygulayabilen topluluk tarafından oluşturulan görevler de vardır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="c97ac-154">Bazen Terkform ve ARM şablonları, yeni oluşturulan bir veritabanına yönelik bağlantı dizesi gibi anlamlı değerler çıktı.</span><span class="sxs-lookup"><span data-stu-id="c97ac-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="c97ac-155">Bu bilgiler derleme ardışık düzeninde yakalanıp sonraki görevlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="c97ac-156">Azure CLı betikleri ve görevleri</span><span class="sxs-lookup"><span data-stu-id="c97ac-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="c97ac-157">Son olarak, bulut altyapınıza bildirimli olarak betik eklemek için [Azure CLI](https://docs.microsoft.com/cli/azure/) özelliğinden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c97ac-157">Finally, you can leverage [Azure CLI](https://docs.microsoft.com/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="c97ac-158">Azure CLı betikleri, neredeyse tüm Azure kaynakları sağlamak ve yapılandırmak için oluşturulabilir, bulunabilir ve paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="c97ac-159">CLı, Gentle öğrenme eğrisi ile kullanımı basittir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="c97ac-160">Betikler PowerShell veya bash içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c97ac-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="c97ac-161">Bunlar, özellikle de ARM şablonlarıyla karşılaştırıldığında hata ayıklama yapmak için de oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="c97ac-162">Azure CLı betikleri, altyapınızı bölmek ve yeniden dağıtmanız gerektiğinde iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="c97ac-163">Mevcut bir ortamı güncelleştirmek karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="c97ac-164">Birçok CLı komutu ıdempotent değildir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="c97ac-165">Diğer bir deyişle, kaynak zaten mevcut olsa bile, her çalıştırıldığında kaynağı yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c97ac-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="c97ac-166">Her zaman oluşturmadan önce her bir kaynağın varlığını denetleyen kodu eklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c97ac-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="c97ac-167">Ancak, bunun yapılması, betiğinizin kaldırılması ve yönetilmesi zor hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="c97ac-168">Bu betikler aynı zamanda Azure DevOps işlem hatları ile de katıştırılabilir `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="c97ac-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="c97ac-169">İşlem hattının yürütülmesi betiği çağırır.</span><span class="sxs-lookup"><span data-stu-id="c97ac-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="c97ac-170">Şekil 10-17, Azure CLı sürümünü ve aboneliğin ayrıntılarını listeleyen bir YAML kod parçacığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="c97ac-171">Azure CLı komutlarının satır içi bir betiğe nasıl dahil edildiğini aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="c97ac-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="c97ac-172">**Şekil 10-17** -Azure CLI betiği</span><span class="sxs-lookup"><span data-stu-id="c97ac-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="c97ac-173">Makalesinde [kod olarak altyapı nedir](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Sam Guckenheimer yazar, "IAC 'Yı uygulayan ekipler, kararlı ortamları hızla ve ölçekte teslim edebilir.</span><span class="sxs-lookup"><span data-stu-id="c97ac-173">In the article, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="c97ac-174">Takımlar ortamların el ile yapılandırılmasını önler ve ortamları kod aracılığıyla istenen durumunu temsil ederek tutarlılığı zorlar.</span><span class="sxs-lookup"><span data-stu-id="c97ac-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="c97ac-175">IAC ile altyapı dağıtımları tekrarlanabilir ve yapılandırma DRIP veya eksik bağımlılıklara neden olan çalışma zamanı sorunlarını önler.</span><span class="sxs-lookup"><span data-stu-id="c97ac-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="c97ac-176">DevOps ekipleri, uygulamaları ve destekleyici altyapıyı hızlı, güvenilir ve ölçeklenebilir bir şekilde sunmak için birleştirilmiş bir uygulama ve araç kümesiyle birlikte çalışabilir. "</span><span class="sxs-lookup"><span data-stu-id="c97ac-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c97ac-177">[Önceki](feature-flags.md) 
> [Sonraki](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="c97ac-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
