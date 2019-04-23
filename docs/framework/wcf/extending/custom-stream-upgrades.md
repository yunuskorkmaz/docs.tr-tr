---
title: Özel Akış Yükseltmeleri
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 8c769321702deb774c04613d5fe5eb2fde069063
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977775"
---
# <a name="custom-stream-upgrades"></a>Özel Akış Yükseltmeleri
İstemci ve sunucu arasında bulunan bayt sürekli bir akış üzerinde Stream odaklı taşımalar TCP ve adlandırılmış kanallar gibi çalışır. Bu akış tarafından gerçekleştirilen bir <xref:System.IO.Stream> nesne. Bir akış yükseltme istemci kanal yığınına bir isteğe bağlı Protokolü katmanı eklemek ister ve bunu yapmak için iletişim kanalı diğer ucuna sorar. Özgün değiştirerek akış yükseltme oluşur <xref:System.IO.Stream> yükseltilmiş bir nesne.  
  
 Örneğin, aktarım akışı üzerinde doğrudan bir sıkıştırma akış oluşturabilirsiniz. Bu durumda özgün taşıma <xref:System.IO.Stream> sıkıştırma sarmalayan bir değiştirilir <xref:System.IO.Stream> ilkinin geçici bir çözüm.  
  
 Birden çok akış yükseltmeleri, her bir sarmalama uygulayabilirsiniz.  
  
## <a name="how-stream-upgrades-work"></a>Stream yükseltme nasıl çalışır  
 Dört bileşenler stream yükseltme işlemi için vardır.  
  
1. Bir yükseltme akışı *Başlatıcı* işlemi başlar: çalışma zamanında kanal Aktarım katmanı yükseltme isteği diğer sonuna bağlantısını başlatabilirsiniz.  
  
2. Bir yükseltme akışı *Acceptor* yükseltme taşır: çalışma zamanında başka bir makineden yükseltme isteği alır ve mümkün olduğunda, yükseltme kabul eder.  
  
3. Yükseltme *sağlayıcısı* oluşturur *Başlatıcı* istemcide ve *Acceptor* sunucusunda.  
  
4. Bir akış yükseltme *bağlama öğesi* hizmet ve istemci bağlantılarına eklenir ve çalışma zamanında sağlayıcısı oluşturur.  
  
 Birden fazla yükseltme söz konusu olduğunda, hangi yükseltme geçişleri her başlatma için geçerli olan zorlamak için Durum makineleri Acceptor ve Başlatıcı kapsülleyen unutmayın.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Stream yükseltme gerçekleştirme  
 Windows Communication Foundation (WCF) dört sağlar `abstract` uygulayabileceğiniz sınıflar:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Özel akış yükseltmeyi uygulamak için aşağıdakileri yapın. Bu yordam istemci ve sunucu makinelerde en az bir akış yükseltme işlemi uygular.  
  
1. Uygulayan bir sınıf oluşturma <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> yükseltilmesi ve yükseltilmiş akış döndürmek için akışa almak için yöntemi. Bu yöntem zaman uyumlu olarak çalışır; zaman uyumsuz olarak yükseltmeyi başlatmak için benzer yöntemler vardır.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> ek güncellenerek denetlemek için yöntem.  
  
2. Uygulayan bir sınıf oluşturma <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> yükseltilmesi ve yükseltilmiş akış döndürmek için akışa almak için yöntemi. Bu yöntem zaman uyumlu olarak çalışır; Yükseltme zaman uyumsuz olarak kabul etmek için benzer yöntemler vardır.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> istenen yükseltme bu yükseltme acceptor bu noktada, yükseltme işlemi tarafından desteklenip desteklenmediğini belirlemek için yöntemi.  
  
3. Uygulayan bir sınıf oluşturmanız <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> ve <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> acceptor ve 2 ve 1. adımda tanımlanan Başlatıcı örnekleri döndürmek için yöntemleri.  
  
4. Uygulayan bir sınıf oluşturma <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> istemcide yöntemi ve <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> hizmette yöntemi.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> istemcide yöntemi ve <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> yükseltme bağlama öğesi eklemek için hizmet metodunda <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5. Yeni akış yükseltme bağlama öğesi, sunucu ve istemci makinelerinde bağlamaları ekleyin.  
  
## <a name="security-upgrades"></a>Güvenlik yükseltmeleri  
 Bir güvenlik yükseltmesi ekleme, genel akışı yükseltme işlemi özelleştirilmiş bir sürümüdür.  
  
 WCF zaten Akış Güvenliği yükseltmek için iki bağlama öğeleri sağlar. Aktarım düzeyi güvenlik yapılandırmasını yalıtılan <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> ve <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> , yapılandırılabilir ve özel bağlama için eklendi. Bu bağlama öğelerini genişletmek <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> yükseltme sağlayıcıları istemci ve sunucu akışı oluşturan sınıf. Bu bağlama öğeleri özel güvenlik akışı olmayan yükseltme sağlayıcısı sınıfları oluşturma yöntemleri sahip `public`, bağlama bağlama öğesi eklemek için bu iki durumda yapmak için ihtiyacınız olan şekilde.  
  
 Yukarıdaki iki nedeni bağlama öğelerinin, üç güvenlikle ilgili karşılanmadı güvenlik senaryoları için `abstract` sınıfları yukarıdaki başlatıcısı, acceptor ve sağlayıcı temel sınıflarından türetilen:  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Uygulama güvenlik stream yükseltme sürecinde daha önce bu üç sınıflardan türetin fark ile aynıdır. Bu sınıfların çalışma zamanı güvenlik bilgileri sağlamak için ek özellikler geçersiz kılar.  
  
## <a name="multiple-upgrades"></a>Birden fazla yükseltme  
 Yükseltme isteklerini ek oluşturmak için yukarıdaki işlemi tekrarlayın: ek uzantıları oluşturma <xref:System.ServiceModel.Channels.StreamUpgradeProvider> ve bağlama öğeleri. Bağlamaya ait bağlama öğelerini ekleyin. Ek bağlama öğeleri bağlamaya eklenen ilk bağlama öğesi ile başlayan ardışık olarak işlenir. İçinde <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> her yükseltme sağlayıcısı kendisi önceden var olan yükseltme parametreleri bağlama üzerinde katman nasıl belirleyebilirsiniz. Ardından yeni bir bileşik yükseltme bağlama parametresi ile parametre bağlama mevcut yükseltme değiştirmeniz gerekir.  
  
 Alternatif olarak, bir yükseltme sağlayıcısı, birden fazla yükseltme destekleyebilir. Örneğin, hem güvenlik hem de sıkıştırma destekleyen özel akış yükseltme sağlayıcıyı uygulama isteyebilirsiniz. Aşağıdaki adımları uygulayın:  
  
1. Alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> Acceptor ve Başlatıcı oluşturur sağlayıcı sınıfı yazılacak.  
  
2. Alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> geçersiz kılmak sağlamaktan <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> Sıkıştırma akışına ve güvenli bir akış için içerik türleri sırayla döndürmek için yöntemi.  
  
3. Alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> özel içerik türleri anlayan kendi <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> yöntemi.  
  
4. Akışı yapılan her çağrı sonra yükseltilecek <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> ve <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
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
