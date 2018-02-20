---
title: "Geleneksel web uygulamaları ve tek sayfa uygulamaları arasında seçim yapma"
description: "ASP.NET Core ve Microsoft Azure ile Mimarı modern web uygulamaları"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb830ede1b644700a80f0e9fac2f3608deb88276
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Geleneksel Web uygulamaları ve tek sayfa uygulamaları (SPAs) arasında seçim yapma

> "Atwood'ın Yasası:, JavaScript'te yazılmış herhangi bir uygulama içinde JavaScript sonunda yazılır."  
> _\- Jeff Atwood_

## <a name="summary"></a>Özet

Web uygulamaları oluşturmaya hemen için iki genel yaklaşım vardır: sunucu ve bir web tarayıcısında kullanıcı arabirimi mantığı çoğunu gerçekleştirmek tek sayfa uygulamaları (SPAs) uygulama mantığını çoğunu gerçekleştirmek geleneksel web uygulamaları öncelikle web API'leri kullanarak web sunucusu ile iletişim kurma. Karma bir yaklaşım da mümkündür, en basit olan konak bir veya daha fazla zengin SPA benzeri alt uygulamalara daha büyük bir geleneksel web uygulaması.

Geleneksel web uygulamaları kullanması gereken zaman:

-   Uygulamanızın istemci-tarafı gereksinimleri, basit veya salt okunur.

-   JavaScript desteği olmadan tarayıcılarda çalışabilmesi uygulamanız gerekir.

-   Ekibinizin JavaScript veya TypeScript geliştirme teknikleri tanınmayan ' dir.

Bir SPA kullanması gereken zaman:

-   Uygulamanızın birçok özellik ile zengin kullanıcı arabirimi kullanıma gerekir.

-   Ekibiniz ile JavaScript ve/veya TypeScript geliştirme alışkın olduğu.

-   Uygulamanız, diğer (dahili veya genel) istemcileri için zaten bir kullanıma bir API gerekir.

Ayrıca, SPA çerçeveleri büyük gerektirir mimari ve güvenlik uzmanlık. Bunlar, geleneksel web uygulamalarını daha sık güncelleştirmeler ve yeni çerçeveleri nedeniyle büyük karmaşası karşılaşırsınız. Otomatikleştirilmiş derleme ve dağıtım işlemlerini yapılandırma ve dağıtım seçenekleri kapsayıcıları gibi kullanan geleneksel web uygulamaları SPA uygulamalarla daha zordur.

Bu noktalar karşı SPA modeli tarafından mümkün hale kullanıcı deneyimi geliştirmeleri ağırlıklı gerekir.

## <a name="when-to-choose-traditional-web-apps"></a>Ne zaman geleneksel web uygulamaları seçin

Daha önce belirtildiği nedenlerini geleneksel web uygulamaları çekme daha ayrıntılı bir açıklaması verilmiştir.

**Basit salt okunur büyük olasılıkla, istemci-tarafı gereksinimleri uygulamanızı vardır**

Birçok web uygulamaları, öncelikle bir salt okunur şekilde kullanıcılarının büyük çoğunluğu tarafından tüketilen. Salt okunur (veya okuma çoğunlukla) uygulamalar çok daha kolaydır, bakımını ve durum önemli miktarda işlemek olanlar olma eğilimindedir. Örneğin, bir arama motoru, metin kutusu ve arama sonuçlarını görüntülemek için ikinci bir sayfa ile tek giriş noktası içerebilir. Anonim kullanıcılar istekleri kolayca yapabilirsiniz ve istemci tarafı mantığı için pek gereksinim yoktur. Benzer şekilde, bir blog veya içerik yönetimi sistemin genel kullanıma yönelik uygulama genellikle çoğunlukla biraz istemci tarafı davranışı içerikle oluşur. Bu tür uygulamalar, web sunucusunda mantığı gerçekleştirmek ve tarayıcıda görüntülenecek HTML oluşturmak geleneksel sunucu tabanlı web uygulamaları olarak kolayca oluşturulur. Her sitenin benzersiz sayfasını işareti ve arama motorları tarafından (varsayılan olarak bu uygulamanın ayrı bir özellik olarak eklemek zorunda kalmadan) dizine kendi URL sahip olmasına ayrıca Temizle senaryolarda avantajdır.

**JavaScript desteği olmadan tarayıcılarda çalışması uygulamanız gereken**

Sınırlı olan veya hiç JavaScript desteği tarayıcılarda çalışması için gereken web uygulamaları geleneksel web uygulaması iş akışlarını kullanarak yazılmalıdır (veya en az bu tür davranış geri mümkün olmayacaktır). SPAs çalışması için istemci tarafı JavaScript gerektirir; kullanılabilir durumda değilse, SPAs iyi bir seçim değildir.

