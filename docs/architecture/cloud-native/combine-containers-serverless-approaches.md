---
title: Bulutta yerel hizmetler için kapsayıcıları ve sunucusuz yaklaşımları birleştirme
description: Kapsayıcıları ve Kubernetes 'i sunucusuz yaklaşımlar ile birleştirme
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199670"
---
# <a name="combining-containers-and-serverless-approaches"></a>Kapsayıcıları ve sunucusuz yaklaşımları birleştirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulutta yerel uygulamalar genellikle kapsayıcılardan ve düzenleme özelliğinden yararlanan hizmetleri uygular. Genellikle bazı uygulama hizmetlerini Azure Işlevleri olarak kullanıma sunma fırsatları vardır. Ancak, Kubernetes 'e dağıtılan bir bulutta yerel uygulama sayesinde, bu araç takımı içindeki Azure Işlevlerinin yararlanmak iyi bir uygulamadır. Neyse ki, Docker Kapsayıcıları içindeki Azure Işlevlerini kaydırabilirsiniz ve Kubernetes tabanlı uygulamanızın geri kalanı ile aynı işlemleri ve araçları kullanarak bunları dağıtabilirsiniz.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Ne zaman sunucusuz ile kapsayıcıları kullanmak mantıklı midir?

Azure Işlevinizin dağıtıldığı platforma ilişkin bir bilgisi yok. Bazı senaryolarda, belirli gereksinimleriniz olabilir ve işlev kodunuzun çalışacağı ortamı özelleştirmeniz gerekebilir. Bağımlılıkları destekleyen özel bir görüntüye veya varsayılan görüntü tarafından desteklenmeyen bir yapılandırmaya ihtiyacınız vardır. Bu durumlarda, işlevinizi özel bir Docker kapsayıcısında dağıtmak mantıklı olur.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Azure Işlevleri ile kapsayıcıları kullanmaktan kaçınmak ne zaman?

Tüketim faturalandırmasını kullanmak istiyorsanız, işlevinizi bir kapsayıcıda çalıştıramazsınız. Daha fazlası, işlevinizi bir Kubernetes kümesine dağıtırsanız, Azure Işlevleri tarafından sunulan yerleşik ölçeklendirmeden artık yararlanabileceksiniz. Bu bölümde daha önce açıklanan Kubernetes ' ölçeklendirme özelliklerini kullanmanız gerekir.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Sunucusuz ve Docker kapsayıcılarını birleştirme

Bir Docker kapsayıcısında bir Azure Işlevini kaydırmak için [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) yükleyip aşağıdaki komutu çalıştırın:

```console
func init ProjectName --worker-runtime dotnet --docker
```

Proje oluşturulduğunda, bir Dockerfile ve ile `dotnet`yapılandırılan çalışan çalışma zamanı dahil edilir. Şimdi, işlevinizi yerel olarak oluşturup test edebilirsiniz. `docker build` Ve `docker run` komutlarını kullanarak derleyin ve çalıştırın. Docker desteğiyle Azure Işlevleri oluşturmaya başlamanıza yönelik ayrıntılı adımlar için bkz. [Linux üzerinde bir Işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) öğreticisini kullanarak.

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>KEDA ile sunucusuz ve Kubernetes 'i birleştirme

Azure işlevleri, hedeflenen olayların hızına göre talebi karşılamak için otomatik olarak ölçeklendirilir. Her zaman, işlevlerinizi barındırmak ve Kubernetes tabanlı olay temelli otomatik ölçeklendirmeyi veya KEDA kullanmak için AKS 'den yararlanabilirsiniz. Herhangi bir olay gerçekleşirken KEDA, sıfır örneğe ölçeklendirebilir. [KEDA Ile Azure işlevlerinin ölçeklendirilmesi hakkında daha fazla bilgi edinin](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

>[!div class="step-by-step"]
>[Önceki](leverage-serverless-functions.md)
>[İleri](deploy-containers-azure.md)
