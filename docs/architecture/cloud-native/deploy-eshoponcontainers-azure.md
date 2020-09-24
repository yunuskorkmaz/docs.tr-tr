---
title: eShopOnContainers'ı Azure'a dağıtma
description: Azure Kubernetes hizmeti, helk ve DevSpaces kullanarak eShopOnContainers uygulamasını dağıtma.
ms.date: 05/13/2020
ms.openlocfilehash: b3871dae2b414709bfe24b6f7bdbf06de1689d12
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160729"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>eShopOnContainers'ı Azure'a dağıtma

EShopOnContainers uygulaması, çeşitli Azure platformlarına dağıtılabilir. Önerilen yaklaşım, uygulamayı Azure Kubernetes hizmetlerine (AKS) dağıtmaktır. Bir Kubernetes dağıtım aracı olan helk, dağıtım karmaşıklığını azaltmak için kullanılabilir. İsteğe bağlı olarak, geliştiriciler geliştirme sürecini kolaylaştırmak için Kubernetes için Azure Dev Spaces uygulayabilir.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

AKS 'de eShop barındırmak için ilk adım bir AKS kümesi oluşturmaktır. Bunu yapmak için, gerekli adımlarda size yol gösterecek Azure portal kullanabilirsiniz. Ayrıca, rol tabanlı Access Control (RBAC) ve uygulama yönlendirmeyi etkinleştirmek için Azure CLı 'dan bir küme oluşturabilirsiniz. EShopOnContainers ' belgeleri kendi AKS kümenizi oluşturmak için gereken adımları ayrıntılı olarak oluşturur. Oluşturulduktan sonra, Kubernetes panosundan kümeye erişip yönetebilirsiniz.

Artık eShop uygulamasını, Held ve Tiller kullanan kümeye dağıtabilirsiniz.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Held kullanarak Azure Kubernetes hizmetine dağıtma

Helk, doğrudan Kubernetes ile birlikte çalışarak bir uygulama paketi Yöneticisi aracıdır. Kubernetes uygulamalarını tanımlamanıza, yüklemenize ve yükseltmenize yardımcı olur. Basit uygulamalar özel CLı betikleri veya basit dağıtım dosyaları ile AKS 'e dağıtılabilirken, karmaşık uygulamalar çok sayıda Kubernetes nesnesi içerebilir ve Held 'den faydalanabilir.

Held kullanarak uygulamalar, Held paketlerinde uygulamayı ve yapılandırmayı bildirimli olarak açıklayan, Held grafikleri adlı metin tabanlı yapılandırma dosyalarını içerir. Grafikler, ilgili bir Kubernetes kaynakları kümesini anlatmak için standart YAML biçimli dosyaları kullanır. Bunlar, tanımladıkları uygulama kodunun yanı sıra sürümlüdür. Hele grafikleri, tanımladıkları yüklemenin gereksinimlerine bağlı olarak basit ile karmaşık arasında değişir.

Held, Held grafiklerini tüketen ve komutları, Tiller adlı bir sunucu bileşenine Başlatan bir komut satırı istemci aracından oluşur. Tiller, Kapsayıcılı iş yüklerinizin doğru sağlamasını sağlamak için Kubernetes API 'siyle iletişim kurar. Held, bulut Yerel Bilgi Işlem altyapısı tarafından korunur.

Aşağıdaki YAML dosyası bir Held şablonu sunar:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

Şablonun bir dinamik anahtar/değer çiftleri kümesini nasıl açıklayacağını aklınızda edin. Şablon çağrıldığında, küme ayraçları içine alınmış değerler diğer YAML tabanlı yapılandırma dosyalarından çekilir.

EShopOnContainers Held grafiklerini/k8s/Held klasöründe bulabilirsiniz. Şekil 2-6, uygulamanın farklı bileşenlerinin, Held tarafından yönetilen dağıtımlar tanımlamak için kullanılan bir klasör yapısına nasıl düzenlendiğini gösterir.

![eShopOnContainers mimari ](./media/eshoponcontainers-helm-folder.png)
 **Şekil 2-6**. EShopOnContainers Held klasörü.

Her bir bileşen, bir komut kullanılarak yüklenir `helm install` . eShop, ilgili Held grafiklerini kullanarak bileşenleri döngüye sokma ve yükleyen bir "tümünü dağıt" betiği içerir. Sonuç, kaynak denetimindeki uygulamayla sürümlü, ekip üzerindeki herkesin tek satırlık bir betik komutuyla bir AKS kümesine dağıtabileceği, tekrarlanabilir bir işlemdir.

