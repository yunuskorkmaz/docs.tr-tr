---
title: Kod olarak altyapı
description: Azure için Cloud Native .NET uygulamaları tasarlama | Kod olarak altyapı
ms.date: 06/30/2019
ms.openlocfilehash: e395db28bdeff785251b91ed643f9920873d26e8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183016"
---
# <a name="infrastructure-as-code"></a>Kod olarak altyapı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulutta yerel uygulamalar, bir hizmet olarak platform (PaaS) bileşeni olan her türlü sıralamayı kullanır. Azure gibi bir bulut platformunda, bu bileşenler depolama, Service Bus ve SignalR hizmeti gibi şeyleri içerebilir. Uygulamalar daha karmaşık hale geldiğinde, kullanımdaki bu hizmetlerin sayısı büyük olasılıkla büyüyebilir. Sürekli teslimin bir ortama el ile dağıtım yaptığı geleneksel modeli ne kadar hızlı bir şekilde dağıttığı gibi, değişikliğin hızlı bir şekilde bir merkezi BT grubu ortamlarını yönetme modeli de vardır.

Ortamları derleme ve ayrıca, aynı zamanda otomatik hale getirilebilir. İşlemi kolay hale getirmek için çok sayıda iyi düşünce sunan araçlar vardır.

## <a name="azure-resource-manager-templates"></a>Azure Resource Manager şablonları

Azure Resource Manager şablonlar, Azure 'da çeşitli kaynakları tanımlamaya yönelik JSON tabanlı bir dildir. Temel şema Şekil 11-10 gibi bir şey arar.

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

**Şekil 11-10** -Kaynak Yöneticisi şablonun şeması

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

**Şekil 11-11** -Kaynak Yöneticisi şablonunda tanımlanan bir depolama hesabı örneği

Şablonlar, bir şablonun geliştirme, QA ve üretim ortamlarını tanımlamak üzere farklı ayarlarla yeniden kullanılabilmesi için parametreli hale getirilmiş olabilir. Bu, düşük ortamlardan farklı şekilde ayarlanan daha yüksek bir ortama geçiş yaparken sürprizleri ortadan kaldırmaya yardımcı olur. Bir şablonda tanımlanan kaynaklar genellikle Azure 'daki tek bir kaynak grubu içinde oluşturulur (tek bir Kaynak Yöneticisi şablonunda birden fazla kaynak grubu tanımlamak mümkündür ancak olağan dışı). Bu, yalnızca kaynak grubunu bir bütün olarak silerek bir ortamı silmeyi çok kolay hale getirir. Maliyet analizi, kaynak grubu düzeyinde de çalıştırılabilir, böylece her bir ortamın maliyetlendirilmesi için hızlı bir hesaplama yapılabilir.

GitHub 'da [Azure hızlı başlangıç şablonları](https://github.com/Azure/azure-quickstart-templates) projesinde tanımlanmış birçok örnek şablon vardır. Bu, yeni bir şablon üzerinde Başlarken veya var olan bir şablona ekleme yaparken bir bacının başlamasını sağlar.

Kaynak Yöneticisi şablonlar, çeşitli yollarla çalıştırılabilir. Belki de en kolay yolu Azure portal yapıştırmanız yeterlidir. Deneysel dağıtımlar için bu yöntem çok hızlı olabilir. Azure DevOps 'da derleme veya yayın sürecinin bir parçası olarak da çalıştırılabilirler. Şablonları çalıştırmak için Azure ile bağlantıları kullanacak görevler vardır. Kaynak Yöneticisi şablonlarındaki değişiklikler artımlı olarak uygulanır, yani yeni bir kaynak eklemek için şablona eklemek yeterlidir. Araç, geçerli kaynak grubunu şablonda tanımlanmış istenen kaynak grubuyla birlikte işleyecek. Daha sonra, kaynaklar şablonda tanımlananla eşleşecek şekilde oluşturulur veya değiştirilir.  

## <a name="terraform"></a>Terraform

Kaynak Yöneticisi şablonlarının algılanan bir dezavantajı, Azure bulutuna özgü olduklarından emin olmalarıdır. Birden fazla buluttan kaynak içeren uygulamalar oluşturmak olağan dışı bir durumlardır, ancak işin yansımalı çalışma süresine dayanmasına neden olduğu durumlarda, birden fazla bulutu destekleme maliyeti çok uzun olabilir. Her bulut genelinde kullanılabilecek bir şablon oluşturma dili varsa, geliştirici becerilerinin çok daha taşınabilir olmasını da sağlar.

Yalnızca bunu yapan çeşitli teknolojiler vardır! Bu alandaki en çok sayıda teklif [Terrayform](https://www.terraform.io/)olarak bilinir. Terminform, Azure, Google Cloud Platform, AWS ve AliCloud gibi her büyük bulut oynatıcıyı destekler ve ayrıca Heroku ve DigitalOcean gibi düzinelerce küçük oyuncuları da destekler. Şablon tanımlama dili olarak JSON kullanmak yerine, biraz daha terse YAML kullanır. 

Şekil 11-12 ' de, önceki Kaynak Yöneticisi şablonuyla aynı olan bir örnek Teraform dosyası (Şekil 11-11) gösterilmektedir:

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

**Şekil 11-12** -Kaynak Yöneticisi Şablon örneği

Terkform, şablondaki bir hata nedeniyle bir kaynak dağıtılırsa, daha iyi bir hata iletileri sağlamaya yönelik daha iyi bir iş oluşturur. Bu, Kaynak Yöneticisi şablonlarının devam eden zorluklara sahip olduğu bir alandır. Ayrıca, şablon hatalarının erken yakalanması için derleme aşamasında kullanılabilecek çok kullanışlı bir görev vardır.

Kaynak Yöneticisi şablonlarda olduğu gibi, Terrayform şablonlarını dağıtmak için kullanılabilecek komut satırı araçları vardır. Ayrıca, Azure Pipelines ' de, Terkform şablonlarını doğrulayabilen ve uygulayabilen topluluk tarafından oluşturulan görevler de vardır.

Terrayform veya Kaynak Yöneticisi şablonunun, yeni oluşturulan bir veritabanına bağlantı dizesi gibi ilginç değerler çıktılarına çıkış durumunda, derleme ardışık düzeninde yakalanıp sonraki görevlerde kullanılabilir.

>[!div class="step-by-step"]
>[Önceki](devops.md)
>[İleri](application-bundles.md)
