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
# <a name="infrastructure-as-code"></a>Kod olarak altyapı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulut Yerel sistemleri, hızlı ve çeviklik sağlamak için mikro hizmetleri, kapsayıcıları ve modern sistem tasarımını imine dönüştürür. Tutarlı ve kalite kodu sağlamak için otomatik derleme ve sürüm aşamaları sağlar. Ancak bu yalnızca hikayenin bir parçasıdır. Bu sistemlerin üzerinde çalıştığı bulut ortamlarını nasıl sağlayacaksınız?

Modern bulutla yerel uygulamalar, [altyapının kod olarak](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)kabul edilen yaygın olarak benimsenme yöntemini benimseyin `IaC` .  IAC ile platform sağlamayı otomatikleştirin. Aslında DevOps uygulamalarınıza test ve sürüm oluşturma gibi yazılım mühendisliği uygulamalarını uygularsınız. Altyapınız ve dağıtımlarınız otomatik, tutarlı ve yinelenebilir. Sürekli teslim, el ile yapılan dağıtımların geleneksel modelini otomatik olarak, kod olarak altyapı (IAC), uygulama ortamlarının nasıl yönetildiğini de gelişiyor.

Azure Resource Manager (ARM), Terkform ve Azure komut satırı arabirimi (CLı) gibi araçlar, ihtiyacınız olan bulut altyapısını bildirimli olarak betiğe olanak sağlar.

## <a name="azure-resource-manager-templates"></a>Azure Resource Manager şablonları

ARM [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/)için temsil eder. Bu, Azure 'da yerleşik olan ve API hizmeti olarak sunulan bir API sağlama altyapısıdır. ARM, Azure Kaynak grubu 'nda bulunan kaynakları tek ve eşgüdümlü bir işlem halinde dağıtmanıza, güncelleştirmenize, silmenizi ve yönetmenize olanak sağlar. Altyapıyı, ihtiyacınız olan kaynakları ve bunların yapılandırmalarını belirten bir JSON tabanlı şablonla birlikte sağlarsınız. ARM, dağıtımı otomatik olarak doğru sırada düzenler ve bağımlılıkları kolaylaştırır. Motor, üst sınırı sağlar. Aynı yapılandırmaya sahip istenen bir kaynak zaten varsa, sağlama yok sayılır.

Azure Resource Manager şablonlar, Azure 'da çeşitli kaynakları tanımlamaya yönelik JSON tabanlı bir dildir. Temel şema Şekil 10-14 gibi bir şey arar.

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

**Şekil 10-14** -Kaynak Yöneticisi şablonun şeması

Bu şablon içinde, bir depolama kapsayıcısını kaynaklar bölümünde şöyle tanımlayabilir:

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

**Şekil 10-15** -Kaynak Yöneticisi şablonunda tanımlanan bir depolama hesabı örneği

ARM şablonu, dinamik ortam ve yapılandırma bilgileriyle parametrelenebilir. Bunun yapılması, geliştirme, QA veya üretim gibi farklı ortamları tanımlamak için yeniden kullanılmasını sağlar. Normalde, şablon tek bir Azure Kaynak grubu içindeki tüm kaynakları oluşturur. Gerekirse, tek bir Kaynak Yöneticisi şablonunda birden fazla kaynak grubu tanımlamak mümkündür. Kaynak grubunun kendisini silerek, bir ortamdaki tüm kaynakları silebilirsiniz. Maliyet analizi, kaynak grubu düzeyinde de çalıştırılabilir, böylece her bir ortamın maliyetlendirilmesi için hızlı bir hesaplama yapılabilir.

GitHub 'da [Azure hızlı başlangıç şablonları](https://github.com/Azure/azure-quickstart-templates) projesinde birçok örnek veya ARM şablonu mevcuttur. Yeni bir şablon oluşturmayı veya var olan bir şablonu değiştirmeyi hızlandırmaya yardımcı olabilirler.

Kaynak Yöneticisi şablonlar birçok şekilde çalıştırılabilir. Belki de en kolay yolu Azure portal yapıştırmanız yeterlidir. Deneysel dağıtımlar için bu yöntem hızlı olabilir. Azure DevOps 'da derleme veya yayın sürecinin bir parçası olarak da çalıştırılabilirler. Şablonları çalıştırmak için Azure ile bağlantıları kullanacak görevler vardır. Kaynak Yöneticisi şablonlarındaki değişiklikler artımlı olarak uygulanır, yani yeni bir kaynak eklemek için şablona eklemek yeterlidir. Araç, geçerli kaynaklar ile şablonda tanımlananlar arasındaki farkları uzlaştıracaktır. Daha sonra, kaynaklar şablonda tanımlananla eşleşecek şekilde oluşturulur veya değiştirilir.  

