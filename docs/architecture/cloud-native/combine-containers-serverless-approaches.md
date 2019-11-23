---
title: Kapsayıcıları ve sunucusuz yaklaşımları birleştirme
description: Kapsayıcıları ve Kubernetes 'i sunucusuz yaklaşımlar ile birleştirme
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183436"
---
# <a name="combining-containers-and-serverless-approaches"></a>Kapsayıcıları ve sunucusuz yaklaşımları birleştirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Genellikle, mikro hizmet tabanlı uygulamalar düğümler arasında iletişim için kapsayıcılar, düzenleme ve ileti geçişini yoğun bir şekilde kullanır. Bu mesajlaşma, Azure Işlevleri için ideal bir görevdir, ancak Kubernetes ve ilgili araçlar kullanılarak yapılandırılan ve dağıtılan uygulamanın geri kalanı ile aynı araç takımı içindeki Azure Işlevleri 'nden faydalanabilir. Neyse ki, Docker kapsayıcılarındaki Azure Işlevlerini kaydırabilirsiniz ve Kubernetes tabanlı uygulamanızın geri kalanı ile aynı işlemleri ve araçları kullanarak bunları dağıtabilirsiniz.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Ne zaman sunucusuz ile kapsayıcıları kullanmak mantıklı midir?

Varsayılan olarak, sunucusuz işlevleriniz, çalıştırdıkları platforma ilişkin hiçbir bilgiye sahip değildir. Ancak bazı durumlarda, kodunuzun çalışacağı kapsayıcı görüntüsünü özelleştirmenizi sağlayan belirli gereksinimlere sahip olabilirsiniz. İşleviniz belirli bir dil sürümünü temel aldığından veya varsayılan görüntü tarafından desteklenmeyen bağımlılıklara veya yapılandırma gereksinimlerine sahip olduğundan özel bir görüntü kullanmak isteyebilirsiniz. Bu durumlarda, kendi kapsayıcınızı özelleştirmek ve işlevinizi özel bir Docker kapsayıcısında dağıtmak mantıklı olabilir.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Azure Işlevleri ile kapsayıcıları kullanmaktan kaçınmak ne zaman?

İşleviniz için tüketim planı faturalandırma avantajlarından faydalanmayı bekliyorsanız, kendi kapsayıcınızı kullanıyorsanız bunu yapamazsınız. Ne kadar çok bir Docker kapsayıcısı kullanmaktan ve işlevlerinizi kendi Kubernetes kümenize dağıtırsanız, Azure Işlevleri tarafından sunulan yerleşik ölçeklendirmeden artık yararlanabileceksiniz. Aşağıda açıklanan Kubernetes ' ölçeklendirme özelliklerini kullanmanız gerekir.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Sunucusuz ve Docker kapsayıcılarını birleştirme

Bir Docker kapsayıcısında bir Azure Işlevini kaydırmak için Azure Functions Core Tools yükleyip aşağıdaki komutu çalıştırın:

```console
func init ProjectName --docker
```

Aşağıdaki seçeneklerden istediğiniz çalışan çalışma zamanını seçin:

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

Proje oluşturulduğunda, bir Dockerfile içerecektir. Şimdi, işlevinizi yerel olarak oluşturup test edebilirsiniz. `docker build` ve `docker run` komutlarını kullanarak derleyin ve çalıştırın. Docker desteğiyle Azure Işlevleri oluşturmaya başlamanıza yönelik ayrıntılı adımlar için bkz. [Linux üzerinde bir Işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) öğreticisini kullanarak.

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>KEDA ile sunucusuz ve Kubernetes 'i birleştirme

Azure işlevleri, belirli bir işlevi hedefleyen olayların hızına göre talebi karşılamak için otomatik olarak ölçeklendirilir. Ayrıca, işlevlerinizi barındırmak için Kubernetes özelliğinden yararlanarak Kubernetes tabanlı olay temelli otomatik ölçeklendirme veya KEDA kullanabilirsiniz. Hiçbir olay gerçekleşmez, KEDA 0 örneğe kadar ölçeklendirebilir ve ardından olaya yanıt olarak, yatay Pod otomatik Scaler kullanarak talebi karşılayacak kapsayıcı sayısını ölçeklendirebilirler. [KEDA Ile Azure işlevlerinin ölçeklendirilmesi hakkında daha fazla bilgi edinin](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

## <a name="references"></a>Referanslar

- [Azure Işlevlerini bir Docker kapsayıcısında çalıştırma](https://markheath.net/post/azure-functions-docker)
- [Linux üzerinde özel görüntü kullanarak bir işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Kubernetes olay odaklı otomatik ölçeklendirmeyle Azure Işlevleri](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[Önceki](leverage-serverless-functions.md)
>[İleri](deploy-containers-azure.md)
