---
title: Önsöz
description: .NET geliştiricilerine Mark Russinovich 'a göre bir Foreword-DAPR
author: markrussinovich
ms.date: 02/17/2021
ms.openlocfilehash: 611cccd7dee253959b06c77c8550b833eec9ddd7
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623973"
---
# <a name="foreword"></a>Önsöz

Bulut benimseme iyi gelişiminde oluşan dalga sayesinde, genellikle mikro hizmet mimarileri ile oluşturulan "bulut Yerel" geliştirmesi ile ilgili önemli bir vardiya vardır. Bu mikro hizmetler hem durum bilgisiz hem de durum bilgisi ve bulut ve uç üzerinde çalışır ve günümüzde sunulan dillerin ve çerçevelerin çeşitliliğe sahiptir. Bu kurumsal kaydırma, hem pazara daha hızlı bir süre, hem de bulut için hizmet oluşturmaya yönelik ölçek ve verimlilik ile çalıştırılır. COVıD-19 ' dan önce bile, bulut benimseme, kuruluşlar için hızlandırılmıştı ve geliştiricilere bu dağıtılmış sistem uygulamalarını oluşturmaya ve bu yana yalnızca hızlandırıcı olan bu uygulamalar için daha da çok daha fazla bilgi istemekte. Kuruluşlardaki geliştiriciler iş mantığına odaklanmayı, platformlar arasında ölçeklendirme, dayanıklılık, bakım, esneklik ve bulut Yerel mimarilerinin diğer özniteliklerini de kapsayan, bu nedenle temel altyapıyı gizleyen sunucusuz platformları de kaydırma yapan platformlara odaklanmayı arar. Geliştiricilerin dağıtılmış sistem uzmanları olması beklenmemelidir. Bu, Kubernetes gibi altyapıya ya da sunucusuz bir platformda oluşturma konusunda size yardımcı olmak için ' deki Bapr adımlarıdır.

Davpr, mantradır "tüm diller, her türlü çerçeve, her yerde Çalıştır" ile kurumsal, geliştirici odaklı, mikro hizmetler programlama modeli platformu olarak tasarlanmıştır. Dağıtılmış uygulamaları, ortak buluttan, hiyerarşik kenara ve hatta tek düğümlü IoT cihazlarına kadar kolay ve taşınabilir hale getirir.Azure Kubernetes hizmeti ve Azure Service Fabric 'da uygulamalar oluşturmaya harcanan zaman ve Azure 'daki deneyimlerimizden ve müşteriler ile çalışmaya harcanan zamanı ortaya çıktı. Ve üzeri olarak, ele aldıkları yaygın problemleri gördük. Geliştiricilerin yalnızca yeni doğa alan uygulamalarında değil, aynı zamanda var olan uygulamaların modernesini kullanmasına yardımcı olmak için yalnızca yeni bir en iyi mikro hizmet uygulamaları için bir "kitaplık" sağlanması gerektiği konusunda net bir sorun oluştu. Kapsayıcılı, dağıtılmış ve ağa bağlı bulut Yerel dünyasında, dışarıdan yükleme modeli, istemci/sunucu oluşturma sırasında dll 'Lerin tercih edildiği şekilde tercih edilen yaklaşım olarak ortaya çıktı. PAPR 'nin dışarıdan yükleme ve API 'Leri, tek bir HTTP veya gRPC yerel çağrısının kolay bir şekilde bir geliştirici olarak, dağıtılmış sistemler işlevinin tüm gücünden yararlanarak size olanak sağlar.

CPR, geliştiricilerin sunduğu çok sayıda senaryoyu ele almak için durum yönetimi, hizmet hizmeti çağrısı, yayın/alt ve dış sistemlerle, Azure Işlevlerinin tetiklerini ve bağlamalarını temel alan g/ç bağlamalarıyla tümleştirme gibi özellikler sağlar. Bu özellikler, bir kodu değiştirmeye, kodun daha taşınabilir olmasını ve gereksinimlerinize en uygun deneme izin vermesini sağlamak zorunda kalmadan, farklı temel durum depolarını, daha esnek ve daha esnek hale getirmek zorunda kalmadan "takas etmenizi" ve farklı temel eyalet mağazalarını söylemek sağlayan mepr 'nin bileşen modelinden faydalanır. Geliştiricilerin, belirli dağıtım ortamlarını hedefleyen kimlik doğrulama, gizli yönetim, yeniden denemeler veya koşullu kod hakkında bilgi edinmek ve bunlara hizmet SDK 'Ları eklemek gerekmez.

