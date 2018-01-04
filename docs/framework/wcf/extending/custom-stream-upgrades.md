---
title: "Özel Akış Yükseltmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73359c293f7d29c16702e826ed6caa61149935bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-stream-upgrades"></a>Özel Akış Yükseltmeleri
İstemci ve sunucu arasındaki bayt sürekli bir akış üzerinde akış odaklı taşımaları TCP ve adlandırılmış kanallar gibi çalışır. Bu akış tarafından gerçekleştirilen bir <xref:System.IO.Stream> nesnesi. Bir akış yükseltme istemci kanal yığına bir isteğe bağlı Protokolü katmanı eklemek ister ve bunu yapmak için iletişim kanalının diğer ucundaki sorar. Özgün değiştirme akış yükseltme oluşur <xref:System.IO.Stream> yükseltilmiş bir nesne.  
  
 Örneğin, aktarım akışı en üstünde Sıkıştırma akışına oluşturabilirsiniz. Bu durumda özgün aktarım <xref:System.IO.Stream> sıkıştırma saran bir ile değiştirilir <xref:System.IO.Stream> ilkinin geçici.  
  
 Birden çok akış yükseltmeleri, her bir kaydırma uygulayabilirsiniz.  
  
## <a name="how-stream-upgrades-work"></a>Akış yükseltme nasıl çalışır  
 Akış yükseltme işlemi dört bileşenleri vardır.  
  
1.  Yükseltme akış *Başlatıcı* işlemi başlar: çalışma zamanında kanal Aktarım katmanı yükseltmek için bir istek diğer sonuna bağlantısını başlatabilirsiniz.  
  
2.  Yükseltme akış *Acceptor* yükseltme taşır: çalışma zamanında başka bir makineden yükseltme isteği alır ve mümkünse, yükseltme kabul eder.  
  
3.  Bir yükseltme *sağlayıcı* oluşturur *Başlatıcı* istemcide ve *Acceptor* sunucusunda.  
  
4.  Bir akış yükseltme *bağlama öğesi* hizmet ve istemci bağlantılarına eklenir ve çalışma zamanında sağlayıcısı oluşturur.  
  
 Birden fazla yükseltme söz konusu olduğunda, hangi yükseltme geçişleri her başlatma için geçerli zorlamak için Durum makineleri Acceptor ve Başlatıcı kapsülleyen unutmayın.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Bir akış yükseltme gerçekleştirme  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]dört sağlar `abstract` , uygulayabileceğiniz sınıfları:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Özel akış yükseltmeyi uygulamak için aşağıdakileri yapın. Bu yordam istemci ve sunucu makinelerde en az bir akış yükseltme işlemi uygular.  
  
1.  Arabirimini uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> yükseltilmesi ve yükseltilmiş akış dönmek için akışında yapılacak yöntemi. Bu yöntem, zaman uyumlu olarak çalışır; zaman uyumsuz olarak yükseltme başlatmak için benzer yöntemler vardır.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> yöntemi ek güncelleştirmelerini denetle.  
  
2.  Arabirimini uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> yükseltilmesi ve yükseltilmiş akış dönmek için akışında yapılacak yöntemi. Bu yöntem, zaman uyumlu olarak çalışır; Yükseltme zaman uyumsuz olarak kabul etmek için benzer yöntemler vardır.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> istenen yükseltme bu yükseltme acceptor bu noktada yükseltme işlemindeki tarafından desteklenip desteklenmediğini belirlemek için yöntem.  
  
3.  Uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> ve <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> acceptor ve 2. ve 1. adımda tanımlanan Başlatıcı örnekleri döndürülecek yöntemleri.  
  
4.  Arabirimini uygulayan bir sınıf oluşturun <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Geçersiz kılma <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> istemcide yöntemi ve <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> hizmette yöntemi.  
  
    2.  Geçersiz kılma <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> istemcide yöntemi ve <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> yükseltme bağlama öğesine eklemek için hizmetinde yöntemini <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Sunucu ve istemci makineleri bağlamaları yeni akış yükseltme bağlama öğesi ekleyin.  
  
## <a name="security-upgrades"></a>Güvenlik yükseltmeleri  
 Bir güvenlik yükseltmesi ekleme, genel akış yükseltme işlemi özelleştirilmiş bir sürümüdür.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zaten Akış Güvenliği yükseltmek için iki bağlama öğeleri sağlar. Aktarım düzeyinde güvenlik yapılandırmasını yalıtılan <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> ve <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> hangi yapılandırılabilir ve özel bağlama için eklendi. Bu bağlama öğelerini genişletmek <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> yükseltme sağlayıcıları istemci ve sunucu akış derlemeler sınıfı. Bu bağlama öğeleri Uzman güvenlik akış olmayan yükseltme sağlayıcısı sınıfları oluşturma yöntemleri sahip `public`, bu iki için tüm yapmanız gereken durumda bağlamaya bağlama öğesi eklemek için.  
  
 Yukarıdaki iki bağlama öğeleri tarafından üç güvenlikle ilgili karşılanmadı güvenlik senaryoları için `abstract` sınıfları yukarıdaki Başlatıcı, acceptor ve sağlayıcı temel sınıflardan türetilmiş:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Güvenlik akış yükseltme uygulama işlemi boyunca önce bu üç sınıflardan türetin fark ile aynıdır. Çalışma zamanı için güvenlik bilgileri sağlamak için bu sınıfları, ek özellikler geçersiz kılar.  
  
## <a name="multiple-upgrades"></a>Birden fazla yükseltme  
 Yükseltme istekleri ek oluşturmak için yukarıdaki işlemi tekrarlayın: ek uzantıları oluşturma <xref:System.ServiceModel.Channels.StreamUpgradeProvider> ve bağlama öğeleri. Bağlamaya ait bağlama öğelerini ekleyin. Ek bağlama öğeleri bağlamaya eklenen ilk bağlama öğesi ile başlayan ardışık olarak işlenir. İçinde <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> her yükseltme sağlayıcı kendisini parametreleri bağlama önceden varolan yükseltme sonrasında katman nasıl belirleyebilirsiniz. Ardından yeni bir birleşik yükseltme bağlama parametresi parametresiyle bağlama varolan yükseltme değiştirmeniz gerekir.  
  
 Alternatif olarak, bir yükseltme sağlayıcı birden fazla yükseltme destekleyebilir. Örneğin, güvenlik ve sıkıştırma destekleyen bir özel akış yükseltme sağlayıcı uygulamak isteyebilirsiniz. Aşağıdaki adımları uygulayın:  
  
1.  Bir alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> Acceptor ve Başlatıcı oluşturur sağlayıcı sınıfı yazmak için.  
  
2.  Bir alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> geçersiz kılmak emin <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> Sıkıştırma akışına ve güvenli akış için içerik türleri sırayla döndürülecek yöntemi.  
  
3.  Bir alt <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> özel içerik türlerinde anlar kendi <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> yöntemi.  
  
4.  Akış her çağrı sonra yükseltilecek <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> ve <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