## <a name="terraform"></a>Terraform

Bulutta yerel uygulamalar genellikle olarak oluşturulur `cloud agnostic` . Bu şekilde, uygulamanın belirli bir bulut satıcısına sıkı bir şekilde bağlı olmaması ve herhangi bir genel buluta dağıtılması anlamına gelir.

[Terminform](https://www.terraform.io/) , tüm büyük bulut oynatıcılarda bulutta yerel uygulamalar sağlayabileceğiniz ticari şablon oluşturma aracıdır: Azure, Google Cloud Platform, AWS ve alicloud. Şablon tanımlama dili olarak JSON kullanmak yerine, biraz daha terse YAML kullanır.

Şekil 10-16 ' de, önceki Kaynak Yöneticisi şablonuyla aynı olan bir örnek Teraform dosyası (Şekil 10-15) gösterilmektedir:

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

**Şekil 10-16** -Kaynak Yöneticisi Şablon örneği

Terrayform, sorun şablonları için sezgisel hata iletileri de sağlar. Ayrıca, şablon hatalarının erken yakalanması için derleme aşamasında kullanılabilecek yararlı bir doğrulama görevi vardır.

Kaynak Yöneticisi şablonlarda olduğu gibi, Terrayform şablonlarını dağıtmak için komut satırı araçları kullanılabilir. Ayrıca, Azure Pipelines ' de, Terkform şablonlarını doğrulayabilen ve uygulayabilen topluluk tarafından oluşturulan görevler de vardır.

Bazen Terkform ve ARM şablonları, yeni oluşturulan bir veritabanına yönelik bağlantı dizesi gibi anlamlı değerler çıktı. Bu bilgiler derleme ardışık düzeninde yakalanıp sonraki görevlerde kullanılabilir.

## <a name="azure-cli-scripts-and-tasks"></a>Azure CLı betikleri ve görevleri

Son olarak, bulut altyapınıza bildirimli olarak betik eklemek için [Azure CLI](https://docs.microsoft.com/cli/azure/) özelliğinden yararlanabilirsiniz. Azure CLı betikleri, neredeyse tüm Azure kaynakları sağlamak ve yapılandırmak için oluşturulabilir, bulunabilir ve paylaşılabilir. CLı, Gentle öğrenme eğrisi ile kullanımı basittir. Betikler PowerShell veya bash içinde yürütülür. Bunlar, özellikle de ARM şablonlarıyla karşılaştırıldığında hata ayıklama yapmak için de oldukça kolaydır.

Azure CLı betikleri, altyapınızı bölmek ve yeniden dağıtmanız gerektiğinde iyi çalışır. Mevcut bir ortamı güncelleştirmek karmaşık olabilir. Birçok CLı komutu ıdempotent değildir. Diğer bir deyişle, kaynak zaten mevcut olsa bile, her çalıştırıldığında kaynağı yeniden oluşturur. Her zaman oluşturmadan önce her bir kaynağın varlığını denetleyen kodu eklemek mümkündür. Ancak, bunun yapılması, betiğinizin kaldırılması ve yönetilmesi zor hale gelebilir.

Bu betikler aynı zamanda Azure DevOps işlem hatları ile de katıştırılabilir `Azure CLI tasks` . İşlem hattının yürütülmesi betiği çağırır.

Şekil 10-17, Azure CLı sürümünü ve aboneliğin ayrıntılarını listeleyen bir YAML kod parçacığını gösterir. Azure CLı komutlarının satır içi bir betiğe nasıl dahil edildiğini aklınızda edin.

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

**Şekil 10-17** -Azure CLI betiği

Makalesinde [kod olarak altyapı nedir](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Sam Guckenheimer yazar, "IAC 'Yı uygulayan ekipler, kararlı ortamları hızla ve ölçekte teslim edebilir. Takımlar ortamların el ile yapılandırılmasını önler ve ortamları kod aracılığıyla istenen durumunu temsil ederek tutarlılığı zorlar. IAC ile altyapı dağıtımları tekrarlanabilir ve yapılandırma DRIP veya eksik bağımlılıklara neden olan çalışma zamanı sorunlarını önler. DevOps ekipleri, uygulamaları ve destekleyici altyapıyı hızlı, güvenilir ve ölçeklenebilir bir şekilde sunmak için birleştirilmiş bir uygulama ve araç kümesiyle birlikte çalışabilir. "

>[!div class="step-by-step"]
>[Önceki](feature-flags.md) 
> [Sonraki](application-bundles.md)