Bu kitapta, Davpr 'nin geliştirme süresini ve genel kod bakımını, "kurallı .NET başvuru uygulaması, eShop" artımlı olarak nasıl azalttığı gösterilmektedir. Örneğin, orijinal eShop uygulamasında, hizmetler arasında olayları yayımlamak için Azure Service Bus ve Kbıbitmq arasında Özet olarak önemli miktarda kod yazıldı. Tüm bu kod atılır ve yalnızca iki değil, daha geniş bir çok sayıda yayın/alt aracıları olan PAPR 'nin pub/Sub API 'SI ve bileşen modeliyle değiştirilebilir. Repr 'nin aktör modeli, yeniden çalışılan eShop uygulamasında kullanıldığında, eşzamanlılık ve çoklu iş parçacığı oluşturma işlemlerini tüm zorluklarıyla birlikte uzun süre çalışan, durum bilgisi olan olay odaklı iş akışı uygulamaları oluşturma kolaylığını gösterir. Bu kitabın sonuna kadar, Davpr 'nin uygulama geliştirme sürecinize getirdiği ve tüm geliştiricilerin alanlarında bir bulutta yerel uygulama üzerinde, bu da tüm geliştiricilerin bir bulut Yerel uygulaması üzerinde, bu da tek başına bir yolculuğa sahip olması gerektiğini düşünmem gerektiğini göreceksiniz.

Inpr 'yi Ekim 2019 ' de ve şu anda bir yıllık ve yarı daha sonraki bir yılda bulunan v 0,1 sürümü ile genel olarak duyurduk. Bu, çok. PAPR 'nin v 1.0 'a alınması, gerçek anlamda topluluk çabasıyla karşılaştı. Açık kaynaklı topluluk KAPR etrafında, ilk duyurulduğu andan itibaren büyümek üzere, 1 Ekim 2021 700 2019 ' deki 114 katkı süresi, 16 ayda bir altı kat artar!  Proje katkılarının her bir Davpr deposuna gitmiş olması ve sorunları açma, özellik önerilerine yorum yapma, örnek sağlama ve ders katkısından kod ekleme. Proje topluluğu üyeleri, en çok bir bileşen olan Davpr çalışma zamanı, docs, CLı, SDK 'lar ve bileşenlerin zengin ekosistemi oluşturma ' yı içerir. Bu açıklığın sürdürülmesi, Davpr 'nin geleceği açısından önemlidir.

Davpr gerçekten kullanmaya devam ediyor, ancak Azure hizmetlerinde daha fazla Davpr özelliği ve daha fazla ek destek görmeniz bekleniyor. Önemli iş mantığınıza odaklanmanızı ve mikro hizmet geliştirme sürecinizi hızlandırmanızı sağlamak için, Davpr 'nin avantajlarından faydalanabilirsiniz. Bu yolculuğa karşı ve ücretsiz olarak bizpr Community 'de bize katılmanız bizim için heyecanlıyım  <https://github.com/dapr/> <https://aka.ms/dapr-discord> .

Modern dağıtılmış sistemler karmaşıktır. Küçük, gevşek olarak bağlanmış ve bağımsız dağıtılabilir hizmetlerle başlayabilirsiniz. Bu hizmetler çapraz işlem ve sunucu sınırları. Daha sonra farklı türlerde altyapı yedekleme hizmetleri (veritabanları, ileti aracıları, Anahtar kasaları) kullanır. Son olarak, bu farklı parçalar bir uygulama oluşturmak için birlikte oluşturur.

*Mark Russinovich* 
 *Azure CTO ve teknik arkadaş* 
 *Microsoft*

> [!div class="step-by-step"]
> [Önceki](index.md) 
>  [Sonraki](the-world-is-distributed.md)
