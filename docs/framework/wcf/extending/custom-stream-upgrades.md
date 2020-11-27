---
title: Özel Akış Yükseltmeleri
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 3ef0f59a5d63c24188b29cb7a38db2d6323d80ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295593"
---
# <a name="custom-stream-upgrades"></a>Özel Akış Yükseltmeleri

TCP ve adlandırılmış kanallar gibi akış odaklı aktarımlar, istemci ve sunucu arasındaki sürekli bayt akışı üzerinde çalışır. Bu akış bir nesne tarafından gerçekleştirilir  <xref:System.IO.Stream> . Bir akış yükseltmesinde, istemci kanal yığınına isteğe bağlı bir protokol katmanı eklemek istemektedir ve iletişim kanalının diğer sonunu bunu yapması istenir. Akış yükseltmesi, özgün <xref:System.IO.Stream> nesneyi yükseltilmiş bir nesne ile değiştirme ile oluşur.  
  
 Örneğin, doğrudan aktarım akışının üzerine bir sıkıştırma akışı oluşturabilirsiniz. Bu durumda, özgün aktarım, <xref:System.IO.Stream> özgün bir etrafında sıkıştırmayı sarmalayan bir ile değiştirilmiştir <xref:System.IO.Stream> .  
  
 Birden çok akış yükseltmesi uygulayabilirsiniz, bunların her biri öncesine göre sarmalanarak.  
  
## <a name="how-stream-upgrades-work"></a>Akış yükseltmeleri nasıl çalışır?  

 Akış yükseltme işleminde dört bileşen vardır.  
  
1. Bir yükseltme akışı *başlatıcısı* işlemi başlatır: çalışma zamanında, kanal Aktarım katmanını yükseltmek üzere bağlantısının diğer ucuna bir istek başlatabilir.  
  
2. Yükseltme akışı *Acceptor* , yükseltmeyi yürütür: çalışma zamanında diğer makineden yükseltme isteğini alır ve mümkünse yükseltmeyi kabul eder.  
  
3. Bir yükseltme *sağlayıcısı* , Istemci üzerinde *başlatıcıyı* ve sunucudaki *Acceptor* 'ı oluşturur.  
  
4. Bir akış yükseltme *bağlama öğesi* , hizmet ve istemcideki bağlamalara eklenir ve çalışma zamanında sağlayıcıyı oluşturur.  
  
 Birden çok yükseltmelerde, başlatıcı ve Acceptor, her başlatma için hangi yükseltme geçişlerinin geçerli olduğunu zorlamak üzere durum makinelerini kapsülletine unutmayın.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Akış yükseltmesini uygulama  

 Windows Communication Foundation (WCF), `abstract` uygulayabileceğiniz dört sınıf sağlar:  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Özel bir akış yükseltmesi uygulamak için aşağıdakileri yapın. Bu yordam, hem istemci hem de sunucu makinelerinde en az bir akış yükseltme işlemi uygular.  
  
1. Uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeInitiator> .  
  
    1. <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A>Yükseltilecek akışta gerçekleştirilecek yöntemi geçersiz kılın ve yükseltilen akışı döndürün. Bu yöntem zaman uyumlu olarak çalışır; yükseltmeyi zaman uyumsuz olarak başlatmak için benzer yöntemler vardır.  
  
    2. <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A>Ek yükseltmeleri denetlemek için yöntemini geçersiz kılın.  
  
2. Uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor> .  
  
    1. <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A>Yükseltilecek akışta gerçekleştirilecek yöntemi geçersiz kılın ve yükseltilen akışı döndürün. Bu yöntem zaman uyumlu olarak çalışır; yükseltmenin zaman uyumsuz olarak kabul edileceği benzer yöntemler vardır.  
  
    2. Bu yükseltmenin, yükseltme <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> işleminin bu noktasında bu yükseltme acceptor tarafından desteklenip desteklenmediğini belirleme yöntemini geçersiz kılın.  
  
3. Uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeProvider> . <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A>Ve <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> Adım 2 ve 1 ' de tanımlanan Acceptor ve başlatıcısının örneklerini döndürmek için yöntemini geçersiz kılın.  
  
4. Uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> .  
  
    1. <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A>İstemcideki yöntemi ve <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> hizmet üzerindeki yöntemi geçersiz kılın.  
  
    2. ' A <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> yükseltme bağlama öğesini eklemek için istemcideki yöntemi ve hizmet üzerindeki yöntemi geçersiz kılın <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A> .  
  
5. Yeni akış yükseltme bağlama öğesini sunucu ve istemci makinelerdeki bağlamalara ekleyin.  
  
## <a name="security-upgrades"></a>Güvenlik yükseltmeleri  

 Güvenlik yükseltmesi eklemek, genel akış yükseltme işleminin özelleşmiş bir sürümüdür.  
  
 WCF, akış güvenliğini yükseltmek için zaten iki bağlama öğesi sağlar. Aktarım düzeyi güvenliği yapılandırması, <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> ve için <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> yapılandırılmış ve özel bir bağlamaya eklenebilen öğesine göre kapsüllenir. Bu bağlama öğeleri <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> , istemci ve sunucu akışı yükseltme sağlayıcılarını oluşturan sınıfını genişletir. Bu bağlama öğelerinde, özel güvenlik akışı yükseltme sağlayıcısı sınıflarını oluşturan yöntemler vardır `public` . bu nedenle, bu iki durum için tek yapmanız gereken, bağlama öğesini bağlamaya eklemektir.  
  
 Yukarıdaki iki bağlama öğesi tarafından karşılanmayan güvenlik senaryoları için, güvenlikle ilgili üç sınıf, `abstract` Yukarıdaki başlatıcıdan, Acceptor 'dan ve sağlayıcı temel sınıflarından türetilir:  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Bir güvenlik akışı yükseltmesini uygulama işlemi, bu üç sınıftan türettiğiniz farkla daha önceki ile aynıdır. Çalışma zamanına güvenlik bilgilerini sağlamak için bu sınıflardaki ek özellikleri geçersiz kılın.  
  
## <a name="multiple-upgrades"></a>Birden çok yükseltme  

 Ek yükseltme istekleri oluşturmak için yukarıdaki işlemi yineleyin: ek uzantılar <xref:System.ServiceModel.Channels.StreamUpgradeProvider> ve bağlama öğeleri oluşturun. Bağlama öğelerini bağlamaya ekleyin. Ek bağlama öğeleri, bağlamaya eklenen ilk bağlama öğesiyle başlayarak sırayla işlenir. ' De <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> her bir yükseltme sağlayıcısı, önceden var olan herhangi bir yükseltme bağlama parametrelerinde katmanın kendisini nasıl göstereceğini belirleyebilir. Daha sonra var olan yükseltme bağlama parametresini yeni bir bileşik yükseltme bağlama parametresiyle değiştirmelisiniz.  
  
 Alternatif olarak, bir yükseltme sağlayıcısı birden çok yükseltmeyi destekleyebilir. Örneğin, hem güvenlik hem de sıkıştırmayı destekleyen özel bir akış yükseltme sağlayıcısı uygulamak isteyebilirsiniz. Aşağıdaki adımları uygulayın:  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>Başlatıcı ve Acceptor oluşturan sağlayıcı sınıfının yazılacağı alt sınıf.  
  
2. Sınıf, <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> sıkıştırma akışı için içerik türlerini ve güvenli akışı sırayla döndürmek için yöntemini geçersiz kıldığınızdan emin olun.  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>Yöntemi içindeki özel içerik türlerini anlayan alt sınıf <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> .  
  
4. Akış, ve ' a yapılan her çağrıdan sonra <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> yükseltilir <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
