---
title: Bulutta yerel hizmetler için kapsayıcıları ve sunucusuz yaklaşımları birleştirme
description: Kapsayıcıları ve Kubernetes 'i sunucusuz yaklaşımlar ile birleştirme
ms.date: 05/13/2020
ms.openlocfilehash: b1b85519ce02ddd1d69735d872cf24fadcc81ef7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160898"
---
# <a name="combining-containers-and-serverless-approaches"></a>Kapsayıcıları ve sunucusuz yaklaşımları birleştirme

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

Proje oluşturulduğunda, bir Dockerfile ve ile yapılandırılan çalışan çalışma zamanı dahil edilir `dotnet` . Şimdi, işlevinizi yerel olarak oluşturup test edebilirsiniz. Ve komutlarını kullanarak derleyin ve çalıştırın  `docker build` `docker run` . Docker desteğiyle Azure Işlevleri oluşturmaya başlamanıza yönelik ayrıntılı adımlar için bkz. [Linux üzerinde bir Işlev oluşturma](/azure/azure-functions/functions-create-function-linux-custom-image) öğreticisini kullanarak.

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>KEDA ile sunucusuz ve Kubernetes 'i birleştirme

Bu bölümde, Azure Işlevleri 'nin platformunun talebi karşılamak için otomatik olarak ölçeklendirilen olduğunu gördünüz. Ancak, Kapsayıcılı işlevleri AKS 'e dağıttığınızda, yerleşik ölçeklendirme işlevini kaybedersiniz. Kurtarma için [Kubernetes tabanlı olay temelli (KEDA)](/azure/azure-functions/functions-kubernetes-keda). Kapsayıcılı işlevleri dahil etmek için hassas otomatik ölçeklendirme imkanı sunar `event-driven Kubernetes workloads,` .

KEDA, Docker kapsayıcısında Işlevlerin çalışma zamanına olay odaklı ölçeklendirme işlevselliği sağlar. KEDA, yük temelinde (herhangi bir olay gerçekleşirken) sıfır örneklerinden ölçeklendirebilir `n instances` . Bu, Kubernetes otomatik ölçeklendirme (yatay Pod otomatik Scaler) için özel ölçümleri ortaya çıkaran otomatik ölçeklendirmeyi sağlar. Bir Kubernetes kümesinde, Işlev kapsayıcılarını KEDA kullanarak, sunucusuz işlev yeteneklerini çoğaltabilirsiniz.

KEDA projesinin artık Cloud Native Computing Foundation (CNCF) tarafından yönetildiğini belirten bir değer.

>[!div class="step-by-step"]
>[Önceki](leverage-serverless-functions.md) 
> [Sonraki](deploy-containers-azure.md)
