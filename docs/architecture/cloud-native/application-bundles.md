---
title: Cloud Native uygulama demeti
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native uygulama demeti
ms.date: 06/30/2019
ms.openlocfilehash: 0c67035af08d3c337ff027f3742e1ce8a83f8d0f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183716"
---
# <a name="cloud-native-application-bundles"></a>Cloud Native uygulama demeti

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulutta yerel uygulamaların anahtar özelliği, geliştirmeyi hızlandırmak için bulutun özelliklerinden faydalandıklarından. Bu genellikle tam bir uygulamanın farklı teknoloji türlerini kullandığı anlamına gelir. Uygulamalar Docker kapsayıcılarından yüklenebilir, bazı hizmetler Azure Işlevlerini kullanarak diğer parçalar donanım GPU hızlandırmalı büyük metal sunucularda ayrılan sanal makinelerde doğrudan çalışabilir. İki bulut Yerel uygulaması aynı değildir; bu nedenle, sevk etmek için tek bir mekanizma sağlamak zordur.

Docker kapsayıcıları, dağıtım için bir helk grafiği kullanılarak Kubernetes üzerinde çalışabilir. Azure Işlevleri Terrayform şablonları kullanılarak ayrılabilir. Son olarak, sanal makineler Terrayform kullanılarak ayrılabilir ancak anormal kullanılarak oluşturulmuş olabilir. Bu bir bütün teknolojiden oluşur ve bunları makul bir pakette paketetmenin bir yolu yoktur. Şimdi.

Cloud Native uygulama demeti (CNABs), dağıtılmış uygulamaları paketlemeyi sağlamak için bir belirtim geliştirmek üzere Microsoft, Docker ve HashiCorp gibi çeşitli topluluk odaklı şirketlerin Birleşik bir çabadır.

Çaba, Aralık 2018 ' de duyuruldu. bu nedenle, daha fazla topluluğun çabasını sergilemek için bir iş gücü de daha fazla. Ancak, zaten [Duffle](https://duffle.sh/)olarak bilinen [açık bir belirtim](https://github.com/deislabs/cnab-spec) ve başvuru uygulamanız vardır. Go 'da yazılmış olan bu araç, Docker ve Microsoft arasındaki bir birleşme çabadır.

CNABs, farklı türlerde yükleme teknolojileri içerebilir. Bu, Helm grafikleri, Terkaform şablonları ve anormal PlayBook gibi öğelerin aynı pakette yer almasına imkan tanır. Oluşturulduktan sonra paketler kendi içinde ve taşınabilir; Bu, USB Stick yüklenebilir.  Paketler, talep ettikleri taraftan kaynaklandıklarından emin olmak için şifreli olarak imzalanır.

CNAB 'nin çekirdeği adlı `bundle.json`bir dosyadır. Bu dosya, paket içeriğini tanımlar, bu, bunlar veya resimler ya da başka bir şey olabilir. Şekil 11-9, bazı Tersform çağıran bir CNAB tanımlar. Bununla birlikte, aslında Terrayform çağırmak için kullanılan bir çağırma görüntüsünü tanımladığına dikkat edin. Paket oluşturulduğunda, *CNAB* dizininde bulunan Docker dosyası, pakete dahil edilecek bir Docker görüntüsüne yerleşik olarak bulunur. Terşform 'ın paket içindeki bir Docker kapsayıcısı içinde yüklü olması, kullanıcıların paketlemeyi çalıştırması için makinenizde Terırform 'ın yüklü olması gerekmediği anlamına gelir.

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

**Şekil 11-13** -örnek bir Terrayform dosyası

Ayrıca `bundle.json` , terrayform 'a geçirilmiş bir parametre kümesi tanımlar. Paketin Parametreleştirme özelliği, çeşitli farklı ortamlarda yüklemeye izin verir.

CNAB biçimi de esnektir ve bu da tüm bulutlarca kullanılmasına izin verir. Bu, [OpenStack](https://www.openstack.org/)gibi şirket içi çözümlere karşı bile kullanılabilir.

## <a name="devops-decisions"></a>DevOps kararları

DevOps alanında bu günlerde çok sayıda harika araç ve hatta daha fazla harika kitap ve bilgi DevOps yolculuğuna başlamak için sık kullanılan bir kitap, NoOps 'dan DevOps 'a kurgusal bir şirketin dönüşümünü izleyen [Phoenix projenidir](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/). Bunlardan biri belirli bir şeydir: DevOps, karmaşık, bulut Yerel uygulamaları dağıtımında artık "daha iyi" olsun. Bu bir gereksinimdir ve herhangi bir projenin başlangıcında planlanmış ve kaynakları planlı olmalıdır.

>[!div class="step-by-step"]
>[Önceki](infrastructure-as-code.md)