> Help 'nin 2. sürümünün, Tiller Server bileşenine yönelik ihtiyacı ortadan kaldırdığına unutmayın. Bu geliştirme hakkında daha fazla bilgiyi [burada](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714)bulabilirsiniz.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Bulutta yerel uygulamalar hızlı bir şekilde büyük ve karmaşık bir şekilde büyüyerek önemli işlem kaynaklarının çalıştırılmasını gerektirir. Bu senaryolarda, tüm uygulama bir geliştirme makinesinde (özellikle bir dizüstü bilgisayar) barındırılamaz. Azure Dev Spaces, AKS kullanarak bu sorunu gidermek için tasarlanmıştır. Geliştiricilerin, bir AKS geliştirme kümesinde uygulamanın geri kalanını barındırırken hizmetlerinin yerel bir sürümüyle çalışmasını sağlar.

Geliştiriciler, Kapsayıcılı uygulamanın tamamını içeren bir AKS kümesinde çalışan (geliştirme) örneği paylaşır. Ancak, hizmetlerini yerel olarak geliştirmek üzere makinesinde ayarlanan kişisel alanları kullanırlar. Hazırlık yapıldığında, bağımlılıklar çoğaltılmaksızın AKS kümesindeki uçtan uca test ederler. Azure Dev Spaces, yerel makineden AKS Hizmetleri ile kod birleştirir. Ekip üyeleri, değişikliklerinin gerçek bir AKS ortamında nasıl davranacağını görebilir. Geliştiriciler Visual Studio 2017 veya Visual Studio Code kullanarak doğrudan Kubernetes 'te kodu hızla yineleyebilir ve hata ayıklamanıza olanak sağlar.

Şekil 2-7 ' de, geliştirici Susie ' nin, Bisiklet mikro hizmetinin güncelleştirilmiş bir sürümünü geliştirme alanına dağıttığdığını görebilirsiniz. Daha sonra kendi alan adı (susie.s.dev.myapp.eus.azds.io) ile başlayan özel bir URL 'YI kullanarak yaptığı değişiklikleri test edebilir.

![eShopOnContainers mimari ](./media/azure-devspaces-one.png)
 **Şekil 2-7**. Geliştirici Susie, Bisiklet mikro hizmetinin kendi sürümünü dağıtır ve test eder.

Aynı zamanda, geliştirici John, rezervasyonlar mikro hizmetini özelleştirip değişiklikleri test etmek için gereklidir. Şekil 2-8 ' de gösterildiği gibi, Susie değişiklikleri ile çakışmadan kendi dev alanındaki değişiklikleri dağıtır. John daha sonra yaptığı kendi URL 'sini kullanarak değişikliklerini test eder (john.s.dev.myapp.eus.azds.io).

![eShopOnContainers mimari ](./media/azure-devspaces-two.png)
 **Şekil 2-8**. Geliştirici John, rezervasyonlar mikro hizmetinin kendi sürümünü dağıtır ve diğer geliştiricilerle çakışmadan test eder.

Azure Dev Spaces kullanarak takımlar, değişiklikleri bağımsız olarak değiştirirken, dağıttığınızda ve test ederken doğrudan AKS ile çalışabilir. Bu yaklaşım, her geliştiricinin kendi AKS ortamları etkin olduğundan, ayrı ayrı barındırılan ortamların gereksinimini azaltır. Geliştiriciler, CLı kullanarak Azure Dev Spaces çalışabilir veya doğrudan Visual Studio 'dan Azure Dev Spaces için uygulamasını başlatabilir. [Azure Dev Spaces nasıl çalıştığı ve yapılandırıldığı hakkında daha fazla bilgi edinin.](/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Işlevleri ve Logic Apps (sunucusuz)

EShopOnContainers örneği, çevrimiçi pazarlama kampanyalarının izlenmesi için destek içerir. Belirli bir kampanya KIMLIĞI için pazarlama kampanyası ayrıntılarını izlemek üzere bir Azure Işlevi kullanılır. Tam bir mikro hizmet oluşturmak yerine, tek bir Azure Işlevi daha basit ve yeterlidir. Azure Işlevleri, özellikle Kubernetes içinde çalışacak şekilde yapılandırıldığında basit bir derleme ve dağıtım modeline sahiptir. İşlevin dağıtımı Azure Resource Manager (ARM) şablonları ve Azure CLı kullanılarak komut dosyası oluşturulur. Bu kampanya hizmeti müşteriye açık değildir ve tek bir işlemi çağırır ve Azure Işlevleri için harika bir aday yapar. İşlev, veritabanı bağlantı dizesi verileri ve görüntü tabanı URI 'SI ayarları dahil olmak üzere en az yapılandırma gerektirir. Azure Işlevlerini Azure portal yapılandırırsınız.

>[!div class="step-by-step"]
>[Önceki](map-eshoponcontainers-azure-services.md) 
> [Sonraki](centralized-configuration.md)