**Ekibinizin JavaScript veya TypeScript geliştirme teknikleri tanınmayan**

Ekibiniz, JavaScript veya TypeScript ile tanınmayan ancak ile sunucu tarafı web uygulaması geliştirme alışkın olduğu sonra büyük olasılıkla bir geleneksel web uygulaması bir SPA daha hızlı bir şekilde teslim etmek seçebilecekler. Öğrenme program SPAs için bir hedef veya SPA tarafından karşılanan kullanıcı deneyimi gerekli olduğu sürece, geleneksel web uygulamaları oluşturma ile bilginiz ekipler için daha verimli bir seçimdir.

## <a name="when-to-choose-spas"></a>Ne zaman SPAs seçin

Geliştirme, web uygulamanız için bir tek sayfalık uygulamalar stilini seçmek ne zaman daha ayrıntılı bir açıklaması verilmiştir.

**Uygulamanızın birçok özellik ile zengin kullanıcı arabirimi kullanıma sunma**

SPAs kullanıcı eylemleri veya uygulama alanları arasında gezinmek gibi sayfa yeniden yükleniyor gerektirmeyen zengin istemci tarafı işlevleri destekler. Arka planda veri getirme sPAs daha hızlı bir şekilde yükleyebilir ve tam sayfa yeniden yükler nadir olduğundan tek tek kullanıcı eylemlerini daha iyi yanıt. Kısmen tamamlanan formları ya da belgeler form göndermek için bir düğmeye gerek kalmadan kullanıcı kaydetme artımlı güncelleştirmeler sPAs destekler. SPAs sürükle ve bırak gibi zengin istemci-tarafı davranışları geleneksel uygulamalar çok daha kolay destekleyebilirsiniz. SPAs bağlantı yeniden kurulduğunda, sunucuya geri sonunda eşitlenen bir istemci-tarafı modeline güncelleştirmeleri yapma bir bağlantısız modda çalıştırmak için tasarlanmış olabilir. Uygulamanızın gereksinimlerine tipik HTML formları sunma ötesine gider zengin işlevlerine eklerseniz SPA stil uygulama seçmeniz gerekir.

Sık SPAs adres çubuğunda geçerli işleme yansıtarak (ve yer işareti kullanıcılara ya da bu URL için ayrıntılı bağlantı dönün izin vererek) anlamlı bir URL görüntüleme gibi geleneksel web uygulamaları için yerleşik özellikleri uygulamak gerektiğini unutmayın. SPAs Ayrıca kullanıcıların tarayıcının geri ve İleri düğmelerini bunları beklenmedik olmaz sonuçlarıyla kullanmasına izin vermelidir.

**Ekibiniz ile JavaScript ve/veya TypeScript geliştirme alışkın olduğu**

SPAs yazma, JavaScript ve/veya TypeScript ve istemci tarafı programlama tekniklerinin ve kitaplıkları gerektirir. Ekibinizin Angular gibi SPA framework kullanarak modern JavaScript yazılırken yetkin olmalıdır.

> ### <a name="references--spa-frameworks"></a>Başvuruları – SPA çerçeveler
> - **AngularJS**  
> <https://angularjs.org/>
> - **4 popüler JavaScript çerçeveleri karşılaştırması**  
> <https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks>

**Zaten bir API uygulamanızın diğer (dahili veya genel) istemcileri için kullanıma gerekir**

Diğer istemciler tarafından kullanılacak bir web API destekleniyorsa zaten sunucu tarafı form mantık yeniden oluşturma yerine bu API'leri yararlanır SPA uygulaması oluşturmak için daha az çaba gerektirebilir. Kullanıcıların uygulama ile etkileşim sPAs sorgu ve güncelleştirme veri web API'leri kapsamlı kullanımını kılın.

## <a name="decision-table--traditional-web-or-spa"></a>Karar tablosu – geleneksel Web veya SPA

Aşağıdaki karar tablo bazı geleneksel web uygulaması arasında bir SPA seçerken dikkate alınması gereken temel etmenler özetler.

  | **Faktörü** | **Geleneksel Web uygulaması** | **Tek Sayfalı Uygulama** |
  |---|---|---|
  | JavaScript/TypeScript gerekli takım aşina | **en az** | **Gerekli** |
  | Komut dosyası olmadan tarayıcılar destekler | Desteklenen | **Desteklenmiyor** |
  | En düşük istemci tarafı uygulama davranışı | **Oldukça uygun** | **Overkill** |
  | Zengin ve karmaşık bir kullanıcı arabirimi gereksinimleri | **Limited** | **Oldukça uygun** |

>[!div class="step-by-step"]
[Önceki] (modern-web-uygulamalar-characteristics.md) [sonraki](architectural-principles.md)
